# LOG WEEK 1

***Application Programming and System Programming***
 - Application Programming is user-oriented, while System Programming is hardware oriented and application-oriented.
 - Example of Application Programming : word processor, games, and softwares that could help a user.
 - Example of Systems Programming: disk defragmenter, operating systems, game engine.
 - System programming requires a greater degree of hardware awareness.
<br />

***Scripting and Programming Language***

 - In terms of executing a program, scripting language doesn’t require your program to be compiled first, while programming language requires your program to be compiled.
 
|                |Scripting                        |Programming                      |
|----------------|-------------------------------|-----------------------------|
|Compile before execute?|No          |Yes            |
|Involved with UI?         |No           |Yes, usually            |
|Written with Object-oriented?         |No|Yes, but depends on the language
 - One example of a language that can do both is Python.
<br />

***Kernel***

 - Kernel is the core of an operating system.
 - Some of the tasks kernel does:
	 - Process scheduling
	 - Memory management
	 - File system
	 - Access to devices
	 - Networking
	 - System call API
 - CPU usually operates in at least two different modes:
	 - **User Mode** doesn't have direct access to hardware or memory, and if there's a crash, then only the app involved will crash.
	 - **Kernel Mode** does have direct access to hardware or memory, but crashes in this mode can lead to more severe results. Blue screens are one example of crashes in kernel mode.
<br />

***Directory, Shell and Manual***

 - . indicates this directory
 - . . indicates the parent of pwd
 - / is the root of the directory hierarchy
 - pwd is present working directory. This command will show the absolute path of the current directory. Example : if you're in a folder Folder1, which is in the folder Folder2, then the pwd would be: **/home/Folder2/Folder1**.
 - Absolute path starts from the root (as seen in example above), meanwhile relative path starts from pwd. Example: for text1.txt in Folder1, if we are already in Folder1 the relative path would be **./text1.txt** .
 - Shell is the terminal for users to communicate with kernel.
 - The **man** command allows user to see the manual for a given command.
	 - For example, **man rm** will give the user the manual for the command **rm**.

