#  lecture 3

**cs 394 computer architecture**

**tuesday, august 27 2024**

##  introduction

####  important questions

-  how are high level language programs translated into the hardware language, and how does the hardware execute the program?
-  what is performance, and how can a programmer improve it?
-  what techniques can be used by hardware designers to improve performance and energy efficiency?
-  since 1950, what great ideas did computer architects come up with that lay the foundation of modern computing?

##  terabyte (tb) vs. tebibyte (tib)

1 tb = $2^{12}$ bytes 

1 tib = $2^{40}$ bytes

| decimal      | abbreviation | value     | binary term    | abbreviation | value    | % larger |
|:------------:|:------------:|:---------:|:--------------:|:------------:|:--------:|:--------:|
| kilobyte     | kb           | $10^3$    | kibibyte       | kib          | $2^{10}$ | 2%       |
| megabyte     | mb           | $10^6$    | mebibyte       | mib          | $2^{20}$ | 5%       |
| gigabyte     | gb           | $10^9$    | gibibyte       | gib          | $2^{30}$ | 7%       |
| terabyte     | tb           | $10^{12}$ | tebibyte       | tib          | $2^{40}$ | 10%      |
| petabyte     | pb           | $10^{15}$ | pebibyte       | pib          | $2^{50}$ | 13%      |
| exabyte      | eb           | $10^{18}$ | exbibyte       | eib          | $2^{60}$ | 15%      |
| zettabyte    | zb           | $10^{21}$ | zebibyte       | zib          | $2^{70}$ | 18%      |
| yottabyte    | yb           | $10^{24}$ | yobibyte       | yob          | $2^{80}$ | 21%      |

##  computing systems - two approaches

####  a multilevel approach

-  the tanenbaum and austin book structured computer organization
-  higher (human friendly) to lower (machine friendly)
-  [multilevel computers](https://users.cs.fiu.edu/~downeyt/cop3402/levels.html)

####  a quantitative approach

-  the hennessy and patterson book
-  quantitative principle of computer design -  to make the common case fast
-  to quantify the principles $/rightarrow$ amdahl's law, cpu performance, principle of locality, advantage of parallelism, etc.
-  [quantitative principles of computer design](https://www.brainkart.com/article/Quantitative-Principles-of-Computer-Design_8830/)

##  eight great ideas about computer architecture

-  design for moore's law
-  use abstraction to simplify design
-  make the common case fast
-  performance via parallelism
-  performance via pipelining
-  performance via prediction
-  hierarchy of memories
-  dependability via redundancy

-  performance via parallelism -  a drummer's stick breaks, but he quickly grabs another one and continues playing the song
-  performance via pipelining -  a brother is washing and drying dishes.  his sister helps by drying each dish immediately after the brother washes each
-  performance via prediction -  a mom expects her son will be hungry after a long airplane flight, so she cooks dinner just in case.  if he's not hungry, she'll whip up a dessert instead
-  dependability via redundancy -  a drummer's stick breaks, but he quickly grabs another one and continues playing the song.

##  below your program

####  abstraction

-  abstraction is a fundamental concept in computing that helps manage complexity by hiding the intricate details of a system and exposing only the essential features.
-  it allows one to work with higher level concepts without needing to understand the underlying specific

**high level languages** -  programming languages that provide a high degree of abstraction from the hardware, making it easier for programmers to write code.  a portable language such as c that is composed of words and algebraic notation that can be translated by a compiler into assembly language

**systems software** -  software that provides services that are commonly useful, including operating systems, compilers, loaders, and assemblers

**operating system** -  supervising program that manages the resource of a computer for the benefit of the programs that run on that computer

**compiler** -  a program that translates high level language statements into assembly language statements

**assembly language** -  a symbolic representation of machine instructions

**machine language** -  a binary representation of machine instructions

**instruction** -  a command the computer hardware understands and obeys

##  under the covers

the underlying hardware in any computer performs the same basic functions -  inputting data, outputting data, processing data, and storing data.

important components

**input device** -  keyboard

**output device** -  display

**memory** -  stores programs and data | cache -  a small fast memory

**dynamic random access memory dram** -  integrated circuit ic

**static random access memory sram** -  integrated circuit ic, faster than dram

**datapath** -  performs operations on data

**control** -  signals that determine the operation of the datapath

**integrated circuit** -  also called a chip.  a device combining dozens to millions of transistors

**central processor unit cpu** -  also called a **processor**.  the active part of the computer, which contains that datapath and control and which adds numbers, and so on

**instruction set architecture** -  also called **architecture**.  an abstract interface between the hardware and the lowest level software that encompasses all the information necessary to write a machine language program

**implementation** -  hardware that obeys the architecture abstraction

**volatile memory** -  storage such as dram that retains data only if it is receiving power

**nonvolatile memory** -  storage that retains data even in the absence of power supply; used to store programs and data.  example -  hard disk

**main memory** -  also called **primary memory**.  memory used to hold programs and data while execution; typically consists of dram.

**secondary memory** -  nonvolatile memory used to store programs and data; typically consists of magnetic disks and flash memory.

**magnetic disk** -  also called **hard disk**.  a form of nonvolatile secondary memory composed of rotating platters.

**flash memory** -  a nonvolatile semiconductor memory.

**input** -  writes data to memory.  an input device feeds information to a computer.  input may come from various sources, like a keyboard, mouse, microphone, touchscreen, a network connected with another computer, etc.

**output** -  reads data from memory.  an output device conveys the result of a computation to a user.  output may go to various destinations, like a display, a speaker, or a network connected with another computer.

**memory** -  stores instructions and data.  many different memory types exist, even within a single computer.

**control** -  sends signals that determine the operation of the other components.  control and datapath are commonly together and called a processor.

**datapath** -  performs computations.  the datapath is where data is transformed via computations like addition or subtraction.  control and datapath are commonly together and called a processor.

