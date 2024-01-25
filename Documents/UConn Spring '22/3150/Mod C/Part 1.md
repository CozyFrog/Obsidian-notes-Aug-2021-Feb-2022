## Heap Allocation
* 'new' operator: receives as an argument a type, and what it does is it returns the address of a memory cell where I can story a value of that type.
* Example:
	~~~
	using namespace std;
	int* px = new int;
	...
	delete px;
	~~~

* allocating an array on the heap
* ``` new <type>[<expression>] ``` – expression can be calculated at runtime!
~~~
int* px = new int[10]; // 
*px = 20; // first element of array is now 20
...
delete[] px;
~~~
~~~
int* px = new int[10];
for (int i = 0; i < 10; i++)
	px[i] = i; // behaves intuitively
...
delete[] px;
~~~
