- Mono* ptr = (Mono*)malloc(sizeof(Mono));
- The following forms are equivalent
	- ptr\[0\].coef = 1;	(Array Bracket Style)
	- (\*ptr\*).coef = 1;	(Deference Style)
	- ptr->coef = 1;		(Arrow Style)

$\\$

- Union Types
	- Have the ability for a value to take different form / types
	- Only takes one at a time
	- 
![[Screen Shot 2021-09-27 at 8.41.30 AM.png]]

$\\$

- Bit Fields
	- A short requires two bytes, or 16 bits.
	- 7 bits for age 0 - 128
	- 2 bits for 3 genders
	- 3 bits for 7 species

struct Census {
$\quad$short age$\quad$: 7;
$\quad$short gender$\quad$: 2;
$\quad$short species$\quad$: 3;
};


$\\$

- Function Pointers
	- \*(char\*\*)s1
	- s1 is a void pointer
	- cast it to char\*\*
	- \* dereferences it, which means we're now accessing the value at char\*
- Pointers to functions are stateless Lambdas!

$\\$

- 