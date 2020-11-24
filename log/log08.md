# LOG WEEK 8

**Signals**
- A signal is a notification to a process that an event has occurred.
- A process can send a signal to another process.
- Signals are usually defined as a small integer.
- Kernel generates signals when:
	- Hardware Exception occured
	- Typed in by the user (Ctrl+Z)
	- Software event occured (timer, process termination, etc.)
- Depending on the signal, some actions will be carried to the process, such as terminating the process, ignoring the signal, generating core dump file, and others.
- Trap handler are used when we want to do certain actions after a signal is received.
	- Bash has the 'trap' command that lets the programmer execute a method when the defined signal is received.
- SIGKILL/SIGTERM cannot be trapped or ignored, as they are usually a last-resort signal to kill a script. Trapping these signals could mean a script can run as long as it wants and won't get stopped.
- Some signals have a keyboard shortcut.
	- SIGINT with Ctrl+C
	- SIGQUIT with CTRL+\
