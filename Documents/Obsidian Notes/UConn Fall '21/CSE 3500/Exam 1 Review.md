Q0:
$n^{10}=O(n^{20})$
$2^n=\Omega (\frac 3 2)^n$
$10^{\log_2n}=\Theta (n^{\log_210})$

buildMaxHeap = $O(n)$
for loop: M
while loop: $\log_{10} n$
total: $m\log_{10}n+n$ - can't get rid of n

$\\$
Q1:
$2^k$ subproblems, each of size $O(\frac n 4)^k$.
Total work at arbitrary level = $O(n\log n)$

$\\$
Q2:
3 loop invariants for binary search.

$\\$
Q3:
Divide sets of lists by two, recurse.
Once you have one list, return.
Merge those lists.

$\\$
Q4:
array size n.
size of dp table: n by k+1. O(nk)

k = 2, so two rows.
either he sung no times, sung once, or sung twice.

only way to get to (i,j) is from (i-1,j-1).
remember, values could be negative.