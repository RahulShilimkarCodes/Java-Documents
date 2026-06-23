# Java OOP Master Guide

# Part 10 - SOLID Principles for Java Developers

---

# Table of Contents

1. Introduction to SOLID
2. Why SOLID Matters
3. Single Responsibility Principle (SRP)
4. Open Closed Principle (OCP)
5. Liskov Substitution Principle (LSP)
6. Interface Segregation Principle (ISP)
7. Dependency Inversion Principle (DIP)
8. SOLID in Selenium Frameworks
9. SOLID in API Automation Frameworks
10. SOLID in Spring Boot Applications
11. Real Project Architecture Examples
12. Common Design Mistakes
13. Common Interview Traps
14. Top Interview Questions
15. Revision Notes
16. Final Cheat Sheet

---

# 1. Introduction to SOLID

SOLID is a collection of five object-oriented design principles.

Created By:

Robert C. Martin

---

Purpose:

```text id="solid001"
Create Maintainable

Scalable

Flexible

Testable Software
```

---

SOLID Stands For:

```text id="solid002"
S → Single Responsibility Principle

O → Open Closed Principle

L → Liskov Substitution Principle

I → Interface Segregation Principle

D → Dependency Inversion Principle
```

---

Senior-Level Interview Favorite.

---

# 2. Why SOLID Matters

Without SOLID:

```text id="solid003"
Tight Coupling

Code Duplication

Difficult Testing

Hard Maintenance

Fragile Systems
```

---

With SOLID:

```text id="solid004"
Loose Coupling

Reusable Components

Easy Refactoring

Scalable Architecture
```

---

Enterprise Frameworks Depend On SOLID.

---

Examples:

```text id="solid005"
Spring Boot

Hibernate

Selenium Frameworks

Microservices
```

---

# 3. Single Responsibility Principle (SRP)

Definition:

```text id="solid006"
A class should have only one reason to change.
```

---

Bad Example:

```java id="solid007"
class UserService {

    void saveUser(){

    }

    void sendEmail(){

    }

    void generateReport(){

    }
}
```

---

Problems:

```text id="solid008"
Too Many Responsibilities
```

---

Better Design:

```java id="solid009"
class UserService {

    void saveUser(){

    }
}
```

---

```java id="solid010"
class EmailService {

    void sendEmail(){

    }
}
```

---

```java id="solid011"
class ReportService {

    void generateReport(){

    }
}
```

---

Benefits:

```text id="solid012"
Easy Maintenance

Easy Testing

Reusable Components
```

---

Interview Answer:

```text id="solid013"
One class = One responsibility.
```

---

# 4. Open Closed Principle (OCP)

Definition:

```text id="solid014"
Software entities should be open for extension
but closed for modification.
```

---

Bad Example:

```java id="solid015"
class PaymentService {

    void pay(String type){

        if(type.equals("UPI")){

        }
        else if(type.equals("CARD")){

        }
    }
}
```

---

Every New Payment Type Requires Modification.

---

Better:

```java id="solid016"
interface Payment {

    void pay();
}
```

---

```java id="solid017"
class UPIPayment
implements Payment {

}
```

---

```java id="solid018"
class CardPayment
implements Payment {

}
```

---

New Feature?

Create New Class.

No Existing Code Changes.

---

Benefits:

```text id="solid019"
Safer Changes

Scalable Design
```

---

# 5. Liskov Substitution Principle (LSP)

Definition:

```text id="solid020"
Child classes must be replaceable
with parent classes without breaking behavior.
```

---

Example:

```java id="solid021"
Animal animal =
new Dog();
```

---

Should Work Correctly.

---

Bad Example:

```java id="solid022"
class Bird {

    void fly(){

    }
}
```

---

```java id="solid023"
class Penguin
extends Bird {

    void fly(){

        throw new RuntimeException();
    }
}
```

---

Problem:

```text id="solid024"
Penguin Cannot Truly Replace Bird
```

---

LSP Violated.

---

Better Design:

```java id="solid025"
Bird
```

↓

```java id="solid026"
FlyingBird
```

↓

```java id="solid027"
Penguin
```

Separate Hierarchies.

---

# 6. Interface Segregation Principle (ISP)

Definition:

```text id="solid028"
Clients should not be forced to depend
on methods they do not use.
```

---

Bad Interface:

```java id="solid029"
interface Worker {

    void work();

    void eat();

    void sleep();
}
```

---

Robot Implementation:

```java id="solid030"
class Robot
implements Worker {

}
```

---

Problem:

```text id="solid031"
Robot Doesn't Eat Or Sleep
```

---

Better:

```java id="solid032"
interface Workable {

    void work();
}
```

---

```java id="solid033"
interface Eatable {

    void eat();
}
```

---

Benefits:

```text id="solid034"
Small Focused Interfaces
```

---

# 7. Dependency Inversion Principle (DIP)

Definition:

```text id="solid035"
High-level modules should not depend
on low-level modules.

Both should depend on abstractions.
```

---

Bad Example:

```java id="solid036"
class UserService {

    MySQLDatabase db =
        new MySQLDatabase();
}
```

---

Problem:

```text id="solid037"
Tight Coupling
```

---

Better:

```java id="solid038"
interface Database {

    void save();
}
```

---

```java id="solid039"
class MySQLDatabase
implements Database {

}
```

---

```java id="solid040"
class UserService {

    Database db;

    UserService(Database db){

        this.db = db;
    }
}
```

---

Benefits:

```text id="solid041"
Flexible

Mockable

Testable
```

---

Foundation Of:

```text id="solid042"
Dependency Injection
```

---

