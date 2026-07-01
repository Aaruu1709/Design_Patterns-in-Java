Structural Design Patterns focus on how classes and objects are connected and organized to form larger and flexible structures.

# Adapter Design Pattern - Interview Notes

## What is Adapter Pattern?

> Adapter Pattern is a structural design pattern that allows two incompatible interfaces to work together by acting as a bridge between them.

---

## Why Do We Use It?

> We use Adapter Pattern when we want to integrate an existing class or a third-party library with our application, but their interfaces are different. Instead of modifying the existing code, we create an adapter class that converts one interface into another.

---

## What Problem Does It Solve?

> Adapter Pattern solves the problem of incompatible interfaces. It helps old and new systems work together without changing their existing implementations, which improves code reusability and reduces tight coupling.

---

## Real Project Example

> In real projects, Adapter Pattern is commonly used while integrating third-party payment gateways, external APIs, legacy systems, or external libraries. The adapter converts the third-party methods into the format expected by our application.

---

## 30-Second Interview Answer

> I have used Adapter Pattern to connect incompatible interfaces without modifying existing code. It acts as a bridge between two classes that cannot work together directly. This pattern is especially useful when integrating third-party APIs or legacy systems into an application. It improves reusability and keeps the code loosely coupled.

---

## Cross Questions

### 1. What is Adapter Pattern?

> Adapter Pattern allows two incompatible interfaces to work together by converting one interface into another.

---

### 2. What problem does it solve?

> It solves the problem of incompatible interfaces and helps reuse existing code without modification.

---

### 3. Where is it used in real projects?

> It is used in third-party API integrations, payment gateway integrations, legacy system migrations, and external library integrations.

---

### 4. What is the difference between Adapter and Facade Pattern?

> Adapter Pattern makes incompatible classes work together, whereas Facade Pattern provides a simple interface to a complex system.

---

## One-Line Summary

> Adapter Pattern = Convert one interface into another so that incompatible classes can work together.



# Adapter Pattern - Practical Example (Interview Answer)

## Example: Payment Gateway Integration

> Suppose my application has a standard interface called `PaymentService` with a method `processPayment()`.
>
> Later, we integrate a third-party payment provider like Razorpay, but it provides a different method called `makePayment()`.
>
> Since both interfaces are different, we create a `RazorpayAdapter` class that implements our `PaymentService` interface and internally calls `RazorpayClient.makePayment()`.
>
> This way, our application continues to use `processPayment()` without knowing the implementation details of Razorpay.
>
> The Adapter acts as a bridge between our application and the third-party library.

---

## Simple Flow

```text
Application
     ↓
PaymentService (Expected Interface)
     ↓
RazorpayAdapter
     ↓
RazorpayClient (Third-Party Library)
     ↓
makePayment()
```

---

## 30-Second Interview Answer

> A practical example of Adapter Pattern is payment gateway integration. Suppose our application uses a `PaymentService` interface with a `processPayment()` method, but a third-party provider like Razorpay provides a `makePayment()` method. We create a `RazorpayAdapter` that converts `processPayment()` into `makePayment()`. This allows both systems to work together without modifying existing code.

---

## Other Real-World Examples

* Payment gateway integration (Razorpay, Stripe, PayPal)
* Third-party API integration
* Legacy system integration
* External library integration
* Different file formats like PDF, Excel, and CSV converters

---

## One-Line Summary

> Adapter Pattern acts as a translator between our application and an external system that has a different interface.
----------------------------------------------------------
---

# Decorator Design Pattern

## What is Decorator Pattern?

> Decorator Pattern is a structural design pattern that allows us to add new functionality to an object dynamically without modifying its existing code.

---

## Why Do We Use It?

> We use Decorator Pattern when we want to extend the behavior of an object without changing the original class. It follows the Open-Closed Principle because we can add new features through decorators instead of modifying existing code.

---

## What Problem Does It Solve?

