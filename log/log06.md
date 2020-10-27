# LOG WEEK 6

***Makefile***
- Makefile is a file containing a set of dependencies and targets that is executed in order to do a certain job.
- It can be executed by using the command 'make' in a directory where Makefile is present.
- Makefile is usually used to compile C programs, although it can also be used to do other jobs as well, such as web deployment
- Using Makefile saves a considerable amount of time, as various commands and jobs can be placed in a file and executed at once.
- It is also good for distribution, as it is very easy to execute. People who doesn't know much about programming can do it easily.
- Makefile consists of a set of dependencies (target and dependent) and rules (how to make the target)
	- It will usually look like this:
	- target_1 : dependencies
		- commands
	- target_2:
		- commands
	- and so on.
- By default, it will build the first target listed in the Makefile (in the example above, target_1 will be the first target)
- There are also additional arguments when you launch make:
	- make -n : dry-run
	- make -k : keep going even if there's errors.
- When we are about to make a target, we check if there are modifications to the dependencies. If there are newer modifications, rebuild the target.
