By default, every process has one thread.

Part 2: coming to terms with multiple processes running at one time. One thread in each of these processes.

Intel 6 cores, 12 threads, but not all instructions run in parallel. This is hardware threads - don't confuse them! 

# PS Command
returns list of processes

PS aux gives all the processes on the machine

$\\$

# Pipes

$ A | B - processes a, b, want output of A to be the input of B so that data flows right from one to the other.

In the creation of the pipe, the shell never dies.

- Steps:
- Parent process will be shell
	- Need a pipe between the two processes. The pipe is basically a pair of file descriptors: one you can write to and one you can read from.
		- Created before fork - you want A and B to have access to pipe, otherwise the children would have a reference to the pipe. By virtue of forking, we get a new address space / new file descriptor table that references the SAME FILES as the parent.

# Review file descriptors


gdb - when debugging, you can follow a fork to a child.

<mark>Practice this early...</mark>