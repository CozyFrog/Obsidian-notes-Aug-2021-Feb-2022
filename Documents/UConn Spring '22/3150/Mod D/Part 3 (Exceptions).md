### Raising
* Quite simple
	* A statement
	* With an expression argument
	* Value of expression is what is "thrown"
~~~
throw <expr>
~~~

### Semantics
* Normal control-flow path is altered - flow is transferred to catch site.
* If there is no catch-site in this function, retun to the callee and handle it there.
* If we reach main and still no catch site the OS kills the program.

### Handling
* Define a catch site for a piece of code
~~~
try {
	<block_0>
} catch(<decl_1>) {
	<block_1>
} catch(<decl_2>) {
	<block_2>
}
~~~