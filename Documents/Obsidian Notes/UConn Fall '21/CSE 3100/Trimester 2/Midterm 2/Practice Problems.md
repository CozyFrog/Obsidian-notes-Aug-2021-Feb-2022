## Client / Server Matrix
- Client takes two dimensions from standard input, num of rows and num of columns
- sends this information to server
- server then allocates m x n dimensional matrix, sends back to client that the matrix has been defined.
- client outputs this message on stdout
- client then takes m\*n values to fill the matrix with from stdin, sends to server.
- server takes these values and fills the matrix with them.
- server sends string representation of matrix to client, which outputs this to stdout

- structure:
	- server:
		- create socket
		- set up address
		- bind socket to address
		- listen
		- accept
		- hand over socket to either createArray or fillArray, based on the first value passed through the socket
	- client:
		- create socket
		- set up server address
		- set up the port (htons)
		- connect
		- use select to listen to both stdin and socket
	- fillArray:

## Remote Shell
- client:
	- create socket
	- set up server address
	- use INADDR_ANY
	- connect
	- set up FD_SET
	- start do/while loop:
		- add stdin, socket to read set
		- exit if message is equal to "$exit".
		- get nb of ready fds in the set
		- if stdin, take input through scanf
		- if socket, read input one byte at a time, store in buffer, send buffer through standard output
- server:
	- create socket
	- set up server address
	- bind sock to address
	- listen
	- loop:
		- set up client address
		- accept
		- redirect standard out, in, err of child to socket
		- exec zsh
		- parent waits

## Send file
Send file from client to server
Server puts file in its folder