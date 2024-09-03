#  lecture 4

**thursday, august 29 2024**

**cs 394 computer architecture**

##  technologies for processors and memory

**performance per unit cost of technology** is relative performance

**vacuum tube** is an electronic component that was widely used in the early electronic devices before the advent of transistors

**transistors** are an on/off switch controlled by an electric signal

**very large scale integrated vlsi circuit** is a device containing hundreds of thousands to millions of transistors in a chip.

**the chip manufacturing processor** starts with an **ingot** which is a silicon crystal ingot, then a **wafter** which is a slice from an ingot, **defects** which are a microscopic flow that can result in the failure of a die are removed, then a **die** which is the individual rectangular sections that are cut from a wafer.

##  performance

what is performance of computers?

which airplane performs better?  what variables are important, speed, capacity, range throughput?

**throughput** aka bandwidth is the number of tasks completed per unit time

**response time** aka **execution time** is the total time required for the computer to complete a task

performance is performance = 1 / execution time

if a computer a runs a program in 10 seconds and computer b runs the same program in 15 seconds, then performance of a / performance of b = execution time of b / execution time of a = 15 / 10 = 1.5.  computer a is 1.5 times faster than computer b.

**cpu execution time** also called **cpu time** is the actual time the cpu spends computing for specific tasks

**user cpu time** is the cpu time spent in a program itself

**system cpu time** is the cpu time spent in the operating system performing tasks on behalf of the program

**clock cycle** also called cycle or **tick** is the time for one clock period, which runs at a constant rate

**clock period** is the length of each clock cycle.  clock cycle time = 1 / clock rate

