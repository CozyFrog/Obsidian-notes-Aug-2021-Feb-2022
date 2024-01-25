# <u>Normal Distribution</u>
<u>Def</u> We say that X is the <u>standard normal</u> random variable if the density function of X is given by
$$f(x)=\frac1{2\pi}e^{\frac{-x^2}{2}}$$.

<u>Thm</u> The function $f(x)=\frac1{2\pi}e^{-x^2/2}$ is a probability density, i.e. $\int^{\infty}_{-\infty}f(x)\;dx=1$.

The cdf is given by $\Phi(x)=\int^x_{-\infty}\frac1{2\pi}e^{-t^2/2}dt$.
Since f(x) is symm. w.r.t. the y-axis, we have
$$\Phi(-x)=P(X\leq x)=1-P(X\leq x)=1-\Phi(x)$$.

## $\Phi(-x)=1-\Phi(x)$
$$E(X^2)=\int^{\infty}_{-\infty}x^2\frac1{2\pi}e^{-x^2/2}dx=\frac1{2\pi}\int^{\infty}_0x^2e^{-x^2/2}dx=\int^{\infty}_{-\infty}\frac1{2\pi}e^{-x^2/2}dx=1$$.

Thus $\text{Var}(x)=E(X^2)-E(X)^2=1$.

We denote the standard normal variable by Z and write
Z=normal(0,1).

Let $X=\sigma Z+\mu$.
$E(X)=E(\sigma Z+\mu)=\sigma E(Z)+\mu$
$Var(X)=Var(\sigma Z+\mu)=\sigma^2Var(Z)=\sigma^2$
$\sigma(X)=\sqrt{\sigma^x}=\sigma$

The density function of X is
$$\Large f(x)=\frac1{\sqrt{2\pi}\sigma}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$

We write X=normal($\mu$,$\sigma^2$).
$$X=\sigma Z+\mu\;\text{<-->}\;Z=\frac{X-\mu}{\sigma}$$

<u>e.g.</u> X=normal(10,$2^2$). P($X\geq12$)=??
\<sol\> P($X\geq12$)=P($\frac{X-10}2\geq\frac{12-10}2$)=P($Z\geq1$)=1-P($Z\leq1$).