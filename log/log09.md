# LOG WEEK 9

**Daemon**
- Daemon is a process that is long-lived. It runs from start-up to shut-down.
- It runs in the background with no connecting terminals.
- Examples of daemons:
	- cron
	- sshd
	- httpd
	- inetd
	- hostapd
- CRON is a daemon that will execute commands on schedule (ex: Doing backups every day at 1 am)
- Steps to make a daemon process:
	- fork
		- parent exits
		- child adopted by init
		- child continues in the background
	- child calls setsid, makes a new session and process group with the child as its leader.
	- if daemon opens terminal later it might require a controlling terminal O_NOCTTY on open
	- clear process umask
	- change cwd typically to root “/”, for safety reasons
	- close all open file descriptors
	- open /dev/null -> dup2(fd, 0,1,2)
- Guideline for writing daemon codes:
	- A daemon typically terminates only when the system shuts down. Many standard daemons are stopped by application-specific scripts executed
	- Every Daemon will receive SIGTERM (15) 5 seconds before SIGKILL sent by init process. The Daemon should do the immediate cleanup process before the SIGKILL arrived
	- Since daemons are long-lived, we must be particularly wary of possible memory leaks
	- Many daemons need to ensure that just one instance of the daemon is active at one time
- Using SIGHUP to re-init daemon:
	- mechanism to reload configuration without restarting the daemon
	- daemon doesn't have a controlling terminal
- We can put a task in the background by adding & at the end.
	- ex: ./job1.sh &
- We can kill background jobs by using kill -9/15 on the process.
- To bring a process from background to foreground, we can do [fg PID].
- To make sure a process won't receive a SIGHUP signal, we can add nohup before the process/job
	- ex: nohup ./job1.sh

