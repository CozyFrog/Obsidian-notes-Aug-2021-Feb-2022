# Some Continuous Distributions

## Exponential Random Variable
For some $\lambda>0$, the density function is

$$\displaystyle   
f(x)=\left\{ \begin{array}{ll}  
\lambda e^{-\lambda x} & x\geq 0 \\  
0 & x < 0  
\end{array} \right.$$

Note: $\int_0^{\infty}x^ne^{-x}dx=n!$.
Assume X=exponential($\lambda$). Then
$$\displaystyle
\begin{array}{lll}
E(X) & =\frac1{\lambda}\\
E(X^2) & =\frac2{\lambda^2}\\
Var(X) & =\frac1{\lambda^2}
\end{array}$$

For $x\geq 0$, $F(x)=1-e^{-\lambda x}$ and 0 otherwise.


## Gamma Random Variable
- The distribution of the amount of time one has to wait until a total of n events has occured.
- $\Gamma(n,\lambda)$.
- $E(X)=\frac{\alpha}{\lambda}$
- $Var(X)=\frac{\alpha}{\lambda^2}$
For $\alpha,\lambda>0$ the density function is
$$f(x)=\frac{\lambda e^{-\lambda x}(\lambda x)^{\alpha-1}}{\Gamma(\alpha)}\text{ if }x\geq 0$$
where $\Gamma(\alpha)=\int_0^{\infty}x^{\alpha-1}e^{-x}dx=(\alpha-1)\Gamma(\alpha-1)$
Thus, $\Gamma(n)=(n-1)!$ for $n>0$.

## Beta Distribution
- $E(X)=\frac{\alpha}{\alpha+\beta}$
- $Var(X)=\frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}$
For $\alpha,\beta >0$, the pdf (probability distribution function) is
$$f(x)=\frac{x^{\alpha-1}(1-x)^{\beta-1}}{B(\alpha,\beta)},0<x<1$$
where $B(\alpha,\beta)=\frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)=\int_0^{\infty}x^{\alpha-1}(1-x)^{\beta-1}dx}$ is the beta function.

## Cauchy Distribution
For $\theta\in\mathbb R$, the pdf is
$$f(x)=\frac{1}{\pi[1+(x-\theta)^2]},x\in\mathbb R$$

## Student's T-Distribution
For $\nu>0$, the pdf is
$$f(x)=\frac{\Gamma(\frac{\nu+1}{2})}{\sqrt{\nu\pi}\;\Gamma(\frac{\nu}2)}\left(1+\frac{x^2}{\nu}\right)^{-\frac{\nu+1}{2}},x\in\mathbb R$$
$$\displaystyle
E(X)=0,\;\;Var(x)=\left\{\begin{array}{ll}
\frac{\nu}{\nu-1} & \text{ if }\nu>2\\
\infty & \text{ if } 1<\nu\leq2,\\
\text{undefined} & \text{otherwise}
\end{array}\right.$$