## References and Arguments
~~~
void sumOf (string a, int& ttl);

int main() {
...
int s;
sumOf(x,s);
}
~~~
* When I'm making the 'sumOf(x,s)' function call, I'm assigning that reference to an int with an alias to s.
* Basically when I'm making that call, the argument ttl is an alias for s

#### Getting rid of ttl arg
~~~
int sumOf(string a) {
	int ttl = 0;
	...
	return ttl
}
int main() {
	...
	int s = sumOf(x);
	...
}
~~~

#### Better solution, but string can now be changed
~~~
int sumOf(string& a) {
	int ttl = 0;
	...
	return ttl
}
int main() {
	...
	int s = sumOf(x);
	...
}
~~~
* The 'string a' -> 'string& a' arg change says "when you call sumOf, if you're passing a string, let's make a be an alias to that string (a reference to it) so that we don't have to copy the string".
* HOWEVER – the original string can be modified.

#### Const reference
~~~
int sumOf(const string& a) {
	int ttl = 0;
	...
	return ttl
}
int main() {
	...
	int s = sumOf(x);
	...
}
~~~
* Only change: 'string& a' -> 'const string& a'. Now a is a reference to a consant string.