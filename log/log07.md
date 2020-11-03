# LOG WEEK 7

- Shell script is a file containing commands that can be executed in a Unix terminal.
- It allows programmers to execute multiple commands by using one file.	
	- It also allows for more complex tasks, as doing so in the terminal could be bothersome.
- Unix primarily uses Bourne shell (sh) and Bash(bash), while Windows has their own shell called PowerShell (msh).
- For some commands, it is required to use sudo.
	- sudo is used when you need permission to do certain actions, such as changing user permissions, file ownership, etc.
- Pipeline allows output of one command to be immediately used as an input for another command.
- Other than the standard packages, you can install other packages that may not be installed yet by using sudo apt install [package name]
- When you open a Unix terminal, there is usually a line that consists of your username and present working directory, among other things. This line is called a shell prompt. You can see the full command of a shell prompt by doing echo $PS1.
	- This shell prompt can be customized depending on the user's taste. To permanently change it, however, users must insert the new PS1 to the .bashrc file for that user.
- 
