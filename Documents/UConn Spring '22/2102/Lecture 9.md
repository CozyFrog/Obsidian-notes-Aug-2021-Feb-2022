## Q1
* The process of finding objects in the problem domain is called:
	* Object-oriented analysis
		* NOT object-design or object-oriented analysis & design.

Identifying the modules and the dependencies.
Overall, the analysis answers the WHAT and the design answers the HOW.
OO design - identify the concepts and the physical entities in the design phase, classes/functions that will model the physical entities.

## Q2
* A class in a UML class diagram consists of which of the following compartments:
	* All of:
		* Name
		* Attributes
		* Operations

## Q3
* Consider the following UML class diagram (shape class, arrow from triangle, arrow from square). What relationship is represented?
	* Realization
	* Inheritance (X)
	* Aggregation
	* Dependency

Usually dependency is not represented on diagram - only something that exists in solution.

## Q4
* The composition relationship is:
	* A weaker version of aggregation
	* A stronger version of aggregation (X)
	* Where a child class can exist without the parent
	* Where a child class cannot exist without the parent (X)

Aggregation is part of relationship. E.g. student is part of a class - if I delet the class, the student still exists in the peoplesoft system. Composition is an entirely made up relationship - whenever a child/parent class share a comp. relationship, if the parent is deleted so too must the student.
Parent class house - child class rooms. If you delete the parent class (house) the rooms will not exist.

## Q5
* Dependence relationship in the UML diagram is:
	* 

It is a relationship that exists b/w the classes only in the solution/implementation domain. Never a permanent part of the state. Dependence on a random number - you don't store the random number somewhere, that defeats the purpose.

## Q6
* Line means association b/w classes, in runtime how many objects of type X are associated with each other.
	* \*2
	* Classes B and C are child classes of class A are siblings of each other. Whatever relationship A has with D, because B and C are children of A, that relationship flows down to B and C. Will have the same relationship with D as A does with D.
	* One object of B must be associated with exactly two objects of D.
	* One object of D may be associated with multiple objects of C.

## Q7
* Visitor 1..\*     1..\* Fair
	* one dot dot star means one or more, so a fair is visited by at least one fair and one visitor visits at least one fair.
	* just a star means zero or more




# Example Problem
First class we might have is an inventory or system.