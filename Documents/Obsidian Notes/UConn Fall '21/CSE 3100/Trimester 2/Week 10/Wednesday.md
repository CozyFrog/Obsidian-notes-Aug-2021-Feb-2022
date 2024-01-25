# Exam:

Processes
Forking
Execing
Pipes

Sockets
Select

No shared virtual memory
No semaphores

[Video summaries](https://courses.engr.uconn.edu/moodle/mod/page/view.php?id=2851)

Mostly setting up sockets

- Non-blocking sockets will not be necessary.
	- but should know how to use them.

- send strings, get strings back
	- do you send binary 0 at the end of the string?
	- no, you don't.
	- it will be confusing - what you do when you deal with an application that's line-oriented, you send a line feed '\\n' at the end.

can you read more than one byte with a blocking socket if you don't know how long the message is?

- send file to 5 people, can send to all 5.
- as the server, send chunks of server to 5 partners.
- simply write, it may block, therefore server is blocking, but there are still 4 other guys to send to.
- ready to write to because the buffer has been cleared.
	- who's ready? when you write you send the # of bytes you wrote.  let's send a megabyte, write tells nah we've only sent 100 kb. have to repeat logic to send data.

write_fd: want to send to multiple at the same time.

$\\$

Friday recommendation: 

$\\$

# Lecture (Threads)
What we have access to is memory. 
Executing concurrently and making use of a shared structure in memory. What you need to protect is what lives in memory.
Virtual memory provides protection for an entire address space.

You can still access memory without the lock.
The protocol has to be followed by every player.

```
void* (*start_routine)(void*)
	pointer to a function, (*start_routine)
	takes a (void*)
	return void* (or return NULL)
```

```
void* increase(void* cnt) {
	int i;
	for (i = 0; i< cnt; i++) 
		x = x + 1;
	return cnt;
}

pthread_t tid1, tid2;
int status;
long cnt = atol(argv[1]); // converts string to long

// status = pthread_create(&tid1,NULL,(void*(*)(void*))increase,(void*)cnt);
// status = pthread_create(&tid2,NULL,(void*(*)(void*))increase,(void*)cnt);
status = pthread_create(&tid1,NULL,increase,(void*)cnt);
status = pthread_create(&tid2,NULL,increase,(void*)cnt);
```

call pthread_join to pick up the value that it returns (parent does that).