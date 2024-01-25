Exam will be on part 2.

No problem set, lab next week, prep for exam.

post fix constantly running, listens on port for inbound connections for emails. socket connected to specific port (2525), always listening to that.

telnet localhost 2525 - telnet establishes connection, starts talking.

MAIL From: ldm@uconn.edu
-> carries over to socket
-> 250 Ok
RCPT To: joe@uconn.edu
-> 250 Ok
DATA
end with ".\n".
QUIT


send to socket:
fprintf(file*);


char buf[8192];
buf[8191] = 0;
snprintf(buf,8191,"HELLO: %s\r\n",fqdn);
socket_send(sockfd,buf);

snprintf(buf,8191,"MAIL From: %s\r\n",theMail.from);
socket_send(sockfd,buf);

snprintf(buf,8191,"MAIL To: %s\r\n",theMail.to);
socket_send(sockfd,buf);

snprintf(buf,8191,"DATA\n%s",theMail.message);
socket_send(sockfd,buf);

```
int socket_send(int sid, char* message) {
	int sent = 0;
	
	int length = strlen(message);
	int rem -= length;
	DEBUG_MSG("Sending...");
	DEBUG_MSG(message);
	while (sent < length) {
		int nbSent = write(sid, 
	}
}
```


which - \<executable name\>
e.g. which grep: /usr/bin/grep