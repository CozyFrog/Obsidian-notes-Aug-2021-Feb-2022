# Sockets
## Sockets at the UNIX level
- Use the normal I/O facility of UNIX
	- These are like <u>files</u>
	- API to open / create
	- API to close
	- API to read / write

## Socket-based Communication
- Client
- Server
- Protocol
- Network Encoding
- Message Format

- Server
	- Listens on a port for inbound "let's talk" requests
	- Fundamentally passive
- Client
	- Initiates comm. w/ server
	- Must know
		- Server name
		- Port number
		- Protocol to use (TCP/UDP)
	- Fundamentally active

### Server Side
- Use Case (TCP)
	- Server <u>binds</u> a port (reserves a port) for chatting
	- Server <u>listens</u> on port for "Let's talk" requests
	- when a request comes in
		- server allocates a separate socket to <u>accept</u> private communication with the client (same host, different port)
		- orig. socket remains available
		- comm. goes on in sep. socket w/
			- <u>send/recv</u> pairs
		- conv. ends with a <u>close</u>
- UDP: similar, but no accept.

Server-Side Example:
```
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>

void checkError(int status) {
	if (status < 0) {
		printf("socket error: [%s]\n",strerror(errno));
		exit(-1);
	}
}
```