# 8. SOLID in Selenium Frameworks

Bad Design:

```java id="solid043"
LoginTest
```

Contains:

```text id="solid044"
Driver Setup

Reporting

Screenshot Logic

Login Logic

Assertions
```

---

Violates SRP.

---

Better:

```text id="solid045"
BaseTest

↓

DriverManager

↓

ReportManager

↓

Page Objects

↓

Test Classes
```

---

Benefits:

```text id="solid046"
Reusable Framework
```

---

OCP Example:

```java id="solid047"
ChromeDriver
```

↓

```java id="solid048"
FirefoxDriver
```

Added Without Changing Core Logic.

---

# 9. SOLID in API Automation Frameworks

Example:

```text id="solid049"
BaseAPI

↓

UserAPI

↓

OrderAPI

↓

ProductAPI
```

---

DIP Example:

```java id="solid050"
UserService
```

Depends On:

```java id="solid051"
APIClient Interface
```

Not Concrete Client.

---

Benefits:

```text id="solid052"
Easy Mocking

Reusable Services
```

---

# 10. SOLID in Spring Boot Applications

Spring Is Built Around SOLID.

---

Dependency Injection:

```java id="solid053"
@Autowired
```

---

Represents:

```text id="solid054"
Dependency Inversion Principle
```

---

Repository Layer:

```java id="solid055"
UserRepository
```

---

Service Layer:

```java id="solid056"
UserService
```

---

Controller Layer:

```java id="solid057"
UserController
```

---

SRP Applied.

---

# 11. Real Project Architecture Examples

E-Commerce Application:

```text id="solid058"
Controller

↓

Service

↓

Repository

↓

Database
```

---

Each Layer:

```text id="solid059"
Single Responsibility
```

---

Payment System:

```text id="solid060"
Payment Interface

↓

UPI

Card

Wallet

NetBanking
```

---

OCP Applied.

---

Notification System:

```text id="solid061"
Notification Interface

↓

Email

SMS

Slack

Teams
```

---

DIP + OCP Applied.

---

# 12. Common Design Mistakes

Mistake 1

```text id="solid062"
God Classes
```

---

Meaning:

```text id="solid063"
One Class Doing Everything
```

---

Mistake 2

```text id="solid064"
Large Interfaces
```

---

Violates:

```text id="solid065"
ISP
```

---

Mistake 3

```text id="solid066"
Direct Object Creation
```

---

Violates:

```text id="solid067"
DIP
```

---

Mistake 4

```text id="solid068"
Huge Inheritance Trees
```

---

Violates:

```text id="solid069"
LSP
```

---

# 13. Common Interview Traps

### Trap 1

```text id="solid070"
Which SOLID Principle Does Spring DI Use?
```

Answer:

```text id="solid071"
DIP
```

---

### Trap 2

```text id="solid072"
Which Principle Says One Class One Responsibility?
```

Answer:

```text id="solid073"
SRP
```

---

### Trap 3

```text id="solid074"
Which Principle Encourages Interfaces?
```

Answer:

```text id="solid075"
DIP and ISP
```

---

### Trap 4

```text id="solid076"
Which Principle Is Violated By Penguin Example?
```

Answer:

```text id="solid077"
LSP
```

---

# 14. Top Interview Questions

### Q1 What Is SOLID?

```text id="solid078"
Five OOP design principles for maintainable software.
```

---

### Q2 What Is SRP?

```text id="solid079"
One class should have one reason to change.
```

---

### Q3 What Is OCP?

```text id="solid080"
Open for extension, closed for modification.
```

---

### Q4 What Is LSP?

```text id="solid081"
Child should replace parent without breaking behavior.
```

---

### Q5 What Is ISP?

```text id="solid082"
Create small focused interfaces.
```

---

### Q6 What Is DIP?

```text id="solid083"
Depend on abstractions, not implementations.
```

---

### Q7 Which SOLID Principle Is Most Used In Frameworks?

```text id="solid084"
DIP
```

---

# 15. Revision Notes

```text id="solid085"
SOLID

↓

SRP

↓

One Responsibility

OCP

↓

Extend

Don't Modify

LSP

↓

Substitution

ISP

↓

Small Interfaces

DIP

↓

Depend On Abstractions
```

---

# 16. Final Cheat Sheet

```text id="solid086"
SRP

↓

One Job

OCP

↓

Add Features
Without Modifying

LSP

↓

Replace Parent
With Child

ISP

↓

Small Interfaces

DIP

↓

Interfaces
Not Implementations

Frameworks

↓

Spring

Selenium

REST Assured

Microservices
```

---

# Interview Takeaway

If interviewer asks:

```text id="solid087"
How do you apply SOLID principles in your Selenium framework?
```

Strong Answer:

```text id="solid088"
I apply SRP by separating DriverManager,
Page Objects, ReportManager, and Test Classes.

I apply OCP using interfaces and pluggable
components such as browser drivers and report engines.

I apply DIP by depending on abstractions and
injecting dependencies rather than creating
objects directly.

This makes the framework scalable, maintainable,
and easy to extend without impacting existing tests.
```

---

# End of OOP Part 10

## Next Part

```text id="solid089"
Part 11 → OOP Design Patterns for Java Interviews

Topics:

✓ Singleton Pattern

✓ Factory Pattern

✓ Builder Pattern

✓ Strategy Pattern

✓ Observer Pattern

✓ Template Method Pattern

✓ Dependency Injection Pattern

✓ Selenium Framework Examples

✓ API Framework Examples

✓ Real Project Architecture

✓ Interview Questions

✓ Revision Notes

✓ OOP Master Revision
```
