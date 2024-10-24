#  the processor

1.  [introduction](#introduction)
2.  [building a datapath](#building-a-datapath)
3.  [overview of pipelining](#overview-of-pipelining)
4.  [pipelined datapath and control](#pipelined-datapath-and-control)
5.  [data hazards](#data-hazards)
6.  [control hazards](#control-hazards)
7.  [parallelism via instructions](#parallelism-via-instructions)
8.  [ilp and matrix multiply](#ilp-and-matrix-multiply)
9.  [questions and answers](#questions-and-answers)

##  introduction

the performance of a computer is determined by three key factors -  instruction count, clock cycle time, and clock cycles per instruction cpi.  the compiler and the instruction set architecture determine the instruction count required for a given program.  however, the implementation of the processor determines both the clock cycle time and the number of clock cycles per instruction.  the following will construct a datapath and control unit for two different implementations of the legv8 instruction set.

the following contains an explanation of the principles and techniques used in implementing a processor, starting with a highly abstract and simplified overview.  it is followed by a section that builds up a datapath and constructs a simple version of a processor sufficient to implement an instruction set like legv8.  the bulk of the chapter covers a more realistic **pipelined** legv8 implementation, followed by a section that develops the concepts necessary to implement more complex instruction sets, like the x86.

###  a basic legv8 implementation

we will be examining an implementation that includes a subset of the core legv8 instruction set 

-  the memory reference instructions load register unscaled `LDR` and store register unscaled `STR`
-  the arithmetic logical instructions `ADD`, `SUB`, `AND`, and `ORR`
-  the instructions compare and branch on zero `CBZ` and branch `B`

this subset does not include all the integer instructions (for example shift, multiply, and divide are missing), nor does it include any floating point instructions.  however, it illustrates the key principles used in creating a datapath and designing the control.  the implementation of the remaining instructions is similar.

in examining the implementation, we will have the opportunity to see how the instruction set architecture determines many aspects of the implementation, and how the choice of various implementation strategies affect the clock rate and cpi for the computer.  many of the key design principles introduced can be illustrated by looking at the implementation, such as simplicity favors regularity.  in addition, most concepts used to implement the legv8 subset in this chapter are the same basic ideas that are used to construct a broad spectrum of computers, from high performance servers to general purpose microprocessors to embedded processors.

####  an overview of the implementation

in the cod chapter 2 (instructions language of the computer), we looked at the core legv8 instructions, including the integer arithmetic logical instructions, the memory reference instructions, and the branch instructions.  much of what needs to be done to implement these instructions in the same, independent of the exact class of instructions.  for every instruction, the first two steps are identical

1.  send the program counter to the memory that contains the code and fetch the instruction from that memory
2.  read one or two registers, using fields of the instruction to select the registers to read.  for the `LDUR` and `CBZ` instructions, we need to read only one register, but most other instructions require reading two registers.

after these two steps, the actions required to complete the instruction depend on the instruction class.  fortunately for each of these three instruction classes (memory reference, arithmetic logical, and branches), the actions are largely the same, independent of the exact instruction.  the simplicity and regularity of the legv8 instruction set simplify the implementation by making the execution of many of the instruction classes similar. 

for example, all instruction classes, except unconditional branch use, the arithmetic logical unit (alu), after reading the registers.  the memory reference instructions use the alu for an address calculation, the arithmetic logical instructions for the operation execution, and conditional branches for comparison to zero.  after using the alu, the actions required to complete various instruction classes differ.  a memory reference instruction will need to access the memory either to read data for a load or write data for a store.  an arithmetic logical or load instruction must write the data from the alu or memory back into a register.  lastly, for a conditional branch instruction, we may need to change the next instruction address based on the comparison; otherwise, the pc would be incremented by four to get the address of the subsequent instruction.

####  an abstract view of the implementation of the legv8 subset showing the major functional units and the major connection between them 

<div align="center">
    <img width="500" src="https://zytools.zybooks.com/zyAuthor/CompOrgAndDesign_PattersonHennesy/56/IMAGES/embedded_image_1arm_d4e8f7c0-c340-9c9b-a5b8-92ea8b357821_5fPSCoDUJwAdYDA1Hv94.png">
</div>

all instructions start by using the program counter to supply the instruction address to the instruction memory.  after the instruction is fetched, the register operand used by an instruction are specified by fields of that instruction.  once the register operands have been fetched, they can be operated on to compute a memory address for a load or store, to compute an arithmetic result (for an integer arithmetic logical instruction), or a compare to zero (for a branch).  if the instruction is an arithmetic logical instruction, the result from the alu must be written to a register.  if the operation is a load or store, the alu result is used as an address to either store a value from teh registers or load a value from memory into the registers.  the result from the alu or memory is written back into the register file.  branches require to use of the alu output to determine the next instruction address, which comes either from teh alu where the pc and branch offset are summed or from teh adder that increments the current pc byu four.  the thick lines interconnecting the functional units represent buses, which consist of multiple signals.  the arrows are used to guide the reader in knowing how information flows.  since signal lines may cross, we explicitly show when crossing lines are connected by the presence of a dot where the lines cross.

first, in several places, the figure above shows data going to a particular unit as coming from two difference sources.  for example, the value written into the pc can come from one of two adders, the data written into the register file can come from either the alu or the data memory, and the second input to the alu can come from a register or the element that chooses from among the multiple sources and steers one of those sources to its destination.  this selection is commonly done with a device called a **multiplexor**, although this device might better be called a **data selector**.  a multiplexor which selects from among several inputs based on the setting of its control lines.  the control lines are set based primarily on information taken from the instruction being executed.

the second omission in the figure above is that several of the units must be controlled depending on the type of instruction.  for example, the data memory must be read on a load and write on a store.  the register file must be written only on a load or an arithmetic logical instruction.  and of course, the alu must perform one of several operations.  like the multiplexor, control lines that are set based on various fields in the instruction direct these operations.

the figure below shows the datapath of abstract view of the implementation of the legv8 subset with the three required multiplexors added, as well as control lines for the major functional units.   a control unit which as has the instruction as an input is ued to determine how to set the control lines for the functional units and two of the multiplexors.  the top multiplexor, which determines whether pc + 1 or the branch destination address is written into the pc, is set based on teh zero output of the alu, which is used to perform the comparison of the `CBZ` instruction.  the regularity and simplicity of the legv8 instruction set mean that a simple decoding process can be used to determine how to set the control lines.

####  the basic implementation of the legv8 subset, including the necessary multiplexors and control lines

the top multiplexor `MUX` controls what value places the `PC` `PC + 4` or the branch destination address; the multiplexor is controlled by the gate and `ANDs` together the zero output of the alu and ta control signal that indicates that the instruction is a branch.  the middle multiplexor, whose output returns to the register file, is used to steer the output of the alu (in teh case of an arithmetic logical instruction) or the output of the data memory (in the case of a load) for writing into the register file.  finally the bottom most multiplexor is used to determine whether the second alu input is from the register (for an arithmetic logical instruction or a branch) or from the offset field of the instruction (for a load or store).  the added control lines are straightforward and determine the operation performed at the alu, whether the data memory should read or write, and whether the registers should perform a write operation.  the control lines are shown in color to make them easier to see.

<div align="center">
<img width="500" src="https://zytools.zybooks.com/zyAuthor/CompOrgAndDesign_PattersonHennesy/56/IMAGES/embedded_image_1arm_6217a3ca-0327-636c-62bd-82f4147f1b5c_5fPSCoDUJwAdYDA1Hv94.png">
</div>

further in this reading we will refine this view to fill in teh details, which requires that we add further functional units, increase the number of connection between units, and of course, enhance a control unit to control what actions are taken for different instruction classes.  cod section 4.3 building a datapath and 4.4 a simple implementation scheme describe a simple implementation that uses a single clock cycle for every instruction and follows the general form of the above figures.  in this first design, every instruction begins execution on one clock edge and completes execution on teh next clock edge.

while easier to understand, this approach is not practical, since the clock cycle must be severely stretched to accommodate the longest instruction.  after designing the control for this simple computer, we will look at pipelined implementation with all its complexities, including exceptions.

##  building a datapath

a reasonable way to start a datapath design is to examine the major components required to execute each class of legv8 instructions.  let's start at the top by looking at which datapath elements each instruction needs, and then work our way down through the levels of **abstraction**.  when we show the datapath elements, we will also show their control signals.  we use abstraction in this explanation, starting from the bottom up.

**datapath element** -  a unit used to operate on or hold data within a processor.  in the legv8 implementation, the datapath elements include the instruction and data memories, the register file, the alu, and adders.

item a in the figure below shows the first element we need -  a memory unit to store the instructions of a program and supply instructions given an address.  item b in the figure below also shows the **program counter pc**, which is a register that holds the address of the current instruction.  lastly, we will need an adder to increment the **pc** to the address of the next instruction.  this adder, which is combinational, can be built from the alu described in detail, by writing the control lines so that the control always specifies an add operation.  we will draw such an alu with the label add as in the figure below, to indicate that it has been permanently made an adder and cannot perform the other alu functions.

**program counter pc** -  the register containing the address of the next instruction in the program being executed.

####  the two state elements are needed to store and access instructions, and an adder is needed to compute the next instruction address 

the state elements are the instruction memory and the program counter.  the instruction memory need only provide read access because the datapath does not write instructions.  since the instruction memory only reads, we treat it as combinational logic -  the output at any time reflects the content of the location specified by the address input, and no read control is needed.  we will need to write the instruction memory when we load the program;  this is not hard to add, we ignore it for simplicity.  the program counter is a 64-bit register that is written at the end of every clock cycle and thus does not need to write control signal.  the adder is an alu wired to always add its two 64-bit inputs and place the sum on its output.

<div align="center">
<img width="500" src="https://zytools.zybooks.com/zyAuthor/CompOrgAndDesign_PattersonHennesy/56/IMAGES/embedded_image_1arm_b83433e2-87d9-7033-0d21-b483ad0ea26a_5fPSCoDUJwAdYDA1Hv94.png">
</div>


##  overview of pipelining

##  pipelined datapath and control

##  data hazards

##  control hazards

##  parallelism via instructions

##  ilp and matrix multiply

##  questions and answers

1.  consider the first three steps for a typical legv8 instruction

1st step -  fetch instruction from memory -  every instruction must first be fetched from memory, based on the value of the program counter.

2nd step -  read register(s) -  every instruction reads one or two registers.

3rd step for memory reference instructions -  use alu for address calculation -  the address calculation determines what memory address to access.

3rd step for arithmetic logic instructions - use alu for operation execution -  the instruction's operation like add or subtract is carried out by the alu.

3rd step for branch instructions -  use alu for comparisons -  the result of the comparison determines whether the branch should be taken.

2.  how many of the five classic components of a computer appear in the figure 

<div align="center">
<img width="500" src="https://zytools.zybooks.com/zyAuthor/CompOrgAndDesign_PattersonHennesy/56/IMAGES/embedded_image_1arm_6217a3ca-0327-636c-62bd-82f4147f1b5c_5fPSCoDUJwAdYDA1Hv94.png">
</div>

input - false - the figure does not show additional mechanisms through which the computer is fed information, such as a keyboard.  

memory -  true -  the instruction memory stores the program that is to be executed.  the data memory stores the data needed by the running programs.

control -  true -  the control unit commands the datapath according to the instructions of the program by setting the control lines for each of the major functional units.

datapath -  true -  the datapath elements include the instruction and data memories, the register file, the alu, and adders.

output -  false -  the figure does not show additional mechanisms that convey the result of a computation, such as a display, to a user or to another computer.