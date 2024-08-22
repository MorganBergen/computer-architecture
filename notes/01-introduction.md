#  01 computer abstraction and technology

1.  [introduction](#introduction) 
2.  [eight great ideas in computer architecture](#eight-great-ideas-in-computer-architecture)
3.  [below your program](#below-your-program) 
4.  [under the covers](#under-the-covers) 
5.  [technologies for building processors and memory](#technologies-for-building-processors-and-memory)
6.  [performance](#performance) 
7.  [the power wall](#the-power-wall) 
8.  [the sea change -  the switch from uniprocessors to multiprocessors](#the-sea-change---the-switch-from-uniprocessors-to-multiprocessors) 
9.  [real stuff -  benchmarking the intel core i7](#real-stuff---benchmarking-the-intel-core-i7) 
10.  [fallacies and pitfalls](#fallacies-and-pitfalls) 
11.  [concluding remarks](#concluding-remarks)
12.  [historical perspective and further reading](#historical-perspective-and-further-reading) <br>

**cs 394 computer architecture**

**august 22 2024**

##  introduction

computers have led to a third revolution for civilization, with the information revolution taking its place alongside the agricultural and the industrial revolutions.  each time the cost of computing proves by another factor of 10 as the computer revolution continues, the opportunities for computers multiply.  applications that were economically infeasible suddenly become practical.

**computers in automobiles**  computers reduce pollution, improve fuel efficiency via engine control, and increase safety through blind spot warnings, lane departure warnings, moving object detection, and air bag inflation to protect occupants in a crash.

**cell phones**  half of the planet has mobile phones, allowing person to person communication all across the world.

**human genome project**  computer equipment to map and analyze human dna sequences.  

**world wide web**  the web has replaced libraries and newspapers

**search engines**  as the content of web grew in size and in value, finding relevant information becauses increasingly important.  today, many people rely on search engines for such a large part of their lives that would be a hardship to go without them.

hardware advances have allowed programmers to create wonderfully useful software, which explains why computers are omnipresent.  

###  classes of computing applications and their characteristics

computers are used in three different classes of applications.  

**personal computers** are possibly the best form of computing.  personal computer emphasize delivery of good performance to single users at a low cast and usually execute third-party software.  

**servers** are the modern form of what were once much larger computers, and are usually accessed only via a network.  servers are oriented to carrying large workloads, which may consist of either single complex applications - usually a scientific or engineering application - or handling many small jobs, such as would occur in building a large web server.  these applications are usually based on software from another source such as a database or simulation system, but are often modified or customized for a particular function.  servers are built from the same basic technology as desktop computers, but provide for greater computing, storage, and input/output capacity.  in general, servers also place a greater emphasis on dependability, since a crash is usually more costly than it would be on a single pc.

**supercomputers** consist of tens of thousands of processors and many **terabytes** of memory, and cost tens of hundreds of millions of dollars.  supercomputers are usually used for high end scientific and engineering calculations.  

**embedded computers** are the largest class of computers and span the widest range of applications and performance.  embedded computers include the microprocessors found in your car, in a tv set, and the network of processors that control a modern airplane or cargo ship.  embedded computing system are designed to run one application or one set of related applications that are normally integrated with the hardware and delivered as a single system.


**the full range of decimal and binary values and names for memory sizes**

|  decimal term |  abbreviation  | value      | binary term | abbreviation | value        | % larger |
|:--------------|:---------------|:-----------|:------------|:-------------|:-------------:|:-------:|
| kilobyte      |  kb            | $10^{3 }$  | kibibyte    | kib          |   $2^{10}$   |  2%      |
| megabyte      |  mb            | $10^{6 }$  | mebibyte    | mib          |   $2^{20}$   |  5%      |
| gigabyte      |  gb            | $10^{9 }$  | gibibyte    | gib          |   $2^{30}$   |  7%      |
| terabyte      |  tb            | $10^{12}$  | tebibyte    | tib          |   $2^{40}$   |  10%     |
| petabyte      |  pb            | $10^{15}$  | pebibyte    | pib          |   $2^{50}$   |  13%     |
| exabyte       |  eb            | $10^{18}$  | exbibyte    | eib          |   $2^{60}$   |  15%     |
| zettabyte     |  zb            | $10^{21}$  | zebibyte    | zib          |   $2^{70}$   |  18%     |
| yottabyte     |  yb            | $10^{24}$  | yobibyte    | yib          |   $2^{80}$   |  21%     |


###  terms

**personal computer** -  a computer designed for use by an individual, usually incorporating a graphics display, a keyboard, and a mouse.

**server** -  a computer used for running larger programs for multiple users, often simultaneously, and typically accessed only via a network.

**supercomputer** -  a class of computers with the highest performance and cost; they are configured as servers and typically cost tens to hundreds of millions of dollars.

**terabyte tb** -  originally $1,099,511,627,776$ / $2^{40}$ bytes, although communications and secondary storage systems developers started using the term to mean $1,000,000,000,000$ or $10^{12}$ bytes.  to reduce confusion, we now use the term **tebibyte (tib**) for $20^{40}$ bytes, defining terabyte (tb) to mean $10^{12}$ bytes.