> Without Decorator Pattern, we may need to create many subclasses for different combinations of features, which makes the code difficult to maintain. Decorator Pattern solves this by adding features dynamically at runtime.

---

## Simple Real-Life Example

### Coffee Shop Example ☕

Base Coffee:

```text
Simple Coffee = ₹100
```

Add Milk:

```text
Simple Coffee + Milk = ₹120
```

Add Sugar:

```text
Simple Coffee + Milk + Sugar = ₹130
```

We keep adding features without changing the original `SimpleCoffee` class.

This is exactly how the Decorator Pattern works.

---

## Real Project Example

> A practical example is notification systems.

Suppose we have:

```java
NotificationService.send()
```

Initially, it sends only emails.

Later, business requirements change:

* Send Email
* Send SMS
* Send WhatsApp notification

Instead of modifying the existing `EmailNotificationService`, we can add decorators like:

```text
EmailNotification
      ↓
SMSDecorator
      ↓
WhatsAppDecorator
```

Each decorator adds new functionality while keeping the original class unchanged.

---

## 30-Second Interview Answer

> Decorator Pattern is a structural design pattern used to add new functionality to an object dynamically without modifying its existing code. It helps us follow the Open-Closed Principle and avoids creating too many subclasses. In real projects, it can be used in notification systems, where we add SMS or WhatsApp notifications on top of existing email notifications.

---

## Cross Questions

### 1. What is Decorator Pattern?

> Decorator Pattern adds new functionality to an object without changing its original implementation.

---

### 2. What problem does it solve?

> It avoids subclass explosion and allows features to be added dynamically at runtime.

---

### 3. Which SOLID principle does it follow?

> It follows the Open-Closed Principle (OCP) because existing classes remain unchanged while new functionality is added through decorators.

---

### 4. Where is it used in real projects?

> It is commonly used in notification systems, logging frameworks, security filters, and Java I/O streams.

---

### 5. Give a practical example.

> A notification system where Email notifications can be extended with SMS and WhatsApp notifications without modifying the original EmailNotification class.

---
The goal of Decorator Pattern is not to reduce one line of code.

The goal is to:

✅ Add new features without modifying existing classes.

✅ Follow the Open-Closed Principle (OCP).

✅ Avoid creating too many subclasses.
## One-Line Summary

> Decorator Pattern = Add new features to an object without changing its existing code.


----------------------------------------
# Facade Design Pattern

## What is Facade Pattern?

> Facade Pattern is a structural design pattern that provides a simple interface to a complex system by hiding its internal details.

---

## Why Do We Use It?

> We use Facade Pattern to reduce complexity for the client. Instead of interacting with multiple classes, the client communicates with a single facade class, which internally coordinates everything.

---

## What Problem Does It Solve?

> Without Facade Pattern, the client needs to know and interact with many different classes. This increases coupling and makes the code difficult to understand and maintain. Facade Pattern hides this complexity behind a single entry point.

---

## Simple Real-Life Example

### Online Food Order 🍕

When we place an order on a food app, we click only one button:

```text
Place Order
```

But internally, many things happen:

```text
Restaurant Service
Payment Service
Delivery Service
Notification Service
```

The user does not interact with each service separately.

The app provides a single interface called:

```text
OrderFacade.placeOrder()
```

This is the Facade Pattern.

---

## Real Project Example

> In a Spring Boot application, suppose we have an Order module.

To place an order, we need to call:

* PaymentService
* InventoryService
* NotificationService
* ShippingService

Instead of calling all these services from the controller, we create an `OrderFacadeService`.

```java
orderFacadeService.placeOrder(orderRequest);
```

The facade internally coordinates all the required services.

This keeps the controller simple and reduces coupling.

---

## 30-Second Interview Answer

