- For office hours:
	- structure is: lock, wait in a loop, do stuff, and broadcast. How does any thread get through the wait?
	- "If the lock is unavailable, the OS must put the thread to sleep. When the lock is released, one sleeper must become runnable."

- Will we need to:
	- know how to use different types of mutexes, like errorcheck(debug)/recursive?
	- know how to use spinlocks?
	- use TLS?
	- use key/value pairs?
	- manually cancel threads?

\* <u>Answers</u>
- Mutex types
	- debug, slower
		- would not use in production.
	- recursive
		- catch: lock n times, have to unlock n times.

- spinlocks:
	- big downside is that you spin actively in place. the thread who is trying to acquire the spinlock will keep trying to get it, burning resources.
	- ACTIVE WAITING - bad if you wait for a long time, no big deal if you're only spinning a couple times.
	- useful when your critical sections are very short.
	- if you need a POSIX condition, you cannot use a spinlock.
	- you have to use at least two cores for a spinlock to make sense
	- mutex have an overhead if you have to go to sleep (that is, if you have contention).
	- spinlock are ONLY FOR THINGS with short critical sections and are computationally heavy. in that case, let's try to avoid going into the operating system.

(won't be asked about attributes)
- pthread cond attributes:
	- Laurent has "never used them in his life".
	- changing priority of a thread (pthread_create attribute)
	- wanna have detached threads (threads that do not have to join), change attribute
	- change size of the runtime stack (maybe for a recursive function) - on windows this will automatically grow. you get a segfault on all other OS's.

- pthread_exit api
	- return value is the pthread_exit failing - tells you whether the function did its job.
	- if it succeeded, it wouldn't return.