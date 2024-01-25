- pid_t - just a signed int, used to represent process ids.
- size_t - unsigned int
- ssize_t - same as size_t, but signed type

- Wait on child:
	- \#include \<sys/wait.h\>
	- pid_t wait(int\* stat_loc);
	- pid_t waitpid(pid_t pid, int\* stat_loc, int options);
		- block the calling process until a child dies
		- reports in \*stat_lock the cause of death and the exit status

- Reaping:
	- when parent is alive, parent attends to the dead processes by waiting on them.
	- when parent is dead, either

- Remember IO APIs
	- The f family (fopen,fclose,fread,fgetc,fscanf,fprintf,...)
	- All use a FILE\* abstraction to rep. a file
	- All rely on buffering in the C library
	- Support line-ending translation when opening in text mode
- UNIX has lower-level API for file handling
	- directly mapped to system calls
	- no buffering
	- raw IO
	- uses OS level file descriptors