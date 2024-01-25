# Server-Side Example
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
[[Code Snippets from week 07 vids.#exit|exit()]]
```
int main(int argc,char* argv[]) {
	// Create a socket
	int sid = socket(PF_INET,SOCK_STREAM,0);
	
	// setup our address -- will listen on 8080 --
	struct sockaddr_in addr;
	addr.sin_family = AF_INET;
	addr.sin_port = htons(8080);
	addr.sin_addr.s_addr = INADDR_ANY;
	// pairs the newly created socket with the requested address.
	int status = bind(sid,(struct sockaddr*)&addr,sizeof(addr));
	checkError(status);
	
	// listen on that socket for "Let's talk" message.
	status = listen(sid,10);
	checkError(status);
	
	while(1) {
		struct sockaddr_in client;
		socklen_t clientSize;
		int chatSocket = accept(sid,
								(struct sockaddr*)&client,
								&clientSize);
		checkError(chatSocket);
		printf("We accepted a socket: %d\n",chatSocket);
		close(chatSocket);
	}
	return 0;
}
```
[[Code Snippets from week 07 vids.#socket int domain int type int protocol|socket()]]
[[Code Snippets from week 07 vids.#sockaddr_in#|struct sockaddr_in]]
[[Code Snippets from week 07 vids.#bind|bind()]]
[[Code Snippets from week 07 vids.#accept|accept()]]

# Client-Side Example
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

int main(int argc,char* argv[]) {
	// Create a socket
	int sid = socket(PF_INET,SOCK_STREAM,0);
	struct sockaddr_in srv;
	struct hostent* server = gethostbyname("localhost");
	srv.sin_family = AF_INET;
	srv.sin_port = htons(8080);
	memcpy(&srv.sin_addr.s_addr, server->h_addr, server->h_length);
	int status = connect(sid, (struct sockaddr*)&srv, sizeof(srv));
	checkError(status);
	return 0;
}
```

### exit()
void exit(int status) terminates the calling process immediately. open file desc. belonging to process are closed, any children of process are inh. by process 1, process parent is sent to a SIGCHLD signal.
status - status value returned to the parent process.

### socket(int domain, int type, int protocol)
- create an endpoint for communication, returns a descriptor
- PF_INET - internet version 4 protocols
- SOCK_STREAM - indicates type, spec. semantics of comm.
	- SOCK_STREAM type provides sequenced, reliable, two-way connection based byte streams.
- <u>domain</u> parameter specs. a comm. domain within which comm. will take place; selects the prot. fam which should be used. fams are defined in \<sys/socket.h\>.
- protocol specifies a partic. prot. to be used w/ socket.

### struct sockaddr_in
Address format
- an IP socket addrress is def. as a comb. of an IP interface address and a 16-bit port number. basic IP prot. does not supply port numbers, they are implemented by higher level protocols. on raw sockets sin_port is set to the ip protocol.
- sin_addr is the IP host address.
	- s_addr member of struct in_addr contains the host interface address in network byte orrder
```
struct sockaddr_in {
	short			sin_family;		// address family: AF_INET
	unsigned short	sin_port;		// port in network byte order
	struct in_addr	sin_addr;		// internet address
}

/* Internet address */
struct in_addr {
	uint32_t	s_addr;		// address in network byte order
}
```

### bind()
- bind a name to a socket
- int bind(int sockfd, const struct sockaddr\* addr, socklen_t addrlen);
	- when a socket is created with *socket()*, it exists in a name space (address fam.) but has no addr. assigned to it. *bind()* assigns the address specified by *addr* to the socket referred to by the file descriptor *sockfd*. *addrlen* specifies the size, in bytes, of the address structure pointed to by *addr*. "assigning a name to a socket".

### accept()
- accept a connection on a socket
- accept(int socket, struct sockaddr* addr, socklen_t* addr_len);
	- arg socket is a socket that has been created with socket(), bound to addr. with bind, and is listening for connections after a listen(). accept() extracts the first connection request on the queue of pending connections, creates a new socket with the same props. of socket, and allocates a new fd for the socket.

### conneect()
- connect(int socket, const struct sockaddr* address, socklen_t address_len)
- initiate a connection on a socket