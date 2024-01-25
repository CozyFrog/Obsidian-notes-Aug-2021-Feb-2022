Activity Selection Algorithm:
- Repeat until there are no more valid options:
	1. Pick the job with the smallest finish time.
	2. Remove all jobs that conflict with that job from the remaining jobs.

- Proof (by Contradiction):
	1. Suppose we are given a set of n activities S, with start and finish times for each activity.
	2. We make choices of which activities to include. We always choose the next nonconflicting activity with the smallest finish time.
	3. Let our algorithm be suboptimal.
	4. Assume that there is some subset of S called S' where |S'| is the maximum (note that activities cannot overlap).
	5. ith choice in our alg can either be in S' or not be in S'.
	6. If c_i is in S', extend and finish.
	7. If c_i is not in S':
		1. The ith activity in S' must have a later finish time than our c_i, as c_i has a later finish time than all c_1,...,c_i-1 (which are in S') and an earlier finish time than all c_i+1,...,c_n.

$\\$

Job Scheduling Algorithm:
- Repeat until there are no more valid options:
	1. Pick the job with the earliest deadline.
	2. Append this job to the end of our schedule.