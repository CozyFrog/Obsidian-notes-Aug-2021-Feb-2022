Divide-and-conquer:
1. Break into subproblems that are small instances of the *same type* of problem
2. Recursively solve these subproblems
3. Appropriately combine their answers


$$\tag*{9/16/21}$$
What matters?
1. Time to aggregate solutions
2. Number of subproblems at level $k$
3. How many levels

Two main approaches to Divide & Conquer:
- <u>Divide Into</u> (e.g. binary search):
	- Divide into sets
	- Pick one set
	- Dive into set
	- Complexity: T(n) = T(n/s) + C
		- subproblems get s smaller
- <u>Dive and Aggregate</u> (e.g. mergesort):
	- Divide into sets
	- Recursively do both
	- Cleverly combine results
	- Complexity: T(n) = kT(n/s) + C
		- make k new problems, get s smaller, plus what we're doing

C is 


Mergesort
- T(n) = 2T(n/2) + O(n)
	- 2 more problems, O(n) to merge in linear time

$\\$
1. Time mostly spent at top
$\quad$What we care about:
$\quad$T(n) = 2T(n/2) + O(n)
1. Time mostly spent at bottom
$\quad$How many subproblems at bottom
1. Even
$\quad$Work at each level, how many levels
$\\$

T(n) = 2T(n/2) + O(n): Even
$\quad$Make 2 new problems each n/2 work to do, so still n at each level

T(n) = 4T(n/2) + O(n): Bottom heavy
$\quad$Making 4 new problems, each n/2, so doubles at each level.
$\quad$Doing more and more work at each level.

T(n) = 4T(n/2) + O(1): Bottom heavy
T(n) = 2T(n/2) + O(1): Bottom heavy

$\\$

# Geometric Series
$1+s+s^2+...+s^n = c$
$s+s^2+s^3+...+s^{n+1}=cs$
$s^{n+1}-1=cs-c$
$=c(s-1)$
=>$\Large c=\frac{s^{n+1}-1}{s-1}$

How does this series behave under different conditions?
s is the amount of work we're doing at each level.

if s < 1 (things get small very fast, so we only care about the top)

lim(n->infinity) $s^{n+1}$ = 0

so c goes to $\frac{1}{1-s}\leq a$ as n grows larger

if s == 1
define 0/0 as 1 (???), so 1+1+1+1 = O(n) (n ones)

if s > 1 (things get big very fast, so we only care about the bottom)
$\frac{s^{n+1}-1}{s-1}\leq aS^n$
$\frac{s^{n+1}-1}{s^n(s-1)}\leq a$
left side:
lim(n->infinity)$\Large \frac{s-\frac{1}{s^n}}{s-1}=\frac s{s-1}$

$\\$

# Master Theorem
If T(n) = aT(ceiling(n/b)) + O($n^d$)
for constants a>0, b>1, d>= 0
Then T(n) =
- O($n^d$) if d > $log_b(a)$
- O($n^dlog_b(n)$) if d = $log_ba$
- O($n^{log_ba}$) if d < $log_ba$

$log_ba$: a subproblems of size n/b

$\\$

$$\tag*{9/28/21}$$

Time = amount of time for line times number of lines

Insertion-Sort(A)
The first j items are sorted

- Show 3 properties of invariant:
	- 1) Initialization: the invariant is true before first iteration.
	- 2) Maintenance: if invariant is true before... iteration i it is true after iteration i.
	- 3) Termination: at the end invariant gives some useful property that shows algorithm correctness.

- For Insertion Sort:
	- 1) A\[0\] is sorted.
	- 2) At iteration j we retrieve A\[j\] and linearly search A\[1...j-1\] for A\[j\]'s sorted position, insert into sorted position. A\[1...j\] will be sorted.
	- 3) If j > n we terminate. Because each loop increments j by 1, we must have j = n + 1. Substitute the term. condition (j > n) into the loop invariant, A\[1...n\] is sorted.

Runtime
$$T(n)=\sum_{line\;i}cost(i)\cdot run(i)$$
$$T(n)=c_1\cdot n+c_2\cdot (n-1)+c_4\cdot (n-1)+c_5\sum_{j=2}^nt_j+c_6\sum_{j=2}^n(t_j-1)+c_7\sum_{j=2}^n(t_j-1)+c_8\sum_{j=2}^n(t_j-1)$$


- Best Case
	- shortest running time for any input
	- 
- Worst Case
	- longest running time for any input
	- $$\sum^n_{j=2}j=\sum^n_{j=1}j-1=\frac{n(n+1)}2-1=O(n^2)$$
- Average
	- average running time for any input
	- 1) distributional assumptions about data
	- 2) algorithm makes random choices

$\\$

- Algorithm for finding $k^{th}$ percentile.
	- We have $T(n)=2T(\frac n 2)+O(n)$
		- even work
		- ratio in geometric series is 1
	- We want either
		- $T(n)=T(\frac n 2)+O(n)$ or
		- $T(n)=2T(\frac n 2)+O(1)$
	- We're going to do this $T(n)=2T(\frac n 2)+O(n)$

- Problem: Selection
- Input: A list of numbers S and integer k
- Output: The $k^{th}$ smallest element of S

Looking for the median:
- selection(S,k) =
	- if $k\leq |s_L|$ selection($S_L, k$)
	- if $|S_L|<k\leq|S_L|+|S_v|$ v
	- if $k>|S_L|+|S_v|$ selection($S_R,k-|S_L|-|S_v|$)

Best case: $T(n)=T(\frac n 2)+O(n)$

Worst case (keep selecting the min):
$O(n^2)$

Best Case (select median):
$O(n)$

<u>Average Case</u>:
Choose pivot randomly that is "good enough".
>"good enough": between $25^{th}$ and $75^{th}$ percentile.

$E[T(n)]=E[T(\frac 3 4 n)+O(n)]=E[T(\frac 3 4 n)]+O(n)$
$T(n)=T(\frac 3 4 n)+O(n)$
Work at arb. level: $(\frac 3 4)^k\cdot O(n)$ - geometric series