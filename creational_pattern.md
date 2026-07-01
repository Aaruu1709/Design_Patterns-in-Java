singlton
factory
builder
Abstract Factory Pattern
Prototype Pattern
### 1️⃣ Singleton Design Pattern
```
Singleton Pattern ensures that only one object of a class is created in the entire application
We use Singleton when we need only one instance throughout the application.

Examples:

Logger
Cache Manager
Configuration Manager
Database Connection Pool
Spring Beans (@Service, @Repository, @Component) by default

How to Create a Singleton Class?
1. Make Constructor Private
2. Create a Static Object
3. Provide a Public Method

example 2:
   @Service
public class EmployeeService {

}

Spring creates only one EmployeeService object.

Multiple controllers use the same instance
This saves memory and maintains consistency.
```
```
2️⃣ Factory Design Pattern
"Factory Pattern creates objects without exposing the object creation logic to the client.
The client asks the factory for an object instead of using the new keyword directly."

Why Do We Use It?

We use Factory Pattern when:

We have multiple implementations of an interface.
The object to create depends on some condition.
We want to reduce tight coupling.
We use it to reduce tight coupling and centralize object creation logic.
It removes multiple if-else conditions from client code and makes adding new implementations easier.
The object creation responsibility moves from the client to the factory.

| Singleton               | Factory                            |
| ----------------------- | ---------------------------------- |
| Creates only one object | Creates different types of objects |
| Focuses on object count | Focuses on object creation logic   |
| Example: Logger         | Example: PaymentService            |

```

# Factory Design Pattern

## What is Factory Pattern?

Factory Pattern creates objects without exposing the object creation logic to the client.

Instead of creating objects using the `new` keyword, the client asks the factory to create and return the required object.

---

## Why Do We Use It?

* Reduces tight coupling
* Centralizes object creation logic
* Makes code easy to maintain
* Easy to add new implementations
* Follows the Open-Closed Principle (OCP)

---

## Problem Without Factory Pattern

### Main.java

```java
public class Main {

    public static void main(String[] args) {

        String paymentType = "UPI";

        Payment payment = null;

        if (paymentType.equalsIgnoreCase("UPI")) {

            payment = new UpiPayment();

        } else if (paymentType.equalsIgnoreCase("CARD")) {

            payment = new CardPayment();

        }

        payment.pay(1000);
    }
}
```

### Problems

* Client knows all implementation classes.
* Multiple if-else conditions increase.
* Difficult to maintain and extend.
* Tight coupling between client and concrete classes.

---

# Factory Pattern Example

## Project Structure

```text
src
│
├── Payment.java
├── UpiPayment.java
├── CardPayment.java
├── PaymentFactory.java
└── Main.java
```

---

## Step 1: Create Interface

### Payment.java

```java
public interface Payment {

    void pay(double amount);

}
```

---

## Step 2: Create Implementations

### UpiPayment.java

```java
public class UpiPayment implements Payment {

    @Override
    public void pay(double amount) {

        System.out.println("Paid " + amount + " using UPI");

    }
}
```

### CardPayment.java

```java
public class CardPayment implements Payment {

    @Override
    public void pay(double amount) {

        System.out.println("Paid " + amount + " using Card");

    }
}
```

---

## Step 3: Create Factory Class

### PaymentFactory.java

```java
public class PaymentFactory {

    public static Payment getPayment(String paymentType) {

        if (paymentType.equalsIgnoreCase("UPI")) {
            return new UpiPayment();
        }

        else if (paymentType.equalsIgnoreCase("CARD")) {
            return new CardPayment();
        }

        throw new IllegalArgumentException("Invalid Payment Type");
    }
}
```

---

## Step 4: Client Code

### Main.java

```java
public class Main {

    public static void main(String[] args) {

        String paymentType = "UPI";

        Payment payment = PaymentFactory.getPayment(paymentType);

        payment.pay(1000);
    }
}
```

---

## Output

```text
Paid 1000.0 using UPI
```

---

## Flow Diagram

```text
Main
 ↓
PaymentFactory
 ↓
UpiPayment / CardPayment
 ↓
pay()
```

The client does not know which object is being created. The Factory class handles the object creation logic.

---

## Interview Questions

### What is Factory Pattern?

Factory Pattern creates objects without exposing the creation logic to the client.

---

### Why do we use Factory Pattern?

We use it to reduce tight coupling and centralize object creation logic.

---

### What problem does Factory Pattern solve?

It removes object creation responsibility from the client and makes the application easier to extend and maintain.

