- Motivation
	- Every time you want to carry out a computation on your machine, you are creating a program, an executable, and when it gets loaded in memory it creates an abstraction that the OS calls a "process".
	- This is at the core of every OS.
	- Represents an executable that has been loaded in memory & is executing. It's the executable and also the state of the processor, state of whatever else it's using.
	- Organization in OS.
		- Processes form a tree rooted at "init".
		- Every other process has a parent.
		- Every process has between 0 and n children.


- Process Life-cycle
	- Birth
		- From another process.
		- Starts life as a clone of the parent process.
			- Either command-line interface or GUI.
		- The process upgrades itself to running a different executable.
		- Process retains access to the files open by the parent.
	- Life
		- Process can create children processes.
	- Death
		- Eventually calls exit or abort to "suicide".
		- Could also be "killed".


- Birth via Cloning
	- Done with API called "Fork". Takes no args, returns one result.
	- In the parent process:
		- fork returns the process identifier of the child.
		- If a failure occurs, returns -1 (sets errno).
	- In the child process: fork returns 0.


- Cloning effect on address space
	- The parent and the cloned child
		- Are virtually indistuingishable.
		- All memory is 100% identical.
		- But are distinct copies.
		- Any memory changes (stack/heap/static) only affect the caller.
		- Thus the parent and their clone quickly diverge.


- Concurrency
	- The parent and child both return from fork.
		- Both can run at the same time on a multicore machine.
		- You cannot assume as to who returns first.


- Usage
	- The parent forks. When the fork returns, test the return value.
	- if 0: we are the child!
	- if > 0: we are the parent and the child was born.
	- if < 0: we are the parent and the child was not born.
	- Branch based on this value.

API:
```
int main() {
	pid_t = value;	# pid = Process IDentifier
	value = fork();
	printf("In main: value = %d\n", value);
	return 0;
}
```
Output:
```
src (master) $ cc fork.c
src (master) $ ./a.out
In main: value = 63689
In main: value = 0
```


Two calls to fork().
API:
```
int main() {
	pid_t = value;	# pid = Process IDentifier
	value = fork();
	value = fork();
	printf("In main: value = %d\n", value);
	return 0;
}
```
Output:
```
src (master) $ cc fork.c
src (master) $ ./a.out
In main: value = 63745
In main: value = 0
In main: value = 63746
In main: value = 0
```

This is because the child of the first fork forks when it hits the second call to fork().


- Waiting on a child
	- Two simple APIs
		- pid_t wait(int \*stat_loc);
		- pid_t	waitpid(pid_t pid, int \*stat_loc, int options);
	- Blocks the calling process until a child dies.
	- Reports in \*stat_loc

![[Screen Shot 2021-10-03 at 4.07.07 PM.png]]
How does wait() work here?

$\\$

- Process Upgrades
	- Usually a fresh clone wants to run different code.
	- This can easily be done:
		- Child guts themselves
		- Reloads the process address space with another executable.
	- Note: Opened files are NOT AFFECTED by the operation.

- The exec family
	- The act of 'gutting and upgrading' is done by the child with a sys call.
	- The call (execl) takes as input
		- The path to the executable to load inside our own address space.
		- A list of args to be passed to the new exec.
		- A final NULL pointer to give the 'end of arg list'.
	- Note:
		- If successful, execl does not return! instead control is transferred to the main func. of the new exec.

- Inheritance
	- Whenever a parent forks, the child inherits all the parent's file descriptors.


- Redirections
	- Simply change the files corresponding to
		- stdin (0) | stdout (1) | stderr (2)

