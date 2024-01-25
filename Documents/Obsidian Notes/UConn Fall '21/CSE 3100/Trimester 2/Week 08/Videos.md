- Summary of Week 07:
	- Forking the parent process
		- The child can carry on convo concurr.
		- Parent can start receiving more "let's talk" messages
		- parent, little work
		- child, core of work
- Message encoding / formatting is important

$\\$

When you call accept, it blocks. Forces you to use fork().
Better solutions?

- Take 1
	- Multiplexing several IO channels: the *select* system call
	- Pro: old-school, reliable, one thread
	- Cons: possibly complex, tricky race w/ blocking IO and sockets
- Take 2
	- Mult. threads to handle concurr. sockets
	- Pro: simple, reliable as longa s you are good with threads
	- Cons: limit on numbers of threads on 32-bit arch.

$\\$

# Blocking & Non-blocking
- By default
	- sockets are blocking
		- accept
		- recv
		- send
		- ...
- Meaning
	- if a call wishes to read data, no data, block
	- if a call wishes to write in a buffer and buffer is full, block

## Non-blocking sockets
- With those the behavior changes the APIs
	- send/recv/accept/... never block
- if no data to read, returns -1, sets errno to EWOULDBLOCK

Loop - data? no data. data? no data... 
active polling

use fcntl API. given socket, F_GETFL, returns the flags (options assoc/ with socket).
[[Screen Shot 2021-10-14 at 7.34.03 PM.png]]

```
int select(int nfds,	// nfds: id of highest # file desc. in 3 sets
			fd_set *readfds,	// sets
			fd_set *writefds,	
			fd_set *errorfds,
			struct timeval * timeout);
```
- fd set API:
	- void FD_ZERO(fd_set \*fdset);
		- creates empty set
	- void FD_CLR(fd, fd_set \*fdset);
		- removes fd from fd set
	- void FD_SET(fd, fd_set \*fdset);
		- adds fd to fd set
	- int FD_ISSET(fd, fd_set \*fdset);
		- membership test on fd in fd set
![[Screen Shot 2021-10-18 at 11.27.23 AM.png]]


## Select
- Input
	- three sets of fds to <u>listen</u> to.
		- ready for reading, ready for writing, ready for errors
	- reading set
		- can contain sockets ready to <u>accept</u>
		- can contain classic fds, like stdin
	- nfds arg is the max fd value + 1
	- returns total # of desc. that are ready.


fd_set - set of file descriptors

look up read buffer api


## Memory Mappings
### Files as Memory
- Idea: map a file into the grey area of memory, then access it just like memory.

- APIs:
	- \#include \<sys/mman.h\>
	- mmap
		- create a mapping
	- munmap
		- destroy mapping
- inputs
	- address where to place it
		- must be page-aligned
			- 0, 4096, (mult. of 4096).
	- size of mapping (in bytes, must be page-size multiple)
	- permissions for accessing content
	- type of map
	- file desc. for source
	- offset to start mapping from (0 means from the start)
![[Screen Shot 2021-10-17 at 9.09.55 PM.png]]

- real address is the one that mmap returns.
- writes to memory will translate to writes to file once you unmap that memory.


## Use Memory Map Across Processes
- Concurrency & Processes
- Possible through Shared Virtual Memory 
	- pretend file -> memory zone
	- a SHARED mapping (as opposed to a PRIVATE mapping)

- shm_open(const char* name, int oflag, ...);
	- shared mem. object referenced by name is opened for reading and/or writing as specified by oflag and a file descriptor is returned to the calling process. 
		- O_RDONLY
		- O_RDWR
		- O_CREAT
		- O_EXCL
		- O_TRUNC
	- flag: S_IRWXU (seems to be read/write/execute permission).
- 
- memset(void* b, int c, size_t len);
	- fill a byte string with a byte value.
	- writes len bytes of value c to the string b. returns its first arg.


## Semaphore
- Flag that can be high (go ahead) or low (don't touch this)
	- sem_wait
		- if flag is high, perm. granted
		- flag is low, go to sleep
	- sem_post
		- done playing, put flag back up