---

### Give a real-world example.

Payment systems, notification services, report generators, and document parsers commonly use the Factory Pattern.

---

## One-Line Summary

> Factory Pattern = Don't create objects using `new`; ask the Factory to create them for you.



------------------------------------------
# Builder Design Pattern

## What is Builder Pattern?

Builder Pattern is used to create complex objects step by step instead of using large constructors with many parameters.

---

## Interview Definition

> Builder Pattern helps us create complex objects in a readable and flexible way. It avoids constructor overloading and allows us to build objects step by step.

---

## Why Do We Use It?

* Avoids large constructors
* Improves code readability
* Supports optional fields
* Makes objects easy to maintain
* Commonly used with Lombok `@Builder` in Spring Boot

---

## Problem Without Builder Pattern

Suppose we have an Employee class:

```java
public class Employee {

    private String name;
    private String email;
    private String department;
    private String address;
    private String phoneNumber;

    public Employee(String name, String email, String department,
                    String address, String phoneNumber) {
        this.name = name;
        this.email = email;
        this.department = department;
        this.address = address;
        this.phoneNumber = phoneNumber;
    }
}
```

Creating an object:

```java
Employee emp = new Employee(
        "Arti",
        "arti@gmail.com",
        "IT",
        "Pune",
        "9876543210"
);
```

### Problems

* Difficult to remember parameter order.
* Readability is poor.
* Optional fields are hard to handle.
* Constructor becomes huge when new fields are added.

---

# Builder Pattern Example (Without Lombok)

## Project Structure

```text
src
│
├── Employee.java
└── Main.java
```

---

## Employee.java

```java
public class Employee {

    private String name;
    private String email;
    private String department;
    private String address;
    private String phoneNumber;

    private Employee(EmployeeBuilder builder) {
        this.name = builder.name;
        this.email = builder.email;
        this.department = builder.department;
        this.address = builder.address;
        this.phoneNumber = builder.phoneNumber;
    }

    public static class EmployeeBuilder {

        private String name;
        private String email;
        private String department;
        private String address;
        private String phoneNumber;

        public EmployeeBuilder name(String name) {
            this.name = name;
            return this;
        }

        public EmployeeBuilder email(String email) {
            this.email = email;
            return this;
        }

        public EmployeeBuilder department(String department) {
            this.department = department;
            return this;
        }

        public EmployeeBuilder address(String address) {
            this.address = address;
            return this;
        }

        public EmployeeBuilder phoneNumber(String phoneNumber) {
            this.phoneNumber = phoneNumber;
            return this;
        }

        public Employee build() {
            return new Employee(this);
        }
    }

    @Override
    public String toString() {
        return "Employee{" +
                "name='" + name + '\'' +
                ", email='" + email + '\'' +
                ", department='" + department + '\'' +
                ", address='" + address + '\'' +
                ", phoneNumber='" + phoneNumber + '\'' +
                '}';
    }
}
```

---

## Main.java

```java
public class Main {

    public static void main(String[] args) {

        Employee employee = new Employee.EmployeeBuilder()
                .name("Arti")
                .email("arti@gmail.com")
                .department("IT")
                .address("Pune")
                .phoneNumber("9876543210")
                .build();

        System.out.println(employee);
    }
}
```

---

## Output

```text
Employee{
name='Arti',
email='arti@gmail.com',
department='IT',
address='Pune',
phoneNumber='9876543210'
}
```

---

# Builder Pattern Using Lombok (Industry Approach)

## Employee.java

```java
import lombok.Builder;
import lombok.Data;

@Data
@Builder
public class Employee {

    private String name;
    private String email;
    private String department;
    private String address;
    private String phoneNumber;
}
```

---

## Main.java

```java
public class Main {

    public static void main(String[] args) {

        Employee employee = Employee.builder()
                .name("Arti")
                .email("arti@gmail.com")
                .department("IT")
                .address("Pune")
                .phoneNumber("9876543210")
                .build();

        System.out.println(employee);
    }
}
```

---

# Flow Diagram

```text
Main
 ↓
Employee.builder()
 ↓
Set properties one by one
 ↓
build()
 ↓
Employee Object Created
```

---

# Where Is It Used In Spring Boot?

Builder Pattern is commonly used in:

* DTO Classes
* Response Objects
* Request Objects
* Immutable Objects
* Entity-to-DTO Mapping

Example:

```java
EmployeeResponse response = EmployeeResponse.builder()
        .id(1L)
        .name("Arti")
        .email("arti@gmail.com")
        .build();
```

---

# Interview Questions
---
```
"Builder Pattern is a creational design pattern that is used to create complex objects step by step instead of using large constructors with many parameters. It improves code readability and makes it easy to handle optional fields.

In Spring Boot projects, I have mainly used Lombok's @Builder annotation for DTOs and response objects. It helps avoid constructor overloading and makes object creation more clean and maintainable.

For example:

EmployeeResponse response = EmployeeResponse.builder()
        .id(1)
        .name("Arti")
        .email("arti@gmail.com")
        .build();

So, Builder Pattern solves the problem of telescoping constructors and provides a flexible way to create objects."

Short Version (1 Minute Answer)

"Builder Pattern is used to create complex objects step by step. It improves readability, avoids large constructors, and handles optional fields easily. In Spring Boot, I have used Lombok @Builder for DTOs and API response objects."

give mi cross que too
Builder Pattern - Cross Questions (Interview Ready)

These are the common follow-up questions an interviewer can ask after you explain Builder Pattern.

1. What problem does Builder Pattern solve?
Answer:

Builder Pattern solves the telescoping constructor problem. When a class has many fields, constructors become large and difficult to understand. Builder Pattern allows us to create objects step by step in a readable way.

2. Why not use setters instead of Builder?
Answer:

Setters make objects mutable, meaning anyone can change their values later. Builder Pattern helps create immutable objects and makes the code more readable and maintainable.

3. What is the telescoping constructor problem?
Answer:

Suppose we have:

Employee(String name)

Employee(String name, String email)

Employee(String name, String email, String department)

Employee(String name, String email, String department, String address)

Too many constructors are created, which makes the code difficult to maintain.

Builder Pattern solves this problem.

4. Where have you used Builder Pattern in your project?
Answer:

I have mainly used Lombok @Builder for DTOs, API response objects, request objects, and immutable classes in Spring Boot applications.

Example:

EmployeeResponse response = EmployeeResponse.builder()
        .id(1L)
        .name("Arti")
        .email("arti@gmail.com")
        .build();
5. What are the advantages of Builder Pattern?
Answer:
Improves code readability.
Handles optional parameters easily.
Avoids constructor overloading.
Supports immutable objects.
Easy to maintain and extend.
6. Is Lombok @Builder an implementation of Builder Pattern?
Answer:

Yes, Lombok @Builder automatically generates Builder Pattern code, so we don't need to write the builder class manually.

7. Can Builder Pattern create immutable objects?
Answer:

Yes. Builder Pattern is commonly used to create immutable objects because all values are set during object creation, and the object does not need setters afterward.

8. What is the difference between Factory Pattern and Builder Pattern?
Factory Pattern	Builder Pattern
Creates different types of objects	Creates one complex object step by step
Focuses on object creation logic	Focuses on object construction
Example: Payment Factory	Example: Employee Builder
Interview Answer:

Factory Pattern is used to create different types of objects, while Builder Pattern is used to create a single complex object step by step.

9. When should we use Builder Pattern?
Answer:

We should use Builder Pattern when a class has many fields, especially optional fields, and when we want readable and maintainable object creation.

10. What is the biggest advantage of Builder Pattern?
Answer:

The biggest advantage is that it improves readability and avoids large constructors with many parameters.
```
---

```
5️⃣ Prototype Design Pattern

⭐ Interview Importance: Low to Medium

For a 4+ years Java/Spring Boot developer, usually a basic understanding with one example is enough.

What is Prototype Pattern?
Interview Definition (Simple)

Prototype Pattern is used to create new objects by copying (cloning) an existing object instead of creating a new one from scratch.

Why Do We Use It?

We use Prototype Pattern when:

Object creation is expensive or time-consuming.
We need multiple similar objects.
We want better performance by cloning existing objects.
What Problem Does It Solve?
❌ Without Prototype Pattern

Suppose creating an employee object takes a lot of time:

Employee emp1 = new Employee("Arti", "IT", 50000);

Employee emp2 = new Employee("Arti", "IT", 50000);

Employee emp3 = new Employee("Arti", "IT", 50000);

Problems:

❌ Same data is created again and again.

❌ Object creation can be expensive.

❌ Performance may decrease.

✅ With Prototype Pattern
Employee emp1 = new Employee("Arti", "IT", 50000);

Employee emp2 = emp1.clone();

Employee emp3 = emp1.clone();

Now:

✅ We create one object.

✅ Other objects are created by cloning.

✅ Better performance.
```



