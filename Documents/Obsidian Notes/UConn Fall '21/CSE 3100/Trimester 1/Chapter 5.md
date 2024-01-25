Unary operator & gives the address of an object.
The statement $p=&c;$ assigns the address of c to the variable p; p *points to* c.
The & operator can only be applied to objects in memory: variables and array elements. It cannot be applied to expressions, constants, or register variables. 

Unary operator \* is the *indirection* or *deferencing* operation; when applied to a pointer, it accesses the object the pointer points to.

$\\$

Pointers and Arrays

The declaration a\[10\]; defines an array a of size 10, which is a block of 10 consecutive objects names a\[0\], a\[1\], ..., a\[9\].

The notation a\[i\] refers to the i-th element of the array. Let pa be a pointer to an integer ($int *pa;$).
Then the assignment $pa=&a[0];$ sets pa to point to element zero of a; that is, pa contains the address of a\[0\].

The assignment $x=*pa$ will copy the contents of (the value at) a\[0\] into x.

If pa points to a particular element of an array, pa+1 will point to the next element. Thus, if pa points to a\[0\], $*(pa+1)$ refers to the contents of a\[1\].

By definition, the value of a variable or expression of type array is the address of element zero of the array. Since the name of an array is a synonym for the location of the initial element, the assignment $pa=&a[0]$ is equal to $pa=a$.
Also, $a[i]$ can be written as $*(a+i)$.