~~~
int barrierWait(thread_arg_t* bar) {
	int st = 0;
	int myGen = 0;
	st = pthread_mutex_lock(&bar->m);
	if (st) return st;
	myGen = bar->gen;
	bar->count++;
	bar->left++;
	while (bar->count < bar->sz && myGen == bar->gen)
		pthread_cond_wait(&bar->c, &bar->m);
	if (myGen == bar->gen) {
		pthread_cond_broadcast(&bar->c);
		bar->gen++;
		bar->count = 0;
	}
	if (--bar->left == 0)
		st = 1;
	pthread_mutex_unlock(&bar->m);
	return st;
}
~~~

\* <u>What does count maintain?</u>
- Count is how many guys are inside the barrier.

\* <u>What does left maintain?</u>
- How many are left from the previous generation.
- You have those who are sitting because they have not gotten up yet and those who are here for the next class. Need to be able to tell them apart - the point of left is to count the # that haven't stood up yet.
- If my barrier has 10 slots, it has <i>10 slots per generation</i>.

\* <u>How do you sort a large array?</u>
- Quicksort, mergesort.
	- Mergesort bc it's always O(nlog(n))

\* <u>Mergesort with Threads</u>
- Each time you have an array, you use two threads to work on each side.
- Merge once they are done, go to next phase.

\* <u>Lab</u>
- Selection sort w/ threads.
- They have to meet in order to do work. Meet w/ temp. result.
- Generations, counts. Code for barrier is similar.