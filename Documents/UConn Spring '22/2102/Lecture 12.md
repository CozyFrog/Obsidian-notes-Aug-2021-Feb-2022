## Q1: Pick the term that relates to polymorphism:
* Dynamic binding
	* Inherits method from parent class, but provides different implementation based on type at runtime (parent or child implementation).
* Method overriding, method overloading

## Q2: Two or more methods with the same name in the same class with different arguments is called:
* Method overloading.
* Constructor of an object is a commonly overloaded method.
	* Example: one constructor w/ all values provided by user.

## Q3: When a sub class decares a method that has the same type arguments as a method declared by one of its superclasses, it is termed as:
* Method overriding.

### Operator overloading
* Occurs when you take basic operators (+,-,...) and redefine them into something else.

## Q5: What type of relationship exists between someMeth in class A and someMeth in class B?
* Neither method overriding nor method overloading.
* Class B is a child of class A.
~~~
class A {
	private void someMeth() {
		// do some stuff
	}
}

class B {
	private void someMeth(int x) {
		// do some stuff with x
	}
}
~~~

# Q6:
* Person (parent)
	* Student (child of person)
		* Undergraduate (child of student)

~~~
Person p = new Person();
Student s = new Student();
Undergraduate u = new Undergraduate();

p = ug;
p = new undergraduate;
ug = new student();
ug = p;
ug = new Student();
~~~

Because student is a child of person, p = s is legit but s = p is not.
* Undergrad can access all methods and variables from student.
* Student can access variables from person, but not ug.
* Person cannot access variables from student or ug.

* p = ug is legit
* p = new undergraduate() is legit
* ug = new student() is not legit
* ug = p is not legit
* ug = new student() is not legit.

<mark>right hand side should be able to access methods/variables of left hand side</mark>

* is s = new Person legit? no.
* is p = new Student legit? yes.


## Does Java support user-defined operator overloading?
* No.
## Which operators are overloaded for Java string objects?
* operator is overloaded for strings objects
* '+' defines concatenation of string operands.