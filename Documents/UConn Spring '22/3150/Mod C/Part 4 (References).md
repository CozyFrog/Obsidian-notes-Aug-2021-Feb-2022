## What is it?
* Serves same purpose as pointers, with advantages:
	* Cleaner syntax
	* Stricter semantics
* But you can't do arithmetic like with pointers (basically an alias)
* '&' means reference

## Examples
#### Example 1:
~~~
int x = 10;
int &y = x; (y is a reference to to an int)
// x = 10
// y = 10
y = 20; (write to y as if you're writing right to x)
		(refers to the memory that x refers to)
// x = 20
// y = 20
// &x = 0x7fff...
// &y = 0x7fff...
~~~
* Need to initialize references on the spot 
* Cannot reassign references later 
* When you declare it, you must initialize it

#### Example 2
~~~
int x = 10;
const int &y = x; 
// x = 10
// y = 10
x = 20;
// x = 20
// y = 20
// &x = 0x7fff...
// &y = 0x7fff...
~~~
* y is a reference to an int that happens to be constant even though x is not const. This means that y can only be used to read from x
#### Example 3
~~~
int x = 10;
const int &y = x; 
// x = 10
// y = 10
y = 20;
~~~
* error: read-only variable is not assignable.