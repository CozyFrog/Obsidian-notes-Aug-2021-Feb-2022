# Conditional Probability
Definition: The conditional probability of B given that A has occured is defined as 
$$\large P(B|A) = \frac{P(A\cap B)}{P(A)}$$

\* We have $P(A\cap B)=P(A)P(B|A)$

$\\$

# Law of Total Probability
$B_1,B_2,...,B_k$: disjoint events such that $\large\cup_{i=1}^kB_i=S$.

$$\large P(A)=\sum_{i=1}^kP(A|B_i)P(B_i)$$

![[Screen Shot 2021-09-20 at 2.49.05 PM.png]]
![[Screen Shot 2021-09-20 at 2.49.15 PM.png]]

$\\$

# Bayes' Formula
$B_1,B_2,...,B_k$: disjoint events such that $\large\cup_{i=1}^kB_i=S$.

$$\large P(B_1|A)=\frac{P(A|B_1)P(B_1)}{\sum_{i=1}^kP(A|B_i)P(B_i)}$$
$P(B_i)$: Prior
$P(A|B_i)$: likelihood
posterior is proportional to likelihood times prior

![[Screen Shot 2021-09-20 at 2.51.51 PM.png]]
![[Screen Shot 2021-09-20 at 2.51.59 PM.png]]