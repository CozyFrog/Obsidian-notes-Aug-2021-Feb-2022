- linux cmmd: who
	- tells who is using the machine


- What needs to happen?
	- one solution:
		- run a different process that process will exec who? who has an output? we can pipe back to parent process
		- parent process will run pump that will dump data into the socket.
	- better solution:
		- have the child pump directly into the socket
		- fork, ask child to do something
		- after fork, child will have socket
	- child process will run who, sends output on stdout. how do we make it so the output goes straight into the pipe? redirection
		- close stdout of the child, dup socket FD into stdout


review formats, socket (sid? line 50 in rwho.c)