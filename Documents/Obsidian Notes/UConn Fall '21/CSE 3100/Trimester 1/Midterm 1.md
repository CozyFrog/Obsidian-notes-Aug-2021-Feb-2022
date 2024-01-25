Concepts:
- C
	- Processes
	- Address Space
	- Data Types
		- Scalars
		- ADTs in C
		- Compound
			- Arrays
			- Unions
			- Structures
			- Pointers
	- Functions
		- Calling Convention
		- Iterative
		- Recursive
	- Control Flow
		- if-then-else
		- switch
		- while
		- for
	- Tools
		- Make
		- Compile
		- Link
		- Debugging
		- Valgrind


$\\$

# SPC 1
- Central Dogma of C:
	- Computations are object of interest
	- Procedures are main abstraction tool
		- Caller / Callee dichotomy
	- Programming means
		- organizing processes as procedures
		- composing processes through procedure calls

- Assignments ARE NOT Statements
	- They are *expressions*, which means you can chain them
<mark>Q: Definition of statements, expressions</mark>

- Operator Precedence:
![[Screen Shot 2021-09-27 at 10.39.06 AM.png]]

- Basic Data Types:
![[Screen Shot 2021-09-27 at 10.39.29 AM.png]]

- Characters
	- 8-bit wide (1 byte)
![[Screen Shot 2021-09-27 at 10.40.05 AM.png]]
![[Screen Shot 2021-09-27 at 10.40.25 AM.png]]

- MACROS
	- always uppercase
	- format: "#define MACRO value"

- Switch Statements
	- switch(expression) {
		- case label0: \<block0\>; break;
		- case label1: \<block1\>; break;
		- ...
		- default: \<blockn\>
	- }


- Functions
	- Fundamental Language tool used to build procedural abstractions

- Context <u>Frames</u>
	- Created automatically when function is called
	- Contain a "copy" of the func. arguments (call by value!)
	- Contains a copy of the function local names
	- Discarded automatically when leaving function
	- Nothing in the frame survives the call

$\\$

- Memory Organization
	- Every process has an address space
![[Screen Shot 2021-09-27 at 10.48.20 AM.png]]
	- 	Executable code is at the bottom
	- 	Statics are just above
	- 	Stack is at the top, going down
	- 	Heap grows from above statics, going up
	- 	Gray no-man's land is up for grab
![[Screen Shot 2021-09-27 at 10.49.12 AM.png]]

$\\$

# SPC 2
- Arrays
	- Is a type constructor
	- Produces a new type
- Cannot assign a whole array at once to another array

- Compound Types (Structures)
	- Structures have a type *name*
	- Can have multiple fields
		- Fields can have any legal type (basic types, structures, arrays, etc.)
- Definition
	- Define a value




- size_t
	- returned by the sizeof operator
	- unsigned integer type of at least 16 bit
	- used to represent the size of an object
	- as an implication, size_t is a type guaranteed to hold any array index


- string literals
	- char* x =  is a string literal; attempting to modify it will yield a segfault
- char array
	- char x\[\] = "string" is a char array. it allocates memory and copies the string into it.

$\\$
# IO
- IO done one character (8-bits, one byte) at a time.
- Simple API
	- int getchar(void)
		- reads a character from STDIN
		- returns the character just read in
	- int putchar(int)
		- write the character received as argument on STDOUT
		- returns the character that was just written out
	- both assume the existence of two "default" Streams
		- STDIN; Standard Input (an integer, really)
		- STOUD; Standard Output (ditto)
- getc/putc
	- same idea as getchar/putchar, but you get to provide the stream
		- int fputc(int c, FILE* stream);
		- int putc(int c, FILE* stream);
	- all you need is an IO strream
		- which you open with fopen and close with fclose

- Streams
- Simple API
	- fp = FILE* fopen("file.txt", "mode");
	- ![[Screen Shot 2021-09-30 at 10.08.36 PM.png]]
	- fclose(fp);
		- int fclose(FILE \*stream);
			- returns 0 if it worked, EOF if there was a problem
![[Screen Shot 2021-09-30 at 10.09.25 PM.png]]
- rewinding/seeking
	- every open file maintains a seek pointer
	- the position into the file from the beginning
	- reading/writing modifies/advances the seek pointer
	- can move it arbitrarily

$\\$

math.h - use "-lm" when compiling

$\\$

# Makefile
![[Screen Shot 2021-09-30 at 10.12.58 PM.png]]

$\\$

# AVL Rotations
- AVL - self-balancing binary search tree
- Four kinds of rotations to balance itself:
	- Left rotation
	- Right rotation
	- Left-Right rotation
	- Right-Left rotation
- Left rotation:
	- If a tree becomes unbalanced when a node is inserted into the right subtree of the right subtree, then we perform a single left rotation
	- ![[Screen Shot 2021-10-01 at 9.20.51 AM.png]]
- Right rotation
	- Unbalanced - left subtree of the left subtree.
	- ![[Screen Shot 2021-10-01 at 9.21.37 AM.png]]
- Left-Right rotation:
	- Node inserted into the right subtree of the left subtree.![[Screen Shot 2021-10-01 at 9.22.51 AM.png]]
	- 
	- First perform left rotation on the left subtree of C.
	- ![[Screen Shot 2021-10-01 at 9.22.43 AM.png]]
	- Still unbalanced
	- ![[Screen Shot 2021-10-01 at 9.23.04 AM.png]]
	- Right rotate the tree.
	- ![[Screen Shot 2021-10-01 at 9.23.09 AM.png]]
	- ![[Screen Shot 2021-10-01 at 9.23.17 AM.png]]
- Right-Left - same as left-right, inverted.


# Tree list rep.
![[Screen Shot 2021-10-01 at 9.31.52 AM.png]]
- If 1-indexed:
- Parent of A\[i\] = A\[floor(i/2)\]
- Left child of A\[i\] = 2i
- Right child: 2i+1
