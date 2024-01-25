<u>Continuous Random Variables</u>
In many situations, random variables can take any value in R.

<u>Def</u> A random variable X is said to have a <u>continuous distribution</u> with <u>density function</u> f(x) if we have
$$P(a\leq X\leq b)=\int_a^bf(x)dx$$

<u>Def</u> X: continuous with density f(x)
Define
1. $E(X)=\int_{-\infty}^{\infty}xf(x)dx$, and
2. $Var(X)=E(X^2)-E(X)^2$.

\*<u>Uniform Random Variable</u>
$f(x)=\frac1{b-a}\text{if a < x < b, otherwise }0$

Cumulative Distribution Function (cdf) is given by
$$F(x)=\int_{-\infty}^xf(t)dt=0\;x\geq a, \frac{x-a}{b-a}\; a\leq x \leq b,\;1 \; x\geq b$$

\* <u>Properties of a CDF</u>
Recall: A CDF F(x) is defined by $F(x)=P(X\leq x)$.
<u>Prop</u>
1. If $a/leq b$ then $F(a)\leq F(b)$, i.e. F is non-decreasing.
2. lim as b goes to inf., F(b) = 1. lim as b goes to ninf., F(b) = 0.
3. $P(a<X\leq b)=F(b)-F(a)$.

$\\$

# Questions
- Find CDF
- Find E(X)
- Find Var(X)
- Find probability of given range of X