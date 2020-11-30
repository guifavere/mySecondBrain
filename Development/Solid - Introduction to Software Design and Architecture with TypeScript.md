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

## Building a real-world DDD app
**Domain model:** A domain model is a declarative layer of code (without dependencies to any upper-layer concerns) that encapsulates the business rules of a particular problem domain.

**Ubiquitous language:** The Ubiquitous Language (which is a fancy DDD term for the common language that best describes the domain model concepts) is learned through conversation with domain experts.

**Anemic model:** When the classes that describe the model and the classes that perform operations on the model are separate. The services contain all the domain logic while the the domain objects themselves contain practically none.

**Transaction script:** The simplest way to organize domain logic as possible. By using simple if and else control statements, we can express domain logic easily. This is perfect for simple applications without a huge amount of domain logic that can do without a lot of time spent on architecture.

**Entities:** Domain objects that we care to uniquely identify.

**Value objects:** Value objects have no identity. They are attributes of Entities.

**Aggregates:** An aggregate is a collection of entities bound together by an aggregate root. The aggregate root is the thing that we refer to for lookups. No members from within the aggregate boundary can be referred to directly from anything external to the aggregate. This is how the aggregate maintains consistency.

**Domain services:** This is where we locate domain logic that doesn't belong to any one object conceptually.

**Repositories:** We use repositories in order to retrieve domain objects from persistence technologies. Using software design principles like the Liskov Substitution Principle and layered architecture, we can design this in a way so that we can easily make architecture decisions to switch between an in-memory repository for testing, a MySQL implementation for today, and a MongoDB based implementation 2 years from now.

**Factories:** We'll want to create domain objects in many different ways. We map to domain objects using a factory that operates on raw SQL rows, raw json, or the Active Record that's returned from your ORM.

**Domain events:** Domain events are simply objects that define some sort of event that occurs in the domain that domain experts care about.

The two most important architectural concepts to grasp in Domain-Driven Design are subdomains and bounded contexts. Subdomains are about creating logical boundaries and bounded contexts are about creating physical ones.

**Subdomains:** A Subdomain is a smaller piece (logical boundary) within the entire problem space.

**Bounded contexts:** A Bounded Context is a logical boundary around all of the subdomains needed in order for an application to achieve its goals.