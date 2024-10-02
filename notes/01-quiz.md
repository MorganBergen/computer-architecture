t - in a pure harvard computer, program and data are stored in separate memories
f - operand fetch is required to execute each and every instruction 
t -  operating system machine level is introduced for supporting input / output operations
f -  in 1940s, a 2 level computer had digital logic level and microarchitecture level
t -  it is expected that different processors should have different sets of isa instructions
f -  it is expected that moore’s law should be a valid forever
t -  a microcontroller is a full blown (i.e. complete) computer
f -  computer family x86 is better suited for embedded systems 
t -  current intel processors are backward compatible as far back as intel’s 8086 processor
f -  comparing with cisc, a risk machine should have more instructions
based on the six-level computer in the textbook mention at least 3 differences between interpretation and translation techniques
interpretation -  conversion type -  instruction by instru. 	translation -  conversion type -  is all at once, the whole original program
interpretation -  seen at level - below level 3 		translation -  seen at level -  above level 3
interpretation -  control -  interpreted / lower level	translation -  control -  translator / upper level
interpretation -  storage required -  less		translation -  storage required -  more
interpretation -  example -  os (partial), microprogram	translation -  example -  compiler, assembler
mention the hardware and software view of a data path - hardware view - a data path consists of registers, alu, and bus, software view - a path inside the cpu, where data moves during the execution of an instruction
consider a multilevel computer with identical interpreters at levels 1, 2, 3.  each interpreter takes 4 instructions to process (fetch, decode, execute) one (upper level) instruction.  one instruction at level 1 takes 2 nanoseconds to execute.  how long does it take for an instruction at level 3? -  one instruction at level 3 is equivalent to 4 * 4 instruction s at level 1, one instruction at level 3 should take (4 * 4) * 2 ns = 32 ns
we are to improve the multilevel computer mentioned in the six level computer.  say we replace the interpreter between levels 1 and 2 and now it takes 5 instructions to process (fetch, decode, execute) one level 2 instruction.  also we replace the interpreter between levels 2 and 3 and now it takes 2 instructions to process (fetch, decode, execute) one level 3 instruction.  one instruction at level 1 takes 2 nanoseconds to execute.  is there any performance improvement?  how? -  here, one instruction at level 3 is equivalent to 2 * 5 instructions at level 1, one instruction at level 3 should take (2 * 5) * 2 ns = 20 ns.  yes, there is a 37.5% performance improvement.  instead of 32 ns, now it takes 20 ns to execute one instruction at level 3.
computer -  a machine that receives inputs, manipulates and or stores data, and provides useful outputs
computer architecture -  conceptual design and fundamental operational structure of a computer system
von neumann architecture -  a computer architecture with these components, a central processing unit cpu that contains a control unit cu, an arithmetic logic unit alu, registers, etc. input and output, i/o mechanisms, memory that stores data and instructions, bus, etc.
pure harvard architecture -  simple, has cpu, i/o, bus, etc. with physically separate storage and single pathways for instructions and data.
pdp-8 architecture - a simple computer architecture that has cpu, memory, i/o, etc. where the components are connected via a shared bus

discuss the major steps to execute an instruction mentioning if it is mandatory or not.  explain why it is mandatory = m or not mandatory = ns
1 -  m -  i.f. instruction fetch -instruction is fetched from memory to instruction register in the central processing unit cpu
2 -  m -  i.d. instruction decode - instruction is decoded by the decoder/control unit cu inside the cpu
3 -  m -  i.e. instruction execution - instruction must be executed by alu inside the cpu
4 -  n -  o.f. operand fetch - operands (variable values) are fetched from memory to data registers in the cpu, otherwise do nothing
4 -  n -  mem. memory access - reading from memory the cpu will access the memory to fetch operations before performing the operation
5-  n -  w.b. result write back to main memory - result/operand is written back to memory from data registers in the cpu, if there is data to write

