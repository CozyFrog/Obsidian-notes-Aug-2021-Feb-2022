### Vector
* vector\<T\>
* It provides
	* a sequence
	* dynamically sized
	* ability to add / remove anywhere
	* random access
	* bounds safety
* like C arrays with extra safety

#### Example:
~~~
vector<int> vec;
for (int i = 0; i < 10; i++) vec.push_back(i);

for (int v : vec) cout << v << " ";
cout << endl;
~~~

### Template
~~~
template <class T>
~~~
* is the way to say "whatever declaration follows is generic and it's parameterized by T. T happens to be any kind of type. (We say "class T" for historical reasons).
~~~
template <class T>
T sum(vector<T>& vec) {
	int ttl = 0;
	for(T v : vec) ttl = ttl + v;
	return ttl;
}
~~~

### Example with Strings
~~~
vector<string> vs;
vs.push_back(string("Hello "));
vs.push_back(string("cruel "));
vs.push_back(string("world "));

cout << "sentence:" << sum(vs) << endl;
// "sentence:Hello cruel world"

~~~