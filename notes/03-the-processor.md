#  the processor

1.  [introduction](#introduction)
2.  [building a datapath](#building-a-datapath)
3.  [overview of pipelining](#overview-of-pipelining)
4.  [pipelined datapath and control](#pipelined-datapath-and-control)
5.  [data hazards](#data-hazards)
6.  [control hazards](#control-hazards)
7.  [parallelism via instructions](#parallelism-via-instructions)
8.  [ilp and matrix multiply](#ilp-and-matrix-multiply)

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




##  building a datapath

##  overview of pipelining

##  pipelined datapath and control

##  data hazards

##  control hazards

##  parallelism via instructions

##  ilp and matrix multiply