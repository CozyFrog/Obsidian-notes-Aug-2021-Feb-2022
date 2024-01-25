- dup2
	- dup2(socket,0) switches standard input with socket.
- remember to close socket / file descriptor after redirecting

send file:
~~~
void sendFile(FILE* fp, int sockfd) {
	int n;
	char data[1024] = {0};
	
	while (fgets(data, 1024, fp) != NULL) {
		if (send(sockfd, data, sizeof(data) == -1) {
			perror("[-]Error in sending file.");
			exit(1);
		}
		memset(
	}
}
~~~