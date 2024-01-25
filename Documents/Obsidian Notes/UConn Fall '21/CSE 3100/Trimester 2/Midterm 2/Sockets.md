- Server listens on port for inbound requests
- Client initiates communication with server.
	- must know server name, port number, protocol to use.

- Server:
	- create socket
	- set up address
		- set sin_family
		- sin_port
		- sin_addr.s_addr
	- pairs socket w/ address
	- bind (socket, address, size of address)
	- listen(socket)
	- loop
		- create client address
		- new socket = accept(socket, client (address), size of client)

- Client:
	- create socket
	- create srv address
	- get host by name, set hostent* server if you need to bind socket to specific IP
	- use INADDR_ANY when you don't need to bind the socket to a specific IP
	- set srv.sin_family, srv.sin_port
	- copy server->address to srv.sin_addr.s_addr
		- or set srv.sin_addr.s_addr to INADDR_ANY
	- connect (socket, srv address, size of srv)

bind() of INADDR_ANY (0) binds the socket to all available interfaces.
for a server, you typically want to bind to all interfaces.