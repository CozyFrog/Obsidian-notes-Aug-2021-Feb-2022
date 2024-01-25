Q1: Pipe in, pipe out
	- same functionality as running the UNIX command
	- showmounts takes its input from the command line and that input is a simple string meant to match filesystem names.
	- set up processes and pipes 
	
A1: 
	- showmounts behaves the same as running "df -h | grep tmpfs"
	- Set up pipe
	- fork
	- Exec child to program in /bin
		- execute specific binaries
		- program name is name passed by command line
	- df - lists existing file systems.
		- child has access to the SAME ARGV of the parent. everything on the command line.
		- sends output to the correct end of the pipe.
	- set input of 2nd child to read end of the pipe.
	- output goes to standard out.
	- parent should wait on the two PIDs we got back
- Key issues:
	- wait on children
	- make sure to CLOSE ALL PIPES
	- when to fork? where are inputs and outputs coming from and going to?
	- <mark>list of unix commands?</mark>

Read question, come up with plan.
Lay out plan:
	- need fork
	- calls to exec
	- input comes through cli, not stdin
	- how do you relay that to the child processes?
	- if it's stdin, you might have to redirect
	
### unix command which - "which df" -> /bin/df

### unalias
used to remove entries from the current user's list of aliases
- list of aliases?

Q2: Get that web page and clean it
- that was the lab.
scan string, copy parts of it into other buffers

$\\$

Q3: You wanna chat? select - ively.

Chat rooms. Implement a pair of programs: a server (ircd) and a chat room client (irc). Pair follows a pattern: client wishes to talk to a server, one can execute a client from a terminal with: ./irc \<hostname\>
for instance, ./irc localhost would connect to a server running on localhost (on port 8075). a client simply reads messages from the keyboard and sends them to the server. when a response comes from the server, it displays the response on its standard output.

<mark>- brush up on remote shell, example done in class.</mark>

server waits for "let's talk" requests from clients on port 8075. when a request arrives the server adds the socket of the client to an array of sockets to talk and then immediately goes back to accepting. what the server does not do is fork a child process. instead the server handles all the communications directly thanks to the select API. given n client sockets and the server socket, the server simply needs to listen to all of them and when one socket has data ready to read, it can handle that socket.

if it is the serevr socket, it is yet another client trying to join the chat room.

if it is a client socket, then it can read the message from that client and send it on its way to all the othre clients. (message is a string fo text whose last char is a line feed).

if a client wants to terminate the chatroom, it can send the special message "\$exit\n", to which the server and all the clients should react to by displaying the message and then terminating the chat. it is a bit rude to term. the chat on one user, but it is simple.

- select listens to multiple sockets.
	- server can listen to 6 client sockets and the server client, so it can accept new clients while taking input from other existing clients.
	- works with files, file descriptors, any sockets
	- if server socket is ready, 
	- if client socket is ready, 


$\\$


for performance, pass structs by pointer most of the time.
memcpy?

why do while?
you need to do it at least once (could do while(!done) and do the same thing).