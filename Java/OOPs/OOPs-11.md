# Java OOP Master Guide

# Part 11 - OOP Design Patterns for Java Interviews

---

# Table of Contents

1. What Are Design Patterns?
2. Why Design Patterns Matter
3. Types of Design Patterns
4. Singleton Pattern
5. Factory Pattern
6. Builder Pattern
7. Strategy Pattern
8. Observer Pattern
9. Template Method Pattern
10. Dependency Injection Pattern
11. Design Patterns in Selenium Frameworks
12. Design Patterns in API Automation Frameworks
13. Design Patterns in Spring Boot
14. Real Project Architecture Examples
15. Common Interview Traps
16. Top Interview Questions
17. Revision Notes
18. Final Cheat Sheet

---

# 1. What Are Design Patterns?

Definition:

```text
Design Patterns are reusable solutions
to commonly occurring software design problems.
```

---

Think Of Them As:

```text
Best Practices

↓

Proven Solutions

↓

Reusable Architecture
```

---

Created By:

Gang of Four

Popularly Called:

```text
GoF Design Patterns
```

---

# 2. Why Design Patterns Matter

Without Patterns:

```text
Tight Coupling

Code Duplication

Difficult Maintenance

Hard Scalability
```

---

With Patterns:

```text
Reusable Design

Flexible Architecture

Maintainable Frameworks

Easy Testing
```

---

Interviewers Love Design Pattern Questions Because:

```text
Patterns Show Design Thinking
```

---

# 3. Types of Design Patterns

Main Categories:

```text
1. Creational

2. Structural

3. Behavioral
```

---

Examples:

| Category   | Patterns                    |
| ---------- | --------------------------- |
| Creational | Singleton, Factory, Builder |
| Structural | Adapter, Decorator          |
| Behavioral | Strategy, Observer          |

---

Most Asked In Interviews:

```text
Singleton

Factory

Builder

Strategy

Observer
```

---

# 4. Singleton Pattern

Definition:

```text
Ensures only one object
exists throughout application.
```

---

Use Cases:

```text
Logger

Configuration Manager

WebDriver Manager

Database Connection Pool
```

---

Implementation:

```java
public class Singleton {

    private static Singleton instance;

    private Singleton(){

    }

    public static Singleton getInstance(){

        if(instance == null){

            instance = new Singleton();
        }

        return instance;
    }
}
```

---

Usage:

```java
Singleton obj1 =
Singleton.getInstance();

Singleton obj2 =
Singleton.getInstance();
```

---

Result:

```text
Both References Point
To Same Object
```

---

Interview Question:

```text
Why Constructor Is Private?
```

Answer:

```text
Prevent Direct Object Creation
```

---

Thread-Safe Singleton:

```java
public static synchronized
Singleton getInstance(){

}
```

---

# 5. Factory Pattern

Definition:

```text
Creates Objects Without
Exposing Creation Logic
```

---

Problem:

```java
Car car =
new BMW();
```

---

Client Knows Exact Class.

Tight Coupling.

---

Factory Solution:

```java
interface Car {

    void drive();
}
```

---

```java
class BMW
implements Car {

}
```

---

```java
class Audi
implements Car {

}
```

---

Factory:

```java
class CarFactory {

    static Car getCar(
        String type){

        if(type.equals("BMW")){

            return new BMW();
        }

        return new Audi();
    }
}
```

---

Usage:

```java
Car car =
CarFactory.getCar("BMW");
```

---

Benefits:

```text
Loose Coupling

Easy Extension
```

---

# 6. Builder Pattern

Definition:

```text
Used To Create Complex Objects
Step By Step
```

---

Without Builder:

```java
Employee emp =
new Employee(
    "Rahul",
    28,
    "QA",
    "Mumbai",
    true,
    100000
);
```

---

Problem:

```text
Too Many Constructor Parameters
```

---

Builder Solution:

```java
Employee emp =
new Employee.Builder()
.name("Rahul")
.age(28)
.department("QA")
.build();
```

---

Benefits:

```text
Readable

Maintainable

Immutable Objects
```

---

Used Heavily In:

```text
REST Assured

Lombok

Spring
```

---

# 7. Strategy Pattern

Definition:

```text
Select Algorithm At Runtime
```

---

Example:

Payment Methods.

---

Interface:

```java
interface PaymentStrategy {

    void pay();
}
```

---

Implementations:

```java
class CardPayment
implements PaymentStrategy {

}
```

---

```java
class UPIPayment
implements PaymentStrategy {

}
```

---

Runtime Selection:

```java
PaymentStrategy payment =
new UPIPayment();
```

---

Benefits:

```text
No If-Else Chains

Easy Extension
```

---

Framework Favorite Pattern.

---

# 8. Observer Pattern

Definition:

```text
One Object Notifies
Multiple Dependent Objects
```

---

Real Example:

```text
YouTube Channel

↓

Subscribers
```

---

When Video Uploaded:

```text
Subscribers Get Notification
```

---

Java Example:

```java
interface Observer {

    void update();
}
```

---

```java
class Subscriber
implements Observer {

}
```

---

Benefits:

```text
Event-Driven Systems
```

---

Used In:

```text
GUI

Messaging Systems

Microservices
```

---

# 9. Template Method Pattern

Definition:

```text
Defines Overall Algorithm

Allows Child Classes
To Implement Specific Steps
```

