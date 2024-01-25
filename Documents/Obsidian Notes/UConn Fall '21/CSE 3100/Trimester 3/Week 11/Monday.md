- Read in 
	- read a chunk at a time (small buffer, say 256 bytes)
	- go back, read more
	- don't know size - keep going until EOF. select will tell you EOF.


$\\$


- Surprised that nobody was above 30 points after 2 hours.
- Plagiarism? Grade will be delayed a bit.
- Final will be a project.
	- Shouldn't fail bc you panic, you should fail bc you don't know.
	- Project will give space we need (about 48 hours).
	- Will be last week of the term.


$\\$

Mutex types (SPThreads-3 p17)- PTHREAD_MUTEX_DEFAULT? Up to OS to define behavior.

How to recognize contention? 2 or more threads trying to play with the same thing at the same time. Increasing a counter is high contention.
High contention tends to happen when you're compute-bound, low contention IO-bound.
If you have high contention, really try to pay attention to this. MUTEXes are expensive.
High contention \> high cost \> spinlock, not mutex.
Won't spin for very long, either.
One core, spinlock doesn't make sense.

- What does it take to do coarse grain locking on a linked list?
	- lock head and tail, append/prepend.
	- insert sorted?
		- have to find the insertion spot in the list (takes O(n) time). do you need the lock to find the spot in the list? Yes! The position might change.

The point of the game is that we're taking the lock way too long bc we have the lock on the entire list.

As many locks as we have elements in the list. How do you use these locks?
Lock between the ranges that you're using?

Lock list like a ladder - when you're holding, you have two hands on the ladder.

Grab first node, lock. Reach for next node, lock next. Unlock previous, lock next next. Insert between two locked nodes, then unlock.