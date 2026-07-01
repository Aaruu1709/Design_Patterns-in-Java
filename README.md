# Behavioral Design Patterns

## What are Behavioral Design Patterns?

Behavioral Design Patterns focus on how objects communicate and interact with each other.

They define how responsibilities are shared between objects and how different objects work together to perform a task.

---

## Interview Definition

> Behavioral Design Patterns deal with communication and interaction between objects. They help make the system flexible, maintainable, and loosely coupled.

---

## Why Do We Use Behavioral Patterns?

We use Behavioral Patterns to:

* Reduce tight coupling between objects.
* Make communication between objects more flexible.
* Easily change behavior at runtime.
* Improve maintainability and scalability.
* Follow SOLID principles.

---

## Difference Between Design Pattern Categories

| Category            | Purpose                            |
| ------------------- | ---------------------------------- |
| Creational Patterns | How objects are created            |
| Structural Patterns | How objects are connected          |
| Behavioral Patterns | How objects communicate and behave |

---

## Types of Behavioral Design Patterns

| Pattern                         | Purpose                                                     |
| ------------------------------- | ----------------------------------------------------------- |
| Strategy Pattern                | Changes algorithms at runtime without modifying client code |
| Observer Pattern                | Notifies multiple objects when one object changes           |
| Template Method Pattern         | Defines the steps of an algorithm and allows customization  |
| Command Pattern                 | Encapsulates a request as an object                         |
| State Pattern                   | Changes object behavior based on its current state          |
| Iterator Pattern                | Traverses collection elements one by one                    |
| Chain of Responsibility Pattern | Passes a request through multiple handlers                  |
| Mediator Pattern                | Centralizes communication between objects                   |
| Visitor Pattern                 | Adds new operations without changing existing classes       |
| Memento Pattern                 | Saves and restores an object's previous state               |

---

### 1. Strategy Pattern ⭐

* Most important behavioral pattern
* Frequently asked in interviews
* Common in payment and discount systems

### 2. Observer Pattern ⭐

* Used in event-driven systems
* Spring events are based on this concept

### 3. Template Method Pattern ⭐

* Common in framework development
* Defines a fixed workflow with customizable steps

### 4. Chain of Responsibility Pattern ⭐

* Used in filters, authentication, and request processing

---

## One-Line Summary

> Behavioral Design Patterns define how objects communicate and work together while keeping the system flexible and loosely coupled.
--------------------------------------------
# Strategy Pattern - Interview Ready Notes

## What is Strategy Pattern?

> Strategy Pattern is a behavioral design pattern that allows us to choose or change an algorithm at runtime without modifying the client code.

---

## Why Do We Use It?

> We use Strategy Pattern when we have multiple ways to perform the same task. It helps us avoid large if-else or switch statements and makes the code easy to maintain and extend.

---

## What Problem Does It Solve?

> It solves the problem of multiple if-else conditions by moving each algorithm into a separate class and selecting the required implementation at runtime.

---

## Real Project Example

> A common example is a payment system. We may have different payment methods like UPI, Credit Card, and Net Banking. Each payment method is implemented as a separate strategy class, and the user can choose the required payment method at runtime.

---

## 30-Second Interview Answer

> I have used the Strategy Pattern when there are multiple ways to perform the same operation. It allows us to change algorithms at runtime without modifying existing code. For example, in a payment system, different payment methods such as UPI, Card, and Net Banking can be implemented as separate strategies. This helps avoid large if-else statements and follows the Open-Closed Principle.

---

## Cross Questions

### What is Strategy Pattern?

> It allows us to choose different algorithms at runtime without changing the client code.

---

### What problem does it solve?

> It removes large if-else or switch statements and makes the code more maintainable.

---

### Which SOLID principle does it follow?

> It follows the Open-Closed Principle because new strategies can be added without modifying existing code.

---

### Where is it used in real projects?

> It is used in payment systems, discount calculations, tax calculations, sorting algorithms, and route planning applications.

---

### Give a practical example.

> A payment system where users can choose UPI, Card, or Net Banking, and each payment method is implemented as a separate strategy class.

---

## One-Line Summary

> Strategy Pattern = Choose different algorithms at runtime without using multiple if-else statements.

---------------------------------------
# Observer Design Pattern

## What is Observer Pattern?

> Observer Pattern is a behavioral design pattern where one object (Subject) maintains a list of dependents (Observers) and notifies them automatically whenever its state changes.

---

## Why Do We Use It?

> We use Observer Pattern when multiple objects need to be updated automatically when one object changes, without tightly coupling them.

---

## What Problem Does It Solve?

> Without Observer Pattern, the subject must manually call all dependent objects, which creates tight coupling and makes the system difficult to maintain. Observer Pattern solves this by allowing automatic notification to all registered observers.

---

## Real Project Example

> A common example is a notification system.

When a user places an order:

* Email service is notified
* SMS service is notified
* WhatsApp service is notified

All services get updated automatically when the order status changes.

---

## Another Real Example

> In Spring Boot, event handling works like Observer Pattern.

When an event is published:

* Multiple listeners receive the event automatically.

---

## 30-Second Interview Answer

> Observer Pattern is a behavioral design pattern where one object notifies multiple dependent objects automatically when its state changes. It helps achieve loose coupling between objects. In real projects, it is used in notification systems where Email, SMS, and WhatsApp services get triggered automatically when an event like order placement occurs. It is also used in Spring Boot event listeners.

---

## Cross Questions

### 1. What is Observer Pattern?

> It defines a one-to-many relationship where multiple objects are notified automatically when one object changes.

---

### 2. What problem does it solve?

> It removes tight coupling between objects and avoids manual notifications.

---

### 3. Where is it used in real projects?

> It is used in notification systems, event-driven architectures, stock price updates, and Spring Boot event listeners.

---

### 4. Give a practical example.

> Order service notifies Email, SMS, and WhatsApp services automatically when order status changes.

---

### 5. Which design principle does it follow?

> It follows the Open-Closed Principle because new observers can be added without changing the subject.

---

## One-Line Summary

> Observer Pattern = One object changes, and multiple dependent objects get automatically notified.


---------------------------------------------
# Template Method Design Pattern - Interview Ready Notes

## What is Template Method Pattern?

> Template Method Pattern is a behavioral design pattern that defines the skeleton of an algorithm in a base class and allows subclasses to override specific steps without changing the overall structure.

---

## Why Do We Use It?

> We use Template Method Pattern when multiple classes follow the same process flow but some steps can vary. It helps us avoid code duplication and keeps a fixed workflow.

---

## What Problem Does It Solve?

> Without Template Method Pattern, each class may implement the same workflow with duplicated code, leading to inconsistency and poor maintainability. This pattern defines a common structure in one place and allows customization of specific steps.

---

## Real Project Example

> A common example is a data processing system.

Different file types like:

* CSV file processing
* Excel file processing
* JSON file processing

All follow the same steps:

* Read data
* Process data
* Save data

But each file type has its own implementation for these steps.

---

## Another Real Example (Spring Boot)

> In Spring, frameworks like Spring Batch use this pattern.

The flow is fixed, but developers customize steps like processing logic.

---

## 30-Second Interview Answer

> Template Method Pattern is a behavioral design pattern where the base class defines the structure of an algorithm and subclasses implement specific steps. It helps avoid code duplication and ensures a fixed workflow. For example, in file processing systems, the steps like reading, processing, and saving remain the same, but each file type like CSV or Excel has its own implementation.

---

## Cross Questions

### 1. What is Template Method Pattern?

> It defines a fixed algorithm structure in a base class and allows subclasses to customize specific steps.

---

### 2. What problem does it solve?

> It removes code duplication and ensures a consistent workflow across multiple implementations.

---

### 3. Where is it used in real projects?

> It is used in file processing systems, Spring Batch, data pipelines, and report generation systems.

---

### 4. Give a practical example.

> CSV, Excel, and JSON file processing where all follow the same steps but implement them differently.

---

### 5. Which SOLID principle does it support?

> It supports the Open-Closed Principle because new implementations can be added without changing the base workflow.

---

## One-Line Summary

> Template Method Pattern = Define the skeleton of an algorithm in a base class and let subclasses implement specific steps.
