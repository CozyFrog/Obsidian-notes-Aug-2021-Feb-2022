### Condition Variables
- Another way of coordinating threads with one another.
	- They work with mutexes.
- Thread can call wait on a cv and gives a mutex. That call locks it, puts the thread to sleep. Thread(s) get access to that mutex.

~~~
struct SBuffer +=
pthread_cond_t vacancy; 
pthread_cond_t taskAvail;
pthread_mutex_t b;

makeBuffer +=
pthread_mutex_init(&b->mtx, NULL);
pthread_cond_init(&b->vacancy);
pthread_cond_init(&b->taskAvail);

void bufferEnqueue(SBuffer* b,Task t) {
	pthread_mutex_lock(&b->mtx);
		assert(b->enter >=0 && b->enter < b->sz);
		while(b->nb == b->sz)
			pthread_cond_wait(&b->vacancy,&b->mtx);

		assert(b->nb != b->sz);
		b->data[b->enter++] = t;
		if (b->enter == b->sz)
			b->enter = 0;
		b->nb += 1;
		assert(b->nb >= 0);
		
		pthread_cond_signal(&b->taskAvail);
	pthread_mutex_unlock(&b->mtx);
}

Task bufferDequeue(SBuffer* b) {
	pthread_mutex_lock(&b->mtx);
		assert(b->leave >= 0 && b->leave < b->sz);
		while(b->nb == 0)
			pthread_cond_wait(&b->taskAvail, &b->mtx);
		assert(b->nb > 0);
		Task rv = b->data[b->leave++];
		if (b->leave == b->sz) b->leave = 0;
		b->nb -= 1;
		assert(b->nb >= 0);
		pthread_cond_signal(&b->vacancy);
	pthread_mutex_unlock(&b->mtx);
	return rv;
}

int main() {
	pthread_t aw[4];
	pthread_create(aw,NULL,consumer,&shared);
	pthread_create(aw+1,NULL,consumer,&shared);
	pthread_create(aw+2,NULL,consumer,&shared);
	pthread_create(aw+3,NULL,consumer,&shared);
}

void* producer(void* producer_thread_data) {
	SData* sd = producer_thread_data;
	int nbGen = 0;
	while(nbGen < 10000) {
		int v = random() % 15;
		Task t = {0, v, 0};
		bufferEnqueue(sd->sb,t);
		nbGen++;
	}
	// how to kill threads/consumers?
	Task et = {0,-1,0}
	bufferEnqueue(sd->sb,et);
	bufferEnqueue(sd->sb,et);
	bufferEnqueue(sd->sb,et);
	return NULL;
}

void* consumer(void* consumer_thread_data) {
	SData* sd = consumer_thread_data;
	int done = 0;
	while(!done) {
		Task t = bufferDequeue(sb->sb);
		done = (t.query == -1);
		if (!done) {
			long long asw = fact(t.query);
			printf("%p did fact(%lld) = %lld\n",
			pthread_self(),
			t.query(),
			asw);
		}
	}
}
~~~

synchronization is only in the buffer (aka the shared resource). There is no synchronization in the producer or consumer.

- what would happen if we only had one condition instead of two? (b->taskAvail, b->vacancy).
	- both enqueue and dequeue would wake when one of them finished - it would work but it would be inefficient.
	- would wake up all producers, all consumers every time you woke up everybody.

Focus on understanding the <u>POSIX condition</u>.
Mutex and POSIX condition are the only two that are critical to understand.

- Can you use a spinlock with a condition?
	- No - pthread_cond_wait only takes a mutex, not a spinlock. Spinlocks are purely for mutual exclusion (spinlock is a special case of a mutex).

- 