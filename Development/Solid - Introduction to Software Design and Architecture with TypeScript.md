# The World of Software Design and Architecture

## Software design and architecture
1. The goals of software are to:
	1. Goal #1: Satisfy the users' needs while minimizing the effort it takes to do so.
	2. Goal #2: Consistently accomplish Goal #1 as the requirements change.
2. Architecture is about identifying the system quality attributes that will stack our odds of successfully performing Goal #1, and our choice of architectural pattern that will best accommodate the project.
3. Software design isn't much different from architecture besides the fact that they have different levels of design that they appear at.

##  Clean code
###  Design choices to write **clean code**:
1. being consistent.
2. Preferring meaningful variable, method and class names over writing comments
ensuring code is indented and spaced properly.
3. Ensuring all of the tests can run.
4. Writing pure functions with no side effects.
5. Not passing null.

### Examples of common design principles:
1. Composition over inheritance.
2. Encapsulate what varies.
3. Program against abstractions, not concretions.
4. The Hollywood principle: "Don't call us, we'll call you.".
5. The SOLID principles, especially the Single responsibility principle.
6. DRY (Do Not Repeat Yourself).
7. YAGNI (You Aren't Gonna Need It).

### There are 3 categories of design patterns: creational, structural, and behavioral
1. Creational Design Patterns: patterns that control how objects are created.
2. Structural Design Patterns: patterns that simplify how we define relationships between components.
3. Behavioral Design Patterns: patterns for facilitating elegant communication between objects.

### Architectural styles are just design patterns at the high-level. They are:
1. Structural: Component-based, Monolithic and Layered.
2. Messaging: Event-Driven and Publish-Subscribe.
3. Distributed: Client-Server and Peer-to-peer.

### Signifiers in software development
There are two ways to recognize a design pattern. The first way is to see the code, the structure, and the second way is to see the pattern name in the actual name of the class, or function, like: **StudentController**.

### Optimizing code
1. Optimizing code for humans means making it easier to read and understand.
2. Optimizing code for computers means making it more efficient.

Often, optimizing code for computers means making it less readable and understandable for humans. This is a tough balance to accomplish, but that's recommended optimizing for humans > computers.

## Design principles
### Dependency Inversion Principle (DIP)
**Source code dependency:** When the current component (class, module, etc) relies on at least one other component in order to be compiled. Source code dependencies should be limited.