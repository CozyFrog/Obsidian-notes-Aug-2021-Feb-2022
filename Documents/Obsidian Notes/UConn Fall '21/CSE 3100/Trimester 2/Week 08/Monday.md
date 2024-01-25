Q: What does the 0666 permissions parameter do?
A: read, write, execute. set permissions individually for each. 
- man chmod
- 0400, 0200 - allow read by owner, allow write by owner.
- 0040, 0020, allow read by group members, allow write by group members
- 0004, 0002, allow read by others, allow write by others

go+rx = give read, execute perms to group (g) and other (o).

- accomodations room: tls 154

- Midterm 2:
	- First week of november (november 5th).


server is a shell
listening for inbound connec.
clone itself, runs shell. client talks to shell, call & response, terminate child. self-termination of the server, have a command to actually stop the server.

- run shell:
	- exec shell


- What is the point?
	- in who, the client was tapping the server on the shoulder and getting back result of the who command.
		- poke, data, print
	- now poke, you get a shell, send command, shell respond, etc.
- data in client can be coming from two sources
	- shell (server, over socket)
	- standard input
- server accepts -> forks, gives to child the socket.
	- clone will be shell script. takes data from stdin, sends result to stdout. takes data from stdin, it's coming across the socket.
	- before load shell into clone, redirect the socket so it becomes the stdin of the shell. redirect output to the same socket. (redirect error, too). then exec.
	- when process dies, it ends and the files get closed. socket gets closed.