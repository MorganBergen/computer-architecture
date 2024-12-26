#  memory hierarchy

1.  [introduction](#introduction)
2.  [memory technologies](#memory-technologies)
3.  [the basic of caches](#the-basic-of-caches)
4.  [virtual machines](#virtual-machines)
5.  [virtual memory](#virtual-memory)
6.  [measuring and improving cache performance](#measuring-and-improving-cache-performance)
7.  [questions and answers](#questions-and-answers)

##  introduction

from the earliest days of computing, programmers have wanted unlimited amounts of fast memory.  the topics in this section aid programmers by creating that illusions.  before we look at creating the illusion, let's consider a simple analogy that illustrates the key principles and mechanisms that we use.

suppose you were a student writing a term paper on important historical developments in computer hardware.  you are sitting at a desk in a library with a collection of books that you have pulled from the shelves and are examining.  you find that several of the important computers that you need to write about are described in the books you have, but there is nothing about the edsac.  therefore, you go back to the shelves of books on the desk in front of you, there is a high probability that many of the topics you need can be found in them, and you may spend most of your time just using the books on the desk without returning to the shelves.  having several books on the desk in front of you saves time compared to having only one book there and constantly having to go back to the shelves to return it and take out another.

the same principle allows us to create the illusion of a large memory that we can access as fast as a very small memory.  just as you did not need to access all the books in the library at once with equal probability, a program does not access all of its code or data at once with equal probability.  otherwise, it would be impossible to make most memory accesses fast and still have large memory in computers, just as it would be impossible for you to fit all the library books on your desk and still find what you wanted quickly.  

this underlies both the way in which you did you work in the library and the way that programs operate.  the principle of locality states that programs access a relatively small portion of their address space at any instant of time, just as you accessed a very small portion of the library's collection.  there are two different types of locality **temporal locality** and **spatial locality**.

**temporal locality**  (locality in time) -  if an item is referenced, it will tend to be referenced again soon.  if you recently brought a book to your desk to look at, you will probably need to look at it again soon.

**spatial locality**  (locality in space) -  if an item is referenced, items whose addresses are close by will tend to be referenced soon.  for example, when you brought out the book on early english computers to learn about the edsace, you also noticed that there was another book shelved next to it about early mechanical computers, so you likewise brought back that book and, later on, found something useful in that book.  libraries put books on the same topic together on the same shelves to increase spatial locality.  we'll see how memory hierarchies use spatial locality a little later in this chapter.

##  memory technologies



##  the basic of caches

##  virtual machines

##  virtual memory

##  measuring and improving cache performance

##  questions and answers

instructions may exhibit temporal locality, but never spatial locality?  

false.  instructions may exhibit both temporal and spatial locality.  instructions are accessed sequentially in the absence of a jump, thus showing spatial locality.  instructions within a loop are executed repeatedly, thus showing temporal locality.

data may exhibit spatial locality, but never temporal locality?

true.  data may exhibit both spatial and temporal locality.  sequential access to arrays or strings show spatial locality.  data within a loop are accessed repeatedly, thus showing temporal locality.

##  key terms

**temporal locality** -  the locality principle stating that if a data location is referenced then it will tend to be referenced again soon.  essentially the reuse of a specific resource within a short time is temporal locality.

**spatial locality** the locality principle stating that if a data location is referenced, data locations with nearby addresses will tend to be referenced soon.  the use of resources stored closely together is known as spatial locality.