[mem - x] = [mem - y] + [mem - z] 	i.f. i.d. i.e. mem. w.b.
[reg -1] = [reg -2] - [reg -3]		i.f. i.d. i.e.
[reg - 4] = [mem - a] + 1		i.f. i.d. i.e. mem.
[mem - b] = 7				i.f. i.d. i.e. w.b.
go to [mem - c]				.
[dreg - 1] = 0				i.f. i.d. i.e.
[mem - 1] = 1				i.f. i.d. i.e. w.b.
[mem - 2] = 2 * [mem - 2]		i.f. i.d. o.f. i.e. w.b.
go to mem 3 				i.f. i.d. i.e.
computer classes - pc, servers, supercomputers, embedded computers, personal mobile devices, warehouse scale computers, quantum computers
great ideas - design for moore’s law, use abstraction to simplify design, make common case fast, performance via parallelism, performance via pipelining, performance via prediction, hierarchy of memories, dependability via redundancy
suspension bridge cables - dependability via redundancy, aircraft and marine novation systems that incorporate wind information - performance via prediction
express elevators in buildings - performance via pipelining, library reserve desk - hierarchy of memories, adding electronic magnetic aircraft catapults - design for moore’s law, discuss three major levels of program code - high level language, assembly language, machine code
cpu - out the instructions of a computer program by performing arithmetical, logical and input/output operations of the system, contains data path and control unit
memory - the storage area in which program are kept when they are running and contains data needed by the running programs
input/output devices - keyboard - mechanism through which the computer is fed information, display - mechanism conveys the result of a computation to a user
high level languages - portable language c, c++, composed of words and algebraic notation that can be translated by a compiler into assembly language
system software - software that provides services that are commonly useful including operating systems, compilers, loader, and assemblers
operating system - supervising program that manages the resources of a computer for the benefit of the programs that run on that computer
compiler - a program that translates high level language statements into assembly language statements
assembler - a program that translates a symbolic version of instructions into binary version 
assembly language - a symbolic representation of machine instructions
machine language - a binary representation of machine instructions
instruction - a command that computer hardware understands and obeys
input device - keyboard, output device - display, memory - stores program and data | cache - a small fast memory
dynamic random access memory dram - integrated circuit
static random access memory sram - ic, faster than dram
datapath - performs operations on data 
control - signals that determine the operation of a datapath
integrated circuit ic - chip, a device combining dozens to millions of transistors
instruction set architecture - abstract interface between hardware and lowest level software, encompasses all the info necessary to write machine language prog
implementation - hardware that obeys the architecture abstraction
volatile memory - storage i.e. dram that retains data only if it is receiving power
nonvolatile memory - storage that retains data even in the absence of power supply, used to store programs and data, e.g. hard disk
main memory - primary memory, used to hold programs and data while execution, consists of dram
secondary memory - nonvolatile memory used to store programs and data, consists of magnetic disks and flash memory
magnetic disk - hard disk, a form of nonvolatile secondary memory composed of rotating platters
flash memory - non volatile semiconductor memory
performance per unit cost of technology - relative performance e
vacuum tube - electronic component that was widely used in early electronic devices before the advent of transits
transistor - on/off switch controlled by electric signal
very large scale integrated vlsi circuit - device containing hundreds of thousands to millions of transistors in a chip
manufacturing process - ingot silicon crystal ingot -> wafer a slice of an ingot -> defect microscopic flow that can result in the failure of a die -> wafer cuts 
throughput - bandwidth another measure of performance, it is the number of tasks completed per unit time
response time - execution time, the total time required for the computer to complete a task
performance = 1 / execution time
if a computer a runs a program in 10 sec and computer b runs the same program in 15 seconds compare a and b
performance of a / performance of b = execution time of b / execution time of a = 15 / 10 = 1.5, computer a is 1.5 times faster than computer b
cpu execution time - cpu time, the actual time the cpu spends computing for a specific task
user cpu time - cpu time spent in a program itself
system cpu time - the cpu time spent in the operating system performing tasks on behalf of the program
clock time - the time for one clock period which runs at a constant rate, clock cycle time = 1 / clock rate
clock period - the length of each clock cycle

cpu execution time for a program = cpu clock cycles for a program * clock cycle time
cpu execution time for a program = cpu clock cycles fro a program / clock rate

program runs in 1 sec on computer a, has 2 ghz clock. help a computer designer build computer b, which will run program in 6 seconds.  the designer determined that a substantial increase in clock rate is possible, but this increase will affect the rest of the cpu design causing compute b to require 1.2 times as many clock cycles as computer a for this program.  what clock rate should we tell the designer to target?
1 ghz = 1 * 109 cycles / second
cpu time a = cpu clock cycles a / clock rate a => cpu clock cuddles = 10 sec * 2 * 109 cycles/sec = 20 * 109 cycles
cpu time b = 1.2 * cpu clock cycles a / clock rate b => clock rate b = (1.2 * 20 * 109 cycles) / 6 sec = 4 * 109 cycles / sec = 4 ghz
to run program in 6 seconds, computer b must have twice the clock rate of a, 1 = 2 ghz, b = 4 ghz 

cpu clock cycles = instructions for a program * average clock cycles per instruction
clock cycles per instruction cpi -  average number of clock cycles per instruction for a program

suppose we have two implementations of the same instruction set architecture.  computer a has a clock cycle time of 250 ps and cpi of 2.0 for some program, and computer b has a clock cycle time of 500 ps and a cpi of 1.2 for the same program.  which computer is faster for this program and by how much?
cpu clock cycles a = I * 2.0 => cpu time a = cpu clock cycles a * clock cycle time = I * 2.0 * 250 ps = 500 * I ps
cpu clock cycles b = I * 1.2 => cpu time b = cpu clock cycles b * clock cycle time = I * 1.2 * 500 ps = 600 I ps
cpu performance a / cpu performance b = execution time b / execution time a = (600 * I ps) / (500 * I ps) = 1.2
computer a is 1.2 times as fast as computer b for this program

cpu execution time for a program = cpu clock cycles for a program * clock cycle time
clock cycle time = 1 / clock rate
cpu time = instruction count * cpi * clock cycle time
cpu time = (instruction count * cpi) / clock rate

	type a	type b	type c		a.  which program is faster - 2
cpi 	1	2	3		b.  which program execute the most instructions? - 2
program 1	2	1	2		c.  which program has higher overall cpi - 1
program 2	4	1	1

cpu clock cycles = ∑^n_i = 1 (cpi_i * c_i)
cpu clock cycles 1 = (2 * 1) + (1 * 2) + (2 * 3) = 2 + 2 + 6 = 10 cycles
cpu clock cycles 2 = (4 * 1) + (1 * 2) + (1 * 3) = 4 + 2 + 3 = 9 cycles
cpi 1 = cpu clock cycles 1 / instruction count 1 = 10 / 5 = 2.0
cpi 2 = cpu clock cycles 2 / instruction count 2 = 9/6 = 1.5








