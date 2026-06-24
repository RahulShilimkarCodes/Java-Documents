# Java OOP Master Guide

# Part 7 - Interface Deep Dive

---

# Table of Contents

1. What is an Interface?
2. Why Interfaces Are Needed
3. Interface Fundamentals
4. Interface Syntax
5. Interface Rules
6. Implementing an Interface
7. Multiple Inheritance Using Interfaces
8. Interface vs Abstract Class
9. Default Methods
10. Static Methods
11. Private Methods
12. Functional Interfaces
13. Lambda Expressions Foundation
14. Marker Interfaces
15. Interface Variables
16. Multiple Interface Implementation
17. Interface Inheritance
18. Interfaces in Selenium Frameworks
19. Interfaces in API Frameworks
20. Real Project Scenarios
21. Common Interview Traps
22. Top Interview Questions
23. Revision Notes
24. Final Cheat Sheet

---

# 1. What is an Interface?

Definition:

```text id="int001"
An interface is a contract that specifies
what a class must do, but not how it does it.
```

---

Simple Definition:

```text id="int002"
Interface Defines Rules

Classes Provide Implementation
```

---

Real World Example:

```text id="int003"
Remote Control
```

---

Buttons:

```text id="int004"
Power

Volume

Mute
```

---

Remote Defines:

```text id="int005"
What Actions Exist
```

---

TV Defines:

```text id="int006"
How Actions Work
```

---

This is Interface-Based Design.

---

# 2. Why Interfaces Are Needed

Without Interfaces:

```java id="int007"
class ChromeBrowser {

}
```

---

```java id="int008"
class FirefoxBrowser {

}
```

---

Each Class Has Different Methods.

---

Problem:

```text id="int009"
Tight Coupling

Difficult Maintenance

No Standardization
```

---

With Interface:

```java id="int010"
interface Browser {

    void launch();
}
```

---

All Browsers Follow Same Contract.

---

Benefits:

```text id="int011"
Loose Coupling

Flexibility

Scalability
```

---

# 3. Interface Fundamentals

Example:

```java id="int012"
interface Animal {

    void sound();
}
```

---

Important:

```text id="int013"
Interface Describes Behavior

Not Implementation
```

---

Implementation:

```java id="int014"
class Dog
implements Animal {

    public void sound(){

        System.out.println("Bark");
    }
}
```

---

# 4. Interface Syntax

Declaration:

```java id="int015"
interface Payment {

    void pay();
}
```

---

Implementation:

```java id="int016"
class UPIPayment
implements Payment {

    public void pay(){

        System.out.println("UPI Payment");
    }
}
```

---

Usage:

```java id="int017"
Payment payment =
new UPIPayment();

payment.pay();
```

---

# 5. Interface Rules

Rule 1

```text id="int018"
Cannot Create Interface Object
```

---

Invalid:

```java id="int019"
Payment p =
new Payment();
```

---

Rule 2

```text id="int020"
Class Uses implements Keyword
```

---

Rule 3

```text id="int021"
Methods Are Public By Default
```

---

Rule 4

```text id="int022"
Variables Are Public Static Final
```

---

Rule 5

```text id="int023"
Supports Multiple Inheritance
```

---

# 6. Implementing an Interface

Interface:

```java id="int024"
interface Vehicle {

    void start();
}
```

---

Class:

```java id="int025"
class Car
implements Vehicle {

    public void start(){

        System.out.println("Car Started");
    }
}
```

---

Important Rule:

```text id="int026"
Implementation Method Must Be Public
```

---

# 7. Multiple Inheritance Using Interfaces

Major Advantage.

Example:

```java id="int027"
interface Camera {

    void click();
}
```

---

```java id="int028"
interface MusicPlayer {

    void play();
}
```

---

```java id="int029"
class Smartphone
implements Camera,
           MusicPlayer {

    public void click(){

    }

    public void play(){

    }
}
```

---

Diagram:

```text id="int030"
Camera

      \
       \
        Smartphone
       /
      /

MusicPlayer
```

---

Supported.

---

# 8. Interface vs Abstract Class

| Interface            | Abstract Class             |
| -------------------- | -------------------------- |
| Contract             | Partial Implementation     |
| Multiple Inheritance | Single Inheritance         |
| No Constructors      | Constructors Allowed       |
| Constants Only       | Instance Variables Allowed |
| Uses implements      | Uses extends               |

---

Interview Favorite.

---

# 9. Default Methods

Introduced In:

```text id="int031"
Java 8
```

---

Purpose:

```text id="int032"
Backward Compatibility
```

---

Example:

```java id="int033"
interface Vehicle {

    default void fuel(){

        System.out.println("Petrol");
    }
}
```

---

Implementation Optional.

---

Usage:

```java id="int034"
Car car =
new Car();

car.fuel();
```

---

# 10. Static Methods

Introduced In:

```text id="int035"
Java 8
```

---

Example:

```java id="int036"
interface Utility {

    static void display(){

        System.out.println("Utility");
    }
}
```

---

Usage:

```java id="int037"
Utility.display();
```

---

Important:

```text id="int038"
Cannot Be Called
Using Object Reference
```

---

# 11. Private Methods

Introduced In:

```text id="int039"
Java 9
```

---

Purpose:

```text id="int040"
Code Reuse Inside Interface
```

---

Example:

```java id="int041"
interface Utility {

    private void helper(){

    }
}
```

---

Accessible Only:

```text id="int042"
Inside Same Interface
```

---

# 12. Functional Interfaces

Definition:

```text id="int043"
Interface Having Exactly One
Abstract Method
```

---

Example:

```java id="int044"
@FunctionalInterface

interface Calculator {

    int add(int a,int b);
}
```

---

Common Examples:

```text id="int045"
Runnable

Callable

Comparator

Predicate

Consumer

Supplier
```

---

Frequently Asked In Java 8 Interviews.

---

# 13. Lambda Expressions Foundation

Functional Interfaces Enable:

```text id="int046"
Lambda Expressions
```

---

Traditional:

```java id="int047"
Calculator calc =
new Calculator(){

    public int add(
            int a,
            int b){

        return a+b;
    }
};
```

---

Lambda:

```java id="int048"
Calculator calc =
(a,b) -> a+b;
```

---

Benefits:

```text id="int049"
Less Code

Readable

Modern Java Style
```

---

# 14. Marker Interfaces

Definition:

```text id="int050"
Interface Without Methods
```

---

Example:

```java id="int051"
Serializable
```

---

```java id="int052"
Cloneable
```

---

Purpose:

```text id="int053"
Provide Metadata To JVM
```

---

Interview Favorite.

---

# 15. Interface Variables

Example:

```java id="int054"
interface App {

    int VERSION = 1;
}
```

---

Compiler Converts To:

```java id="int055"
public static final int VERSION = 1;
```

---

Meaning:

```text id="int056"
Constant Variable
```

---

Cannot Modify.

---

# 16. Multiple Interface Implementation

Example:

```java id="int057"
interface A {

    void methodA();
}
```

---

```java id="int058"
interface B {

    void methodB();
}
```

---

```java id="int059"
class Test
implements A,B {

    public void methodA(){

    }

    public void methodB(){

    }
}
```

---

Very Common In Enterprise Projects.

---

# 17. Interface Inheritance

Interface Can Extend Interface.

Example:

```java id="int060"
interface Vehicle {

    void start();
}
```

---

```java id="int061"
interface Car
extends Vehicle {

    void openDoor();
}
```

---

Valid.

---

Keyword:

```java id="int062"
extends
```

---

# 18. Interfaces in Selenium Frameworks

Example:

```java id="int063"
public interface BrowserActions {

    void click();

    void type();
}
```

---

Implementation:

```java id="int064"
public class SeleniumActions
implements BrowserActions {

}
```

---

Benefits:

```text id="int065"
Framework Standardization

Loose Coupling

Reusable Components
```

---

# 19. Interfaces in API Frameworks

Example:

```java id="int066"
public interface PaymentService {

    void pay();
}
```

---

Implementations:

```java id="int067"
UPIPayment

CardPayment

WalletPayment
```

---

Usage:

```java id="int068"
PaymentService payment;
```

---

Flexible Architecture.

---

# 20. Real Project Scenarios

Automation Framework:

```text id="int069"
ReportManager

↓

ExtentReport

AllureReport

CustomReport
```

---

Interface:

```java id="int070"
generateReport()
```

---

API Framework:

```text id="int071"
NotificationService

↓

Email

SMS

Slack
```

---

Same Interface.

Different Implementations.

---

# 21. Common Interview Traps

### Trap 1

```text id="int072"
Can Interface Have Constructor?
```

Answer:

```text id="int073"
No
```

---

### Trap 2

```text id="int074"
Can Interface Have Variables?
```

Answer:

```text id="int075"
Yes

Constants Only
```

---

### Trap 3

```text id="int076"
Can Interface Have Methods With Body?
```

Answer:

```text id="int077"
Yes

Default & Static Methods
```

---

### Trap 4

```text id="int078"
Can Interface Be Final?
```

Answer:

```text id="int079"
No
```

---

### Trap 5

```text id="int080"
Can One Class Implement Multiple Interfaces?
```

Answer:

```text id="int081"
Yes
```

---

# 22. Top Interview Questions

### Q1 What Is Interface?

```text id="int082"
A contract that defines behavior.
```

---

### Q2 Difference Between Interface And Abstract Class?

```text id="int083"
Interface defines contracts,
abstract class provides partial implementation.
```

---

### Q3 Why Use Interfaces?

```text id="int084"
Loose coupling and flexibility.
```

---

### Q4 What Is Functional Interface?

```text id="int085"
Interface with exactly one abstract method.
```

---

### Q5 What Is Marker Interface?

```text id="int086"
Interface with no methods.
```

---

### Q6 What Is Default Method?

```text id="int087"
Method with implementation inside interface.
```

---

# 23. Revision Notes

```text id="int088"
Interface

↓

Contract

↓

implements

↓

Implementation

Multiple Inheritance

↓

Supported

Functional Interface

↓

One Abstract Method

↓

Lambda Expression

Marker Interface

↓

No Methods

Default Method

↓

Implementation Allowed
```

---

# 24. Final Cheat Sheet

```text id="int089"
Interface

↓

Defines Behavior

Class

↓

Implements Interface

Benefits

✓ Loose Coupling

✓ Reusability

✓ Scalability

✓ Multiple Inheritance

Java 8 Features

✓ Default Methods

✓ Static Methods

Java 9 Features

✓ Private Methods

Special Types

✓ Functional Interface

✓ Marker Interface
```

---

# Interview Takeaway

If interviewer asks:

```text id="int090"
Why are interfaces heavily used in Selenium frameworks?
```

Strong Answer:

```text id="int091"
Interfaces help achieve loose coupling by defining
contracts without implementation.

In Selenium frameworks, interfaces are commonly used
for reporting, browser actions, API clients, and
service layers. Different implementations can be
plugged in without changing the framework code.

Interfaces also support runtime polymorphism and
multiple inheritance, making frameworks more scalable
and maintainable.
```

---

# End of OOP Part 7

## Next Part

```text id="int092"
Part 8 → Association, Aggregation & Composition

Topics:

✓ HAS-A Relationship

✓ Association

✓ Aggregation

✓ Composition

✓ Strong vs Weak Relationships

✓ Real-Life Examples

✓ UML Understanding

✓ Selenium Framework Design

✓ API Framework Design

✓ Dependency Injection Concepts

✓ Project Scenarios

✓ Interview Questions

✓ Revision Notes
```
