# Moment Generating Functions

\* <u>Moment Generating Function</u>
$$M_x(t)=E(e^{tX})$$
That is,
$$M_X(t)=\sum_xe^{tX}p(x)$$
or
$$\int_{-\infty}^{\infty}e^{tX}f(x)dx.$$

\* <u>X~binomial(n, p)</u>
$M_X(t)=(pe^t+(1-p))^n.$

\* <u>X~Poisson($\lambda$)</u>
$M_X(t)=e^{\lambda(e^t-1)}.$

\* <u>X~exponential($\lambda$)</u>
$M_X(t)=\frac{\lambda}{\lambda-t}.$

\* <u>X~normal(0, 1)</u>
$M_X(t)=e^{\frac{t^2}{2}}.$