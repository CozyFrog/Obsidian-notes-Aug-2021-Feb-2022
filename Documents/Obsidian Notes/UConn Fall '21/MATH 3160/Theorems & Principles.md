# Basic counting principle
Suppose that two experiments are to be performed. Then if experiment 1 can result in any one of m possible outcomes, and if for each outcome of experiment 1 there are n possible outcomes of experiment 2, then there are $m*n$ possible outcomes of the two experiments together.
<br>
<br>
# The Multiplication Rule
Suppose that
1) m experiments are performed in order
2) the experiment k has n<sub>k</sub> possible outcomes
Then the total # of outcomes is $n_1\cdot n_2\cdot...\cdot n_m$
<br>
<br>
# Permutations
Assume that there are n different objects. How many different ordered arrangements (permutations) of the objects are possible?
$$n(n-1)(n-2)...2\cdot1=n!$$
The number of permutation of *n* objects is equal to
$$n! := 1\cdot...\cdot n$$
with the usual convention $0!=1$
<br>
<br>
# Permutations with Identical Objects
Assume that there are n objects, of which n<sub>1</sub> are alike, n<sub>2</sub> are alike, ..., n<sub>r</sub> are alike. Then there are $\large\frac{n!}{n_1!n_2!...n_r!}$ different permutations of the n objects.
<br>
<br>
# Combinations (binomial coefficients)
<center>--------------------------------------------------------------------</center>

$$_nC_k=\frac{n!}{k!(n-k)!}\quad\text{is called the number of combinations of k objects from a set of size n.}$$
$$_nP_k=\frac{n!}{(n-k)!}\quad\text{is called the number of permutations of k objects from a set of size n.}$$
<center>--------------------------------------------------------------------</center>

The number of different groups of *k* objects chosen from a total of *n* objects is equal to
$$_nC_k={n\choose k}=\frac{n!}{k!(n-k)!}$$
This is true when the order of the selection is irrelevant.
If the order of selection is relevant, then there are
$$_nP_k=n*(n-1)*...*(n-k+1)=\frac{!n}{(n-k)!}$$
ways of choosing *k* objects out of *n*.
<br>
<br>
# Choosing *k* objects is the same as rejecting *n-k* objects
$${n\choose k}={n\choose {n-k}}$$
<br>
<br>
# Generalized Counting Principle
Suppose that *k* experiments are to be performed, with the number of possible outcomes being *n<sub>i</sub>* for the *i*th experiment. Then there are
$$n_1\cdot...\cdot n_k$$
possible outcomes of all *k* experiments together.
<br>
<br>
# Theorem 1.1 The Binomial Theorem
$$(x+y)^n=\sum_{k=0}^{n}{n \choose k}x^ky^{n-k}$$
Choose x or y from each factor. The coefficient of $x^{n-k}y^k$ is the # of ways of choosing k factors for y.
e.g. $(x+y)^4=x^4+4x^3y+6x^2y^2+4xy^3+y^4$
<br>
<br>
# Multinomial Coefficients
$${n\choose {n_1,...,n_r}}=\frac{n!}{n_1!n_2!...n_r!}$$
Then $\large{n\choose {n_1,n_2...,n_r}}$ is the # of possible divisions of n distinct objects into r distinct groups of respective sizes $n_1, n_2,...n_r$
<u>Remark</u> It is also the # of permutations with identical objects
<br>
<br>
# The Pascal's Triangle Inductive Rule
$${n\choose k}={{n-1}\choose {k-1}}+{{n-1}\choose k}$$
<br>
<br>
# The Multinomial Theorem
$$x_1+x_2+...+x_r=\sum_{n_1+...+n_r=n}{n\choose {n_1,...,n_r}}x_1^{n_1}x_2^{n_2}...x_r^{n_r}$$
$${n\choose {n_1,...,n_r}} \quad\text{is called a multinomial coefficient}$$
<br>
<br>
# The Number Of Integer Solutions
Positive:
There are $\large{{n-1}\choose {r-1}}$ positive integer solutions for the equation $x_1+x_2+...+x_r=n$.

Nonnegative:
There are $\large{{n+r-1}\choose {r-1}}={{n+r-1}\choose n}$ nonnegative integer solutions for $x_1+x_2+...+x_r=n$.
<u>e.g.</u> 10 fish are caught at a lake that contains 5 distinct types of fish.
(a) How many different outcomes are possible?
\<sol\> $x_1+x_2+x_3+x_4+x_5 = 10,\quad x_i >= 0$
Thus $\large {{n+r-1}\choose {r-1}}={{10+5-1}\choose {5-1}}=1001$