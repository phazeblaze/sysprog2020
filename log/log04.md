# LOG WEEK 4

***Program, process, and thread***
- **Program** is an executable file containing a set of instructions designed to do a specific job on your computer.
	- Example: chrome.exe, word.exe
	- Programs are not stored on the primary memory, rather on secondary memory
	- Programs are sometimes referred as passive entity
- **Process** is an executing instance of program.
	- Referred as active entity
	- Several instance of process can be related to a same program. Ex: opening 5 windows of Notepad
- **Thread** is the smallest executable unit of a process.
- A Process can have multiple threads, with each thread has their own specific task and execution.
- All threads of the same process share the same memory.
- When we execute a fork() syscall into a running process, it will spawn a **child process** for the parent process (process that called fork()).
	- Both processes run concurrently, and execute the same instructions.
	- Both processes use the same program counter, CPU registers, and open files.
- In the case of fork() and child processes, it is preferable to use _exit() instead of exit(), due to _exit()'s nature of immediately exiting and not doing any cleanups.
	- exit() will clean up data, so using it on a child process can lead to data interference with the parent.
<br/>

***Process ID and ps***
- Process ID (PID) is a number that identifies a unique process.
- Users can get the PID of a process by calling getpid().
	- For child processes, they can get their parent's PID by using get ppid().
- By default, the highest number of PID is 32767, though this number can be higher on 64-bit systems.
- Knowing PID can be useful in certain situations, for example when you want to kill() a process, or get information about a process.
- ps can be used in various situations, such as getting users that created a certain process, seeing every process on the system, and more.
	- These options can be accessed by using the manual (man ps).
- ps can also be used to get information, some of the information that can be provided are:
	- PID : Process ID of the process. 
	-  USER : Process creator. 
	- PR: Priority of the process, also known as PRI 
	-  NI: Nice value, used for priority.  
	- VIRT: Virtual size of the process. 
	- RSS: Resident Set Size, amount of physical memory used by the process. 
	- S: Minimal state display of the process. 
	-  %CPU: Percentage of CPU used by the process. 
	- %MEM: Percentage of memory used by the process. 
	- TIME+: Cumulative time for the process. 
	- COMMAND: Command name.
<br/>

***Process States***
- There are four different types of process states:
	- Running : Process is either running or ready to run. 
	-  Waiting : Process is waiting for for an event or for a resource. 
	-  Stopped : Process is stopped. 
	-  Zombie : Process is dead but still has an entry in the process table.
- **Zombie process** is a result of a child process died after the parent process has finished their process.
	- Too many zombie processes can result in PIDs running out due to zombie processes still having an entry in the process table.
	- This can be prevented by suspending the parent process by using wait() until the child process is terminated.
- **Orphan process** is a running process whose parent process is already finished or terminated.
	- This can be done intentionally or unintentionally. Intentional orphan process usually leads to daemon process.
- **Daemon process** is a process that is running in the background.
	- Technically they still have a parent, as they are adopted by init.
