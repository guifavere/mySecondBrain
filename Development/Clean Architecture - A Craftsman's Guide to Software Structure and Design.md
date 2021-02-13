# Clean architecture

## Paradigms

### Procedure programming
Discipline imposed upon direct transfer of control

### Object-oriented programming
Discipline imposed upon indirect transfer of control

### Functional programming
Discipline imposed upon assignment

1. The business rules must be at core of the architecture.
2. The architecture must be independent of frameworks, databases and GUI's.
3. The architecture must be testable.

## About the layer

###  Entities
This layer keeps the business rules that are independent of the application.

### Use cases
This layer keeps the operations, business rules that are dependents of the application.

### Interface adapters (controllers, gateways and presenters)
This layer transform the data to be accessible between the layers: entities, and use cases.

### Frameworks and drivers
This is the external layer, it keeps the technologies that are used.

The communication between the layers are made using interfaces. And internal layers can't depend resources of layer above.