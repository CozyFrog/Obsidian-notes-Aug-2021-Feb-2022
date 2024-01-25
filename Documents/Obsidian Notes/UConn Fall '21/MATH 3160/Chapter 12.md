# Expectations
\* <u>Covariance</u>
Definition: $Cov(X,Y)=E(XY)-E(X)E(Y).$
Note: if X and Y are independent then Cov(X,Y)=0.
![[Screen Shot 2021-11-27 at 12.03.36 PM.png]]

Lemma:
![[Screen Shot 2021-11-27 at 12.04.14 PM.png]]

Theorem (Var. of sum of independent random variables):
![[Screen Shot 2021-11-27 at 12.04.46 PM.png]]

Example:
![[Screen Shot 2021-11-27 at 12.05.21 PM.png]]

$\\$

\* <u>Conditional Expectation</u>
Definition: The <u>conditional expectation</u> of X given that Y=y is
$$E(X|Y=y)=\sum_xxP_{X|Y}(x|y)=\sum_xP(X=x|Y=y),$$
or
$$E(X|Y=y)=\int_{-\infty}^{\infty}xf_{X|Y}(x|y)=\int_{-\infty}^{\infty}x\frac{f(x,y)}{f_Y(y)}dx.$$