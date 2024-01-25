Some Discrete Distributions.

![[Screen Shot 2021-10-13 at 8.41.25 PM.png]]

$\\$

# Bernoulli Random Variable
An experiment whose outcome is a success or a failure.

$\\$

# Binomial Random Variable
Repeat trial n times, each trial is independent and outcome for each trial is success or failure.
- Parameters:
	- n: number of trials
	- p: probability of success at each trial
$$P(X=k)=_nC_kp^k(1-p)^{n-k}$$

$\\$

# Poisson Random Variable
If $X-binom(n,p)$ with n large enough & p small enough, $X\approx poisson(\lambda)$ where $\lambda=n\cdot p$.
$$p(k)=e^{-\lambda}\frac{\lambda^k}{k!}\text{for k=0,1,2,...}$$

$\\$

# Geometric Distribution
X = # of trials until a success occurs.
$$P(X=k)=(1-p)^{k-1}p\;\text{for k=1,2,...}$$

$\\$

# Negative Binomial Random Variable
X = # of trials until *r* success occur.
$$P(k)={{k-1}\choose {r-1}}p^r(1-p)^{k-r}\;\text{for k=r,r+1,...}$$

$\\$

# Hypergeometric Random Variable
Choose n items from a set of N, m number of one particular kind of item.
Example: Choose n balls from set of N, where m are red and N-m are blue. X = # of red balls.

$$P(X=k)=\frac{_mC_k\cdot _{N-m}C_{n-k}}{_NC_n}$$
$$E(X)=\frac{mn}N=np$$
$$Var(X)=np(1-p)(1-\frac{n-1}{N-1})$$
where we set $p=\frac m N$.