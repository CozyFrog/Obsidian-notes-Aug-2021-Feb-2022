Universe U
Interested in $S\subset U$ and $|S| << |U|$.
We want function that maps elements in U to S.
<u>preserve randomness</u>.

for hash tables $S=\{0,...,n-1\}$
IP address - $2^{32}$ possible addresses in that space U. Want to map it to smaller space S.

Map 1-$n^2$ elements to 0-(n-1) elements.
Worst case, some subset of $n^2$ elements that map to one element.

### <u>Hash Function Families</u>
h(128.38.125.99) = 128
$2^{32}$ IP addresses in U
table size is 250.then $\frac{2^{32}}{250}$ addresses are assigned to some value.

<u>Universality</u>
- For any pair of elements $u,v\in U$ the probability that a randomly chosen $h\in H$ satisfies $h(u)=h(v)$ is at most $1\over n$.
<u>Universality implies constant collisions</u>.
<u>Assume:</u>H:U->{0,...,n-1} is universal.
let $S\in U\;\;\;\;|S|\leq n\;\;\;\;u\in U$
define $X=$ number of $h(s)=h(u)$ for $s\in S$.
For a random choice $h\in H$ then $E[X]\leq 1$.

<u>Proof</u> For an element $s\in S$ r.v. $X_s=1$ if $h(s)=h(u)$ and 0 otherwise. (Bernoulli random variable).
$E[X_s]=1\cdot P(X_s=1)+0\cdot P(X_s=0)\leq \frac 1 n$
$E[X]=E[\sum_{s\in S}X_s]=\text{(linearity of expectations)}\sum_{s\in S}E[X_s]=|S|\cdot\frac 1 n\leq 1$

<u>Strategy</u>
Compute some random value based on data mod size of array. 
Size of array, or "buckets", will be a prime number.
IP address $X_1\cdot X_2\cdot X_3\cdot X_4\text{ mod 257}$.
Pick 4 random numbers.
$(a_1X_1+a_2X_2+a_3X_3+a_4X_4)\text{ mod 257}$.

$(87X_1+23X_2+125X_3+4X_4)\text{ mod 257}$.
$h_a(x_1,...,x_4)=\sum_{i=1}^4a_ix_i\%n=H$.
^ distribution over hash functions.

<u>good hash funct</u>
consider two IPs X Y
if a is chosen at random
$P\{h_a(x_1,...,x_4)=h_a(y_1,...,y_4)\}=\frac 1 n$.

1. we don't control rnadomness in data, insert randomness in alg.
2. enforce universality
3. for any two items P(collision) is 1/n. 
4. in expectation number of collisions is constant