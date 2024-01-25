- creating processes, forking
- all the ways to create sockets
- client/server programs
- semaphores, shared memory

### Matrix Multiplication - O(n^3)
If you have n^2 processors, divy up work among processors.

How do you know when you're done?

Need to set up pipe so you can send int product back to parent. Gets row,column info from child. Finished when matrix is full.

With therads, all live in the same address space as the parent. They have direct access to the matrices that exist in the address space of the parent.


1000 threads, 10 cores. Each thread gets 100 rows.

$\\$

IO is slow, threads can do things while we're waiting on IO.

GPUs are really bad at branching.