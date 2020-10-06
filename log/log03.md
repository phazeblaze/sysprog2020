# LOG WEEK 3

***Stat system call***
- Stat syscall gives us detailed information about a file using stat structure.
- Some information that can be seen using stat structure are ID of device containing file, inode number, owner, size, time of last access/mod/status change, blocksize.
- stat system call has some variation such as: stat, fstat, lstat, fstatat. These commands generally work the same, but with some slight differences.
	- stat and lstat for example, works differently when the pathname given is a symbolic link.

***File descriptors and I/O***
- File descriptor is an integer used in system calls to refer to an open file description.
- Some processes doesn't have a file descriptors, one example being daemon processes
	- Daemon processes run in the background, and while doing so it closes opened file descriptors for the process.
- It is possible to use close() on standard file descriptors, although doing so will risk your program crashing and other programs and libraries may be affected as well.
- Generally opening a file (open()) without closing it (close()) is fine, but if it keeps happening at one point all available file descriptors will run out, resulting in subsequent file openings failing.
