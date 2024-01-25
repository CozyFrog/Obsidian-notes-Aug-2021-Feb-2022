# Multivariate Distributions

### 11.1
Joint distribution for discrete and continuous random variables.

\* <u>Joint PMF for discrete random variables:</u>
$$p_{XY}(x, y)=\mathbb{P}(X=x, Y=y).$$
Recall that here the comma means <i>and</i>, or the intersection of two events.

\* <u>Joint PMF for continuous random variables:</u>
$$\mathbb{P}((X,Y)\in A)=\int\int_Af_{XY}(x,y)dxdy.$$
In particular, for $A={(x,y):a\leq x\leq b,c\leq y\leq d}$ we have $$P(a\leq X\leq b,c\leq Y\leq d)=\int_a^b\int_c^df_{X,Y}(x,y)dydx.$$

- Example: If the density $f_{X,Y}(x,y)=ce^{-x}e^{-2y}$ for $0<x<\infty$ and $x<y<\infty$, what is c?
- Solution: we use the fact that a density must integrate to 1. So
$$\int_0^{\infty}\int_x^{\infty}ce^{-x}e^{-2y}dydx=1.$$
- c = 6.
- The multivariate distribution function (CDF) of (X,Y) is defined by $F_{X,Y}(x,y)=\mathbb{P}(X\leq x,Y\leq y)$. In the continuous case, this is
$$F_{X,Y}(x,y)=\int_{-\infty}^x\int_{-\infty}^yf_{X,Y}(x,y)dydx,$$

\* <u>Marginal PDFs:</u>
Suppose $f_{X,Y}(x,y)$ is a joint PDF of X and Y.
Marginal densities:
$$f_X(x)=\int_{-\infty}^{\infty}f_{X,Y}(x,y)dy,$$
$$f_Y(y)=\int_{-\infty}^{\infty}f_{X,Y}(x,y)dx.$$