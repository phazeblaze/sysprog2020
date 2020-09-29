# LOG WEEK 2

***System Call***
 - System call is a controlled entry point into the kernel.
 - Needed because it allows process to request kernel to do something.
 - Switches from user mode to kernel mode.
<br />

***System Call Execution***

 - An application prepares a wrapper that contains information about what function and memory should be initialized.
 - Trap handler, located in kernel space, will receive the information from the wrapper, and changes the mode from user mode to kernel mode.
 - The function then will be passed to the system call service routine.
 - After the function is performed there, it will return the results to the trap handler.
 - Trap handler will then revert the mode back to user mode and pass the result to the wrapper.
 - The wrapper then will give the result to the application.
<br />

***Error Number***

 - Errors in Unix are represented by decimal numbers, starting from 1.
 - Some system calls may return -1 even though the process is successful.
 - We include errno.h into a program to check whether an error has occurred or not.
 - In case of system calls returning -1 after a successful process, we set the value of errno.h to 0. If the process was indeed successful, the value of errno.h should be remain unchanged.
<br />

***Library Functions and System Call***

 - Library functions are inbuilt functions group in a common space called libraries to perform a specific task.
 - Some examples are **<time.h>** , **<math.h>**.
 - Some library function make a system call, some don't.
 - Functions that make a system call generally works like a wrapper.
 - Some examples of library functions that make a system call:
	 - fopen() = open()
	 - printf() = write()
 - Applications use library functions to perform system calls because it is more safer and easier. Library functions are also can be debugged, whereas system call can't.