> Facade Pattern is a structural design pattern that provides a simple interface to a complex subsystem. It hides internal implementation details and reduces coupling between the client and multiple services. In real projects, I have seen similar approaches where a facade service coordinates payment, inventory, and notification operations through a single method call.

---

## Cross Questions

### 1. What is Facade Pattern?

> Facade Pattern provides a single, simplified interface to a complex system.

---

### 2. What problem does it solve?

> It reduces complexity and hides the interactions between multiple classes from the client.

---

### 3. Where is it used in real projects?

> It is commonly used in service orchestration, order processing, payment workflows, and integration layers.

---

### 4. What is the difference between Adapter and Facade?

> Adapter Pattern makes incompatible interfaces work together, whereas Facade Pattern simplifies a complex system by providing a single entry point.

---

### 5. Give a practical example.

> An OrderFacade that internally calls PaymentService, InventoryService, ShippingService, and NotificationService to complete an order.

---

## One-Line Summary

> Facade Pattern = One simple interface that hides a complex system behind it.
--------------------------------------------------

# Proxy Design Pattern - Interview Notes

## What is Proxy Pattern?

> Proxy Pattern is a structural design pattern that provides a placeholder or representative object to control access to another object.

---

## Why Do We Use It?

> We use Proxy Pattern when we want to add extra functionality like security, logging, caching, lazy loading, or access control before calling the actual object.

---

## What Problem Does It Solve?

> Without Proxy Pattern, the client directly accesses the real object, and all additional logic such as authentication, authorization, logging, or caching gets mixed into the business code. Proxy Pattern separates these concerns and controls access to the real object.

---

## Simple Real-Life Example

### ATM Machine 🏧

When you withdraw money:

```text
You
 ↓
ATM Machine (Proxy)
 ↓
Bank Server (Real Object)
```

The ATM first:

* Checks your PIN
* Verifies your account
* Checks your balance

Only then does it allow access to the bank server.

The ATM acts as a **Proxy**.

---

## Real Project Example

> Suppose we have an `EmployeeService` that returns employee details.

Before allowing access, we want to:

* Check user roles
* Log the request
* Cache frequently used data

Instead of adding this logic to `EmployeeService`, we create an `EmployeeServiceProxy`.

```java
employeeServiceProxy.getEmployee(101);
```

The proxy performs validation and then calls the actual service.

---

## Spring Boot Example

> Spring AOP works similarly to the Proxy Pattern.

For example:

```java
@Transactional
public void saveEmployee() {
    // business logic
}
```

Spring creates a proxy object around this method.

The proxy:

* Starts the transaction
* Executes the business method
* Commits or rolls back the transaction

The actual business code remains clean.

---

## 30-Second Interview Answer

> Proxy Pattern is a structural design pattern that controls access to another object by introducing a proxy or intermediate object. It is commonly used for security, logging, caching, and lazy loading. In Spring Boot, features like `@Transactional` and Spring AOP internally use proxy mechanisms to add functionality without modifying business code.

---

## Cross Questions

### 1. What is Proxy Pattern?

> Proxy Pattern provides a placeholder object that controls access to the real object.

---

### 2. What problem does it solve?

> It separates concerns like security, logging, caching, and lazy loading from the core business logic.

---

### 3. Where is it used in real projects?

> It is used in Spring AOP, transactions, security, caching, remote service calls, and lazy loading.

---

### 4. Give a practical example.

> An `EmployeeServiceProxy` that performs authorization and logging before calling the actual `EmployeeService`.

---

### 5. What is the difference between Proxy and Decorator?

| Proxy Pattern                         | Decorator Pattern                             |
| ------------------------------------- | --------------------------------------------- |
| Controls access to an object          | Adds new functionality to an object           |
| Focuses on security, caching, logging | Focuses on extending behavior                 |
| Example: Spring AOP, `@Transactional` | Example: Email + SMS + WhatsApp notifications |

---

## One-Line Summary

> Proxy Pattern = Control access to an object by placing another object in front of it.