---

Abstract Class:

```java
abstract class TestExecution {

    public final void execute(){

        setup();

        runTest();

        tearDown();
    }

    abstract void runTest();
}
```

---

Child:

```java
class LoginTest
extends TestExecution {

    void runTest(){

    }
}
```

---

Benefits:

```text
Reusable Flow

Customizable Steps
```

---

Used In:

```text
TestNG

JUnit

Selenium Frameworks
```

---

# 10. Dependency Injection Pattern

Definition:

```text
Provide Dependencies
From Outside
```

---

Bad Design:

```java
class UserService {

    Database db =
    new Database();
}
```

---

Problem:

```text
Tight Coupling
```

---

Good Design:

```java
class UserService {

    Database db;

    UserService(
       Database db){

       this.db = db;
    }
}
```

---

Benefits:

```text
Loose Coupling

Easy Testing

Mocking Support
```

---

Foundation Of:

```text
Spring Framework
```

---

# 11. Design Patterns in Selenium Frameworks

### Singleton

```text
WebDriver Manager
```

---

One Driver Instance.

---

### Factory

```text
ChromeDriver

FirefoxDriver

EdgeDriver
```

Created Dynamically.

---

### Strategy

```text
Different Browser Execution
```

---

### Template Method

```text
BaseTest
```

Defines Execution Flow.

---

### Builder

```text
TestData Creation
```

---

# 12. Design Patterns in API Automation Frameworks

### Factory

```text
API Client Creation
```

---

### Builder

```java
RequestSpecification
```

Builder Style API.

---

### Singleton

```text
Config Manager
```

---

### Strategy

```text
Authentication Strategy

OAuth

JWT

Basic Auth
```

---

# 13. Design Patterns in Spring Boot

Spring Uses:

```text
Singleton

Dependency Injection

Factory

Proxy

Template Pattern
```

---

Example:

```java
@Bean
```

---

Creates:

```text
Singleton Objects
```

---

Dependency Injection:

```java
@Autowired
```

---

Major Interview Topic.

---

# 14. Real Project Architecture Examples

Automation Framework:

```text
DriverFactory

↓

DriverManager

↓

Page Objects

↓

Test Classes
```

---

Patterns:

```text
Factory

Singleton

Template Method
```

---

E-Commerce Application:

```text
PaymentStrategy

↓

Card

UPI

Wallet
```

---

Pattern:

```text
Strategy Pattern
```

---

Notification System:

```text
Observer Pattern
```

---

# 15. Common Interview Traps

### Trap 1

```text
Which Pattern Creates
Only One Object?
```

Answer:

```text
Singleton
```

---

### Trap 2

```text
Which Pattern Avoids
Huge Constructors?
```

Answer:

```text
Builder
```

---

### Trap 3

```text
Which Pattern Supports
Runtime Algorithm Selection?
```

Answer:

```text
Strategy
```

---

### Trap 4

```text
Which Pattern Is Used By Spring?
```

Answer:

```text
Dependency Injection
```

---

### Trap 5

```text
Which Pattern Is Common
In WebDriver Creation?
```

Answer:

```text
Factory Pattern
```

---

# 16. Top Interview Questions

### Q1 What Are Design Patterns?

```text
Reusable solutions for common design problems.
```

---

### Q2 What Is Singleton Pattern?

```text
Ensures only one object exists.
```

---

### Q3 What Is Factory Pattern?

```text
Creates objects without exposing creation logic.
```

---

### Q4 What Is Builder Pattern?

```text
Creates complex objects step by step.
```

---

### Q5 What Is Strategy Pattern?

```text
Changes behavior dynamically at runtime.
```

---

### Q6 What Is Observer Pattern?

```text
One-to-many notification mechanism.
```

---

### Q7 Which Pattern Does Spring Use Most?

```text
Dependency Injection
```

---

# 17. Revision Notes

```text
Design Patterns

↓

Creational

↓

Singleton

Factory

Builder

Behavioral

↓

Strategy

Observer

Template Method

Enterprise Favorite

↓

Dependency Injection
```

---

# 18. Final Cheat Sheet

```text
Singleton

↓

Single Object

Factory

↓

Object Creation

Builder

↓

Complex Object Creation

Strategy

↓

Runtime Behavior Change

Observer

↓

Notifications

Template Method

↓

Fixed Flow

Dependency Injection

↓

Loose Coupling
```

---

# Interview Takeaway

If interviewer asks:

```text
Which design patterns have you used in your Selenium framework?
```

Strong Answer:

```text
I have used Factory Pattern for browser creation,
Singleton Pattern for driver/config management,
Template Method Pattern in BaseTest execution flow,
Builder Pattern for test data creation, and
Strategy Pattern for browser-specific execution.

These patterns improve maintainability,
reusability, scalability, and reduce code duplication.
```

---

# End of OOP Part 11

## Next Part

```text
Part 12 → OOP Master Revision Guide

Topics:

✓ Complete OOP Revision

✓ Inheritance Revision

✓ Polymorphism Revision

✓ Encapsulation Revision

✓ Abstraction Revision

✓ Interface Revision

✓ Relationships Revision

✓ SOLID Revision

✓ Design Patterns Revision

✓ Framework-Based Revision

✓ 100+ Rapid Fire Interview Questions

✓ Final OOP Cheat Sheet

✓ MNC Interview Notes
```
