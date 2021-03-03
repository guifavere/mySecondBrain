# Dive into design patterns

## Types of relation between  objects

### Inheritance
A object extends another object. The child object must implement all the abstract methods from parent.
You can use it when you need reusing all methods from a parent class, and just an additional method.

### Polymorphism
The application identify, and call the implementation class for a specific interface.

###  Dependency
There is dependency between classes, when changes in a class can result in changes in another class. You must avoid declare classes that depend of concrete class, inside that, depend of interface or abstract class.

### Association
You can use it, when you need to represent an entity in some class, like an attribute.

### Aggregation
It's used to represent individual relations, like: one to many, many to many and whole part.

### Composition
This relation is a specific type of the relation: aggregation. The difference is the component just only can exist as a part of a container.

## Types of design patterns

### Creational
They are patterns that improve flexibility, and reuse of code for creating objects.

### Structural
They define how build objects in bigger structures, also keep them flexible and efficient.

### Behavioral
They are patterns that are responsible by an efficient communication, and definition of responsibilities between objects.