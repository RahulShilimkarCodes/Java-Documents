# Java OOP Master Guide

# Part 6 - Abstraction Deep Dive

---

# Table of Contents

1. What is Abstraction?
2. Why Abstraction is Needed
3. Real-World Examples of Abstraction
4. Abstraction vs Encapsulation
5. Abstract Classes
6. Abstract Methods
7. Concrete Methods
8. Rules of Abstract Classes
9. Rules of Abstract Methods
10. Partial Abstraction
11. 100% Abstraction
12. Abstract Class vs Interface
13. Template Method Design Pattern
14. Constructor in Abstract Classes
15. Variable Behavior in Abstract Classes
16. Abstraction in Selenium Frameworks
17. Abstraction in API Frameworks
18. Real Project Scenarios
19. Advantages of Abstraction
20. Common Interview Traps
21. Top Interview Questions
22. Revision Notes
23. Final Cheat Sheet

---

# 1. What is Abstraction?

Abstraction is one of the four pillars of OOP.

Definition:

```text id="abs001"
Abstraction is the process of hiding
implementation details and showing only
essential functionality.
```

---

Simple Definition:

```text id="abs002"
What To Do

Not

How To Do
```

---

Example:

```text id="abs003"
Car Steering
```

Driver Knows:

```text id="abs004"
Turn Left

Turn Right
```

---

Driver Does NOT Need To Know:

```text id="abs005"
Hydraulic System

Mechanical Linkages

Steering Internals
```

---

This is Abstraction.

---

# 2. Why Abstraction is Needed

Without Abstraction:

```text id="abs006"
Users Need To Understand
Every Internal Detail
```

---

Problems:

```text id="abs007"
Complex Design

Tight Coupling

Poor Maintainability
```

---

With Abstraction:

```text id="abs008"
Expose Required Features

Hide Internal Logic
```

---

Benefits:

```text id="abs009"
Simpler API

Better Security

Easy Maintenance
```

---

# 3. Real-World Examples of Abstraction

### ATM Machine

Visible:

```text id="abs010"
Withdraw

Deposit

Balance Inquiry
```

---

Hidden:

```text id="abs011"
Database Calls

Network Requests

Encryption
```

---

### Mobile Phone

Visible:

```text id="abs012"
Call

Message

Camera
```

---

Hidden:

```text id="abs013"
OS Internals

Hardware Drivers

Communication Protocols
```

---

# 4. Abstraction vs Encapsulation

Very Important Interview Topic.

| Abstraction                               | Encapsulation                   |
| ----------------------------------------- | ------------------------------- |
| Hides Implementation                      | Hides Data                      |
| Focuses On What                           | Focuses On How Access Happens   |
| Achieved Using Abstract Class & Interface | Achieved Using Access Modifiers |
| Design Level Concept                      | Object Level Concept            |

---

Interview Answer:

```text id="abs014"
Abstraction hides implementation details,
whereas encapsulation hides object data.
```

---

# 5. Abstract Classes

Definition:

```text id="abs015"
A class declared with abstract keyword.
```

---

Example:

```java id="abs016"
abstract class Animal {

}
```

---

Important Rule:

```text id="abs017"
Cannot Create Object
Of Abstract Class
```

---

Invalid:

```java id="abs018"
Animal a =
new Animal();
```

---

Compilation Error.

---

# 6. Abstract Methods

Definition:

```text id="abs019"
Method without implementation.
```

---

Example:

```java id="abs020"
abstract class Animal {

    abstract void sound();
}
```

---

Characteristics:

```text id="abs021"
No Body

Ends With Semicolon
```

---

Example:

```java id="abs022"
abstract void sound();
```

---

# 7. Concrete Methods

Normal methods inside abstract class.

Example:

```java id="abs023"
abstract class Animal {

    void sleep(){

        System.out.println("Sleeping");
    }
}
```

---

This is:

```text id="abs024"
Concrete Method
```

---

Meaning:

```text id="abs025"
Abstract Class Can Have

Abstract Methods

and

Normal Methods
```

---

# 8. Rules of Abstract Classes

Rule 1

```text id="abs026"
Can Contain Constructors
```

---

Rule 2

```text id="abs027"
Can Contain Variables
```

---

Rule 3

```text id="abs028"
Can Contain Concrete Methods
```

---

Rule 4

```text id="abs029"
Cannot Be Instantiated
```

---

Rule 5

```text id="abs030"
May Or May Not Have
Abstract Methods
```

---

Example:

```java id="abs031"
abstract class Employee {

    int id;

    Employee(){

    }

    void display(){

    }
}
```

---

Valid.

---

# 9. Rules of Abstract Methods

Rule 1

```text id="abs032"
Must Be Inside Abstract Class
Or Interface
```

---

Rule 2

```text id="abs033"
No Method Body
```

---

Rule 3

```text id="abs034"
Child Must Implement
```

---

Example:

```java id="abs035"
abstract void login();
```

---

# 10. Partial Abstraction

Achieved Through:

```text id="abs036"
Abstract Classes
```

---

Example:

```java id="abs037"
abstract class Vehicle {

    abstract void start();

    void fuel(){

    }
}
```

---

Contains:

```text id="abs038"
Abstract Method

+

Concrete Method
```

---

Called:

```text id="abs039"
Partial Abstraction
```

---

# 11. 100% Abstraction

Traditionally Achieved Through:

```text id="abs040"
Interfaces
```

---

Example:

```java id="abs041"
interface Payment {

    void pay();
}
```

---

Only Contract.

No Implementation Requirement.

---

Modern Java:

```text id="abs042"
Default Methods Exist

So Interface Is No Longer
Strictly 100% Abstract
```

---

Advanced Interview Topic.

---

# 12. Abstract Class vs Interface

| Abstract Class              | Interface                |
| --------------------------- | ------------------------ |
| Uses abstract keyword       | Uses interface keyword   |
| Can Have Constructors       | Cannot Have Constructors |
| Can Have Instance Variables | Only Constants           |
| Single Inheritance          | Multiple Inheritance     |
| Partial Abstraction         | Contract Definition      |

---

Interview Favorite.

---

# 13. Template Method Design Pattern

Built Using Abstract Classes.

Example:

```java id="abs043"
abstract class TestExecution {

    void execute(){

        setup();

        runTest();

        tearDown();
    }

    abstract void runTest();
}
```

---

Child:

```java id="abs044"
class LoginTest
extends TestExecution {

    void runTest(){

    }
}
```

---

Frameworks Use This Extensively.

---

# 14. Constructor in Abstract Classes

Allowed.

Example:

```java id="abs045"
abstract class Employee {

    Employee(){

        System.out.println(
            "Parent Constructor"
        );
    }
}
```

---

Child:

```java id="abs046"
class Developer
extends Employee {

}
```

---

Usage:

```java id="abs047"
new Developer();
```

Output:

```text id="abs048"
Parent Constructor
```

---

Interview Question:

```text id="abs049"
Can Abstract Class Have Constructor?
```

Answer:

```text id="abs050"
Yes
```

---

# 15. Variable Behavior in Abstract Classes

Example:

```java id="abs051"
abstract class Employee {

    String company =
        "OpenAI";
}
```

---

Child:

```java id="abs052"
class Developer
extends Employee {

}
```

---

Usage:

```java id="abs053"
Developer d =
new Developer();

System.out.println(
d.company
);
```

---

Output:

```text id="abs054"
OpenAI
```

---

Variables Can Be Inherited.

---

# 16. Abstraction in Selenium Frameworks

Example:

```java id="abs055"
public abstract class BasePage {

    protected WebDriver driver;

    public abstract boolean
    isPageLoaded();
}
```

---

Child:

```java id="abs056"
public class LoginPage
extends BasePage {

    @Override

    public boolean isPageLoaded(){

        return true;
    }
}
```

---

Benefits:

```text id="abs057"
Common Framework Contract
```

---

# 17. Abstraction in API Frameworks

Abstract Base Service:

```java id="abs058"
public abstract class BaseAPI {

    abstract String
    getEndpoint();
}
```

---

Implementation:

```java id="abs059"
public class UserAPI
extends BaseAPI {

    String getEndpoint(){

        return "/users";
    }
}
```

---

Benefits:

```text id="abs060"
Standard API Structure
```

---

# 18. Real Project Scenarios

Automation Framework:

```java id="abs061"
BasePage

↓

LoginPage

HomePage

CartPage
```

---

Each Page:

```text id="abs062"
Implements Common Contract
```

---

API Framework:

```java id="abs063"
BaseService

↓

UserService

ProductService

OrderService
```

---

Shared Behavior:

```text id="abs064"
Authentication

Logging

Reporting
```

---

# 19. Advantages of Abstraction

```text id="abs065"
Reduced Complexity

Better Design

Security

Loose Coupling

Scalability

Maintainability
```

---

Enterprise Benefit:

```text id="abs066"
Clear Contracts Between Components
```

---

# 20. Common Interview Traps

### Trap 1

```text id="abs067"
Can Abstract Class Have Constructor?
```

Answer:

```text id="abs068"
Yes
```

---

### Trap 2

```text id="abs069"
Can Abstract Class Have Concrete Methods?
```

Answer:

```text id="abs070"
Yes
```

---

### Trap 3

```text id="abs071"
Can Abstract Method Be Private?
```

Answer:

```text id="abs072"
No
```

---

### Trap 4

```text id="abs073"
Can We Create Object Of Abstract Class?
```

Answer:

```text id="abs074"
No
```

---

### Trap 5

```text id="abs075"
Can Abstract Class Have Variables?
```

Answer:

```text id="abs076"
Yes
```

---

# 21. Top Interview Questions

### Q1 What Is Abstraction?

```text id="abs077"
Hiding implementation details
while exposing functionality.
```

---

### Q2 How Is Abstraction Achieved?

```text id="abs078"
Abstract Classes

Interfaces
```

---

### Q3 Can Abstract Class Have Constructor?

```text id="abs079"
Yes
```

---

### Q4 Can Abstract Class Have Concrete Methods?

```text id="abs080"
Yes
```

---

### Q5 Difference Between Abstract Class And Interface?

```text id="abs081"
Abstract class provides partial implementation,
interface primarily defines contracts.
```

---

### Q6 Why Is Abstraction Important?

```text id="abs082"
Reduces complexity and improves maintainability.
```

---

# 22. Revision Notes

```text id="abs083"
Abstraction

↓

Hide Implementation

↓

Expose Functionality

Abstract Class

↓

Partial Abstraction

Abstract Method

↓

No Body

Interface

↓

Contract

Framework Usage

↓

Base Classes

↓

Reusable Design
```

---

# 23. Final Cheat Sheet

```text id="abs084"
abstract class

↓

Cannot Instantiate

abstract method

↓

No Implementation

Child Class

↓

Provides Implementation

Benefits

✓ Simplicity

✓ Security

✓ Scalability

✓ Maintainability

Framework Examples

BasePage

BaseAPI

BaseTest
```

---

# Interview Takeaway

If interviewer asks:

```text id="abs085"
Explain Abstraction with a Selenium Framework Example.
```

Strong Answer:

```text id="abs086"
Abstraction is the process of hiding implementation
details while exposing essential functionality.

In Selenium frameworks, a BasePage abstract class
can define common methods and contracts such as
isPageLoaded(). Individual pages like LoginPage
or HomePage provide their own implementations.

This creates a reusable and maintainable framework
while hiding internal implementation details from
test classes.
```

---

# End of OOP Part 6

## Next Part

```text id="abs087"
Part 7 → Interface Deep Dive

Topics:

✓ Interface Fundamentals

✓ Interface Rules

✓ Multiple Inheritance

✓ Default Methods

✓ Static Methods

✓ Private Methods

✓ Functional Interfaces

✓ Lambda Expressions Foundation

✓ Marker Interfaces

✓ Selenium Examples

✓ API Examples

✓ Framework Design

✓ Interview Questions

✓ Revision Notes
```
