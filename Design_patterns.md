# Design_Patterns-in-Java
```
Design patterns are reusable and proven solutions to common software design problems. They help us write loosely coupled, maintainable, and scalable applications
design pattern are not ready made code , it is template or guidline which help us to solve similar problems
we don't create a new blueprint every time. we can use a predefined design that has already worked many times.

Similarly, in software development:
Many developers face the same problems.
Experienced developers created standard solutions.
Those standard solutions are called Design Patterns.

What Problems Do They Solve?

Without design patterns:

Code becomes tightly coupled.
Code duplication increases.
Maintenance becomes difficult.
Adding new features is harder.

With design patterns:

Code is reusable.
Components are loosely coupled.
Maintenance becomes easier.
New features can be added with minimal changes.

Design patterns are mainly divided into Creational, Structural, and Behavioral patterns

Types of Design Patterns

There are 3 categories:

Type	Purpose
Creational	How objects are created
Structural	How classes and objects are organized
Behavioral	How objects communicate with each other

```

```
Creational Patterns
Singleton
Factory
Abstract Factory
Builder
Prototype

Purpose: Object creation.

Structural Patterns
Adapter
Decorator
Facade
Proxy
Composite
Bridge
Flyweight

Purpose: Class and object structure.

Behavioral Patterns
Strategy
Observer
Template Method
Command
State
Iterator
Chain of Responsibility
Mediator
Visitor
Memento

Purpose: Communication and behavior between objects.
```

```
📌creational design pattern:
-this pattern mainly focused on object creation mechanism
--------------------------------------------------
| Pattern                  | Purpose                                           |
| ------------------------ | ------------------------------------------------- |
| Singleton Pattern        | Creates only one object in the entire application |
| Factory Pattern          | Creates objects without exposing creation logic   |
| Abstract Factory Pattern | Creates families of related objects               |
| Builder Pattern          | Builds complex objects step by step               |
| Prototype Pattern        | Creates new objects by cloning existing ones      |
```

```
📌 Structural Design Patterns:
-this pattern are focus on how classes and object are organized and related to eachother
| Pattern           | Purpose                                                                    |
| ----------------- | -------------------------------------------------------------------------- |
| Adapter Pattern   | Connects incompatible classes so they can work together                    |
| Decorator Pattern | Adds new features to an object without changing its code                   |
| Facade Pattern    | Provides a simple interface to a complex system                            |
| Proxy Pattern     | Controls access to another object                                          |
| Composite Pattern | Treats individual objects and groups of objects in the same way            |
| Bridge Pattern    | Separates abstraction from implementation so both can change independently |
| Flyweight Pattern | Shares objects to reduce memory usage                                      |
```


```
📌 Behavioral Design Patterns
-this pattern focus on communication and responsibitlity between object

| Pattern                         | Purpose                                                                         |
| ------------------------------- | ------------------------------------------------------------------------------- |
| Strategy Pattern                | Changes an algorithm at runtime without modifying the client code               |
| Observer Pattern                | Notifies multiple objects when one object changes                               |
| Template Method Pattern         | Defines the steps of an algorithm but allows subclasses to customize some steps |
| Command Pattern                 | Encapsulates a request as an object                                             |
| State Pattern                   | Changes an object's behavior based on its current state                         |
| Iterator Pattern                | Traverses elements of a collection one by one                                   |
| Chain of Responsibility Pattern | Passes a request through multiple handlers until one handles it                 |
| Mediator Pattern                | Manages communication between multiple objects                                  |
| Visitor Pattern                 | Adds new operations to objects without changing their classes                   |
| Memento Pattern                 | Saves and restores an object's previous state                                   |
```
-------------------------------------------------------------

```
### difference bet design pattern and solid principles:
SOLID Principles:"What rules should I follow to write clean and maintainable code?
For example:

SRP → One class, one responsibility.
OCP → Open for extension, closed for modification.
DIP → Depend on interfaces, not implementations.

So, SOLID is a set of design guidelines.

Design Patterns:"How can I solve this problem using a standard solution?"
For example:

Need only one object? → Use Singleton.
Need different algorithms? → Use Strategy.
Need to create objects dynamically? → Use Factory.

So, Design Patterns are ready-made solutions.
```
