#  lecture 7 

**cs 394 computer architecture**

**tuesday, september 10 2024**

##  cpu performance and its factors

clock cycle time = 1 / clock rate

clock rate = 1 / clock cycle time

cpu execution time = cpu clock cycles / clock cycle time

cpu execution time = cpu clock cycles / clock rate

our favorite program runs in 10 seconds on computer a, which has a 2 ghz clock.  we are trying to help a computer designer build a computer b, which will run this program in 6 seconds.  the designer has determined that a substantial increase in the clock rate is possible, but this increase will affect the rest of the cpu design, causing computer b to require 1.2 times as many clock cycles as computer a for this program.  what clock rate should we tell the designer to target?

cpu time a = cpu clock cycles a / clock rate a $\rightarrow$ cpu clock cycles = 10 sec $\times$ 2 $\times$ 10^9 cycles/sec = 20 $\times$ 10^9 cycles

cpu time b = 1.2 $\times$ cpu clock cycles b / clock rate b $\rightarrow$  = 1.2 $\times$ 20 $\times$ 10^9 cycles / 6 seconds = 0.2 $\times$ 20 $\times$ 10^9 cycles = 4 $\times$ 10^9 cycles = 4 ghz

to run the program in 6 seconds, b must have twice the clock rate of a, a = 2 ghz, b = 4 ghz

##  translation

how can a program written in l2 be executed by the computer? 

via translation, replace each instruction in the l2 program by an equivalent sequence of instructions in l2.  the new l1 program is then executed by the computer.

via interpretation, an l1 program examines the l2 program instructions by instruction and executes the equivalent sequence of l1 instructions directly.

level 5 - problem oriented language level 

$\downarrow$ translation compiler

level 4 -  assembly language level

$\downarrow$ translation assembler

level 3 - operating system machine level

$\downarrow$ partial interpretation operating system

level 2 - instruction set instruction level

$\downarrow$ interpretation microprogram or direct execution

level 1 -  microarchitecture level 

$\downarrow$ hardware

level 0 -  digital logic level

##  multilevel machine

**in 1940s two level computer**

isa level (software)

digital logic level (hardware)

**in 1950s three level computer**

isa level (software)

micro architecture level (simplified hardware, complicated logic, design rectification, big fix, cheap, flexible)

digital logic level hardware

**in 1960s four level computer**

operating system machine level 

automate the operators job (scheduling and load balancing)

more instructions / functionalities

input / output operations

multitasking (time sharing)

isa level software, machine instruction set

micro architecture level registers, alu, data path

simplified hardware, complicated logic, design rectification, bug fix, cheap, flexible

digital logic level hardware, gates

##  computer generations

zeroth generation - mechanical computers 1642 - 1945

first generation - vacuum tube computers 1945 - 1955

second generation -  transistors 1955 - 1965

third generation -  integrated circuits 1965 - 1980

four generation - very large scale integration 1980 - ?

##  zeroth generation - mechanical computers 1642 - 1945

first calculating machine by pascal in 1642

babbage 1792 - 1871 different engine, speedometer

analytical engine - storage memory 1000 words of 50 decimal digits, mill computation unit - add, subtract, multiply, divide, input section punched card reader, and output section punched and printed output

##  first generation - vacuum tube computers 1945 - 1955

enigma thomas jefferson former u.s. president

vacuum tubes - eniac electronic numerical integrator and computer, 18,000 vts and 1,500 relays, 30 tons, 140 kw power

the original von neumann machine - cpu memory unified, i/o

the harvard machine - cpu, memory (split into instruction and data), i/o

##  second generation - transistors 1955 - 1965

transistor - tiny electronic switch

size, power, cost

programmed data processor pdp

mit, tx-0

ibm 7094

pdp-1, mit

concept of supercomputers (cray)

##  third generation - integrated circuits 1965 - 1980

integrated circuit (ic) - dozens of transistors in a chip

ibm system / 360, multiprogramming

##  fourth generation - very large scale integration 1980 - ?

vlsi - millions of transistors in a chip

ibm personal computer pc, intel cpu

graphical user interface gui

fpga field programmable gate array

##  moore's law and processor design

gordon earle moore co-founder and chairman emeritus of intel corp

moore's law predicts a 60 percent annual increase in the number of transistors that can be put on a chip (transistors doubles every two years)

what is the importance / significance of moore's law

more transistors - larger memory, powerful processor

in the past 50 years or so, semiconductor industry is moving ahead faster than any other

in the past 50 years or so, computer / processor industry is moving ahead faster

design more powerful computers at the same or lower price

##  fifth generation - low power and invisible computers

embedded systems

internet of things iot, artificial intelligence

gridpad first tablet from grid systems 1989

pda personal digital assistant, smartphone simon

##  fifth generation - multicore computers 2000 - ?

vlsi - millions of transistors in a chip

2001, power4, first dual core chip microprocessor, imb

advanced vlsi - billions of transistors in a chip 2008

system on a chip soc

network on a chip noc

multicore / many core systems

##  disposable computers

rfid radio frequency identification

##  microcontrollers

controls devices such sa alarm clock, micro ove, etc

hardware software systems

embedded systems

##  game computer and personal computers

game computer - special graphics sound cards, need powerful processors

personal computers - general purpose, need powerful processors

##  servers and clusters of work stations

servers - faster more disk space, faster network connection

##  mainframe and supercomputers

mainframe 

more i/o capacity, vast disk space, not faster than server

supercomputer

##  handheld mobile device