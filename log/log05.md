# LOG WEEK 5

***Virtual Memory***
- Virtual memory is one of the most important components in OS.
- It allows users to run more program than what the physical memory can handle.
	- Because RAM is limited, there can be a point where it will run out of space and unable to run another application.
- Virtual Memory is a simulated memory written to a file in hard drive. That file is called **page file** or **swap file**.
- Virtual memory has a process called **swapping**.
	- The process will swap programs from RAM to hard drive and vice versa depending on the activity of the program (is it actively used, etc.)
- Advantages of virtual memory:
	- Allows users to run multiple programs at once
	- Helpful when implementing multiprogramming environment
	- Processes that require a segment of a program can be faster.
- Disadvantages of virtual memory:
	- Programs that un in hard drive is slower than in RAM.
	- Could negatively affect system performance.
	- Takes space in the hard drive.
<br/>

***Memory Leak***
- Memory leak happens when a program takes memory, but doesn't free it back, resulting in wasted memory space.
	- One example of this is when you reach an *OutOfMemoryError* in Java, this means that a memory leak happened.
- When memory leak happens, it means that the limit of virtual memory has been reached.
- Memory leaks won't allow us to allocate blocks anymore because there are no more free blocks.
- Some reasons as to how memory leak happens:
	- not free()-ing up malloc()
	- touching bytes outside given allocation
	- errors in the code that allows memory leaks to happen
- Generally, memory leaks are hard to find. There are libraries for the purpose of seeking out memory leaks in a program.

***malloc()***
- malloc() is a function that allows the programmer to allocate a certain amount of blocks for the caller.
- malloc() will try to find free blocks with the size that the caller wants, and if its available, it will return a pointer to that block.
- blocks allocated by malloc() are not initialized yet.
- When a malloc() function fails/encountered an error, it will return NULL. Null return can also happen when a malloc() call with the size of 0 is successful.
- free() is a function that allows programmer to free up memory blocks that has been used or allocated before.
	- doing free() at the right time can prevent memory leaks from happening.
