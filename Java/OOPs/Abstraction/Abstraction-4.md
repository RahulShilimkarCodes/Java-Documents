# Java Abstraction Master Guide – Part 4

## Interfaces Fundamentals (Interview Preparation)

---

# Table of Contents

1. Introduction to Interfaces
2. Why Interfaces Were Introduced
3. What Problem Do Interfaces Solve?
4. Interface Syntax
5. Rules of Interfaces
6. Interface Variables
7. Interface Methods
8. Multiple Interface Implementation
9. Multiple Inheritance Problem
10. Diamond Problem
11. Interface Memory Model
12. JVM Internal Working
13. Interface vs Abstract Class
14. Interface vs Class
15. Real Project Examples
16. Selenium Framework Usage
17. Spring Framework Usage
18. Design Patterns Using Interfaces
19. Common Mistakes
20. Advanced Interview Questions
21. Tricky Interview Questions
22. Revision Notes
23. Cheat Sheet
24. Summary
25. Practice Questions

---

# 1. Introduction to Interfaces

An Interface is a blueprint of behavior.

It defines:

```text id="int001"
WHAT should be done
```

but not

```text id="int002"
HOW it should be done
```

The implementation is provided by implementing classes.

---

## Real World Example

Think about a TV Remote.

The remote exposes:

```text id="int003"
Power Button
Volume Button
Channel Button
```

User knows:

```text id="int004"
What the button does
```

User does NOT know:

```text id="int005"
Internal circuitry
Signal transmission
Hardware processing
```

This is abstraction.

---

# 2. Why Interfaces Were Introduced

Before interfaces, developers relied heavily on inheritance.

Example:

```java id="int006"
class Animal {

}
```

Problem:

Java does not support multiple inheritance using classes.

Example:

```java id="int007"
class A {

}

class B {

}

class C extends A, B {

}
```

Compilation Error.

Java introduced Interfaces to solve this problem.

---

# 3. What Problem Do Interfaces Solve?

Interfaces help achieve:

* Abstraction
* Loose Coupling
* Multiple Inheritance of Behavior
* Framework Flexibility
* Plug-and-Play Architecture

---

Example:

```java id="int008"
interface Payment {

    void pay();
}
```

Implementations:

```java id="int009"
UPIPayment
CreditCardPayment
NetBankingPayment
```

Consumer only knows:

```java id="int010"
payment.pay();
```

Implementation remains hidden.

---

# 4. Interface Syntax

Basic Interface

```java id="int011"
interface Animal {

    void sound();
}
```

Implementation:

```java id="int012"
class Dog implements Animal {

    public void sound() {

        System.out.println("Bark");
    }
}
```

Usage:

```java id="int013"
Animal animal =
        new Dog();

animal.sound();
```

Output:

```text id="int014"
Bark
```

---

# 5. Rules of Interfaces

---

## Rule 1

Interface uses keyword:

```java id="int015"
interface
```

Example:

```java id="int016"
interface Vehicle {

}
```

---

## Rule 2

Cannot create object directly.

Invalid:

```java id="int017"
Vehicle vehicle =
        new Vehicle();
```

Compilation Error.

---

## Rule 3

Class must implement interface.

Example:

```java id="int018"
class Car implements Vehicle {

}
```

---

## Rule 4

Implementing class must implement all methods.

Example:

```java id="int019"
interface Animal {

    void sound();
}
```

---

Invalid:

```java id="int020"
class Dog implements Animal {

}
```

Compilation Error.

---

Valid:

```java id="int021"
class Dog implements Animal {

    public void sound() {

    }
}
```

---

# 6. Interface Variables

Many interviewers ask:

Can interfaces have variables?

Answer:

Yes.

---

Example:

```java id="int022"
interface Constants {

    int MAX_VALUE = 100;
}
```

Java automatically converts it to:

```java id="int023"
public static final int MAX_VALUE = 100;
```

---

Meaning:

```text id="int024"
public
static
final
```

are added automatically.

---

Usage:

```java id="int025"
System.out.println(
        Constants.MAX_VALUE);
```

---

# 7. Interface Methods

Before Java 8:

All methods were:

```java id="int026"
public abstract
```

automatically.

Example:

```java id="int027"
interface Vehicle {

    void start();
}
```

Compiler converts:

```java id="int028"
public abstract void start();
```

---

# 8. Multiple Interface Implementation

One class can implement multiple interfaces.

---

Example:

```java id="int029"
interface Flyable {

    void fly();
}
```

---

```java id="int030"
interface Swimmable {

    void swim();
}
```

---

Implementation:

```java id="int031"
class Duck
implements Flyable,
           Swimmable {

    public void fly() {

    }

    public void swim() {

    }
}
```

Valid.

---

# 9. Multiple Inheritance Problem

Suppose:

```java id="int032"
class A {

    void show() {

    }
}
```

---

```java id="int033"
class B {

    void show() {

    }
}
```

---

Now:

```java id="int034"
class C extends A, B {

}
```

Question:

Which show() method should be inherited?

Java cannot decide.

This is Multiple Inheritance Problem.

---

Solution:

Interfaces.

---

# 10. Diamond Problem

Advanced Interview Topic.

---

Diagram:

```text id="int035"
        Animal
         /  \
        /    \
      Bird  Mammal
        \    /
         \  /
         Bat
```

Suppose both parent classes provide:

```java id="int036"
void move();
```

Which implementation should Bat inherit?

Confusion.

This is Diamond Problem.

---

Java avoids this by:

```text id="int037"
No Multiple Class Inheritance
```

---

Interfaces solve this problem.

---

# 11. Interface Memory Model

Example:

```java id="int038"
Animal animal =
        new Dog();
```

Memory:

```text id="int039"
STACK

animal
  |
  |
  V

HEAP

Dog Object
```

---

Reference Type:

```java id="int040"
Animal
```

Object Type:

```java id="int041"
Dog
```

---

# 12. JVM Internal Working

Code:

```java id="int042"
Animal animal =
        new Dog();

animal.sound();
```

---

Compiler Checks:

```text id="int043"
Does Animal contain sound()?
```

Yes.

Compilation successful.

---

Runtime Checks:

```text id="int044"
Actual object?
```

Dog.

JVM executes:

```java id="int045"
Dog.sound();
```

This is runtime polymorphism.

---

# 13. Interface vs Abstract Class

Most Asked Interview Question

---

| Feature              | Interface  | Abstract Class |
| -------------------- | ---------- | -------------- |
| Constructor          | No         | Yes            |
| Instance Variables   | No         | Yes            |
| Multiple Inheritance | Yes        | No             |
| Object Creation      | No         | No             |
| Abstraction          | Full       | Partial        |
| Inheritance Keyword  | implements | extends        |

---

# When to Use Interface?

Use when:

```text id="int046"
Behavior Contract
Multiple Implementations
Loose Coupling
Framework Design
```

---

# When to Use Abstract Class?

Use when:

```text id="int047"
Shared Logic
Common State
Reusable Methods
```

---

# 14. Interface vs Class

| Feature          | Interface   | Class    |
| ---------------- | ----------- | -------- |
| Object Creation  | No          | Yes      |
| Constructor      | No          | Yes      |
| Abstract Methods | Yes         | Optional |
| State Storage    | Limited     | Full     |
| Instantiation    | Not Allowed | Allowed  |

---

# 15. Real Project Example

Payment Gateway

---

Interface:

```java id="int048"
interface Payment {

    void pay();
}
```

---

Implementations:

```java id="int049"
class UPIPayment
implements Payment {

    public void pay() {

    }
}
```

---

```java id="int050"
class CreditCardPayment
implements Payment {

    public void pay() {

    }
}
```

---

Usage:

```java id="int051"
Payment payment =
        new UPIPayment();

payment.pay();
```

---

Benefits:

```text id="int052"
Loose Coupling
Scalability
Maintainability
```

---

# 16. Selenium Framework Usage

Extremely Important Interview Topic.

---

WebDriver is an Interface.

```java id="int053"
WebDriver driver;
```

Implementations:

```java id="int054"
ChromeDriver
FirefoxDriver
EdgeDriver
SafariDriver
RemoteWebDriver
```

---

Usage:

```java id="int055"
WebDriver driver =
        new ChromeDriver();
```

Compiler sees:

```text id="int056"
WebDriver
```

Runtime sees:

```text id="int057"
ChromeDriver
```

---

This is:

```text id="int058"
Abstraction
Polymorphism
Interface Usage
```

---

# 17. Spring Framework Usage

Repository Pattern

---

Interface:

```java id="int059"
public interface UserRepository {

}
```

Implementation:

```java id="int060"
@Repository
public class UserRepositoryImpl
implements UserRepository {

}
```

---

Injection:

```java id="int061"
@Autowired
UserRepository repository;
```

Spring injects actual implementation.

Loose coupling achieved.

---

# 18. Design Patterns Using Interfaces

---

## Strategy Pattern

Interface:

```java id="int062"
interface PaymentStrategy {

    void pay();
}
```

Implementations:

```java id="int063"
UPIPayment
CardPayment
WalletPayment
```

Runtime selection.

---

## Factory Pattern

Return interface.

Hide implementation.

Example:

```java id="int064"
Payment payment =
        PaymentFactory
        .getPayment();
```

---

# 19. Common Mistakes

---

## Mistake 1

Trying to create interface object.

```java id="int065"
new Animal();
```

Invalid.

---

## Mistake 2

Forgetting method implementation.

```java id="int066"
class Dog implements Animal {

}
```

Compiler Error.

---

## Mistake 3

Modifying interface variable.

```java id="int067"
MAX_VALUE = 200;
```

Invalid.

Because variable is final.

---

# 20. Advanced Interview Questions

---

## Q1

What is an Interface?

Answer:

A contract that defines behavior without implementation.

---

## Q2

Can interface have variables?

Answer:

Yes.

All variables are:

```java id="int068"
public static final
```

---

## Q3

Can interface have constructors?

Answer:

No.

---

## Q4

Can interface be instantiated?

Answer:

No.

---

## Q5

Can a class implement multiple interfaces?

Answer:

Yes.

---

## Q6

Why are interfaces used?

Answer:

To achieve abstraction, loose coupling, and multiple inheritance of behavior.

---

## Q7

Explain WebDriver architecture using interfaces.

Answer:

WebDriver is an interface.

ChromeDriver, FirefoxDriver etc. implement WebDriver.

---

# 21. Tricky Interview Questions

---

## Q1

Can interface extend another interface?

Answer:

Yes.

Example:

```java id="int069"
interface A {

}

interface B extends A {

}
```

---

## Q2

Can interface implement another interface?

Answer:

No.

Interfaces extend interfaces.

Classes implement interfaces.

---

## Q3

Can abstract class implement interface?

Answer:

Yes.

Example:

```java id="int070"
abstract class Employee
implements Serializable {

}
```

---

## Q4

Can interface contain static methods?

Answer:

Yes (Java 8+).

Covered in Part 5.

---

## Q5

Can interface contain private methods?

Answer:

Yes (Java 9+).

Covered in Part 6.

---

# 22. Revision Notes

```text id="int071"
Interface
------------
Contract

No Object Creation

Supports Multiple Inheritance

Methods:
-------------
public abstract

Variables:
-------------
public static final

Used For:
-------------
Loose Coupling
Framework Design
Dependency Injection
```

---

# 23. Cheat Sheet

```text id="int072"
Interface = Behavior Contract

implements keyword

No Constructor

No Instance Variables

Multiple Interfaces Allowed

WebDriver = Interface

Repository Pattern = Interface

Strategy Pattern = Interface
```

---

# 24. Summary

Interfaces are one of the most important features in Java.

They provide:

* Abstraction
* Loose Coupling
* Extensibility
* Multiple Inheritance of Behavior
* Better Framework Design

Used extensively in:

* Selenium
* Spring Boot
* REST Assured
* Design Patterns
* Enterprise Applications

Mastering interfaces is essential for automation testing and Java developer interviews.

---

# 25. Practice Questions

1. What is an Interface?
2. Why were Interfaces introduced?
3. Difference between Interface and Abstract Class?
4. Can interfaces have variables?
5. Can interfaces have constructors?
6. What is Multiple Inheritance Problem?
7. What is Diamond Problem?
8. Explain WebDriver using Interfaces.
9. Explain Repository Pattern using Interfaces.
10. Explain runtime polymorphism with interfaces.
11. Why are interface variables final?
12. Can interfaces extend interfaces?
13. Can interfaces implement interfaces?
14. Explain Strategy Pattern using interfaces.
15. When should you choose an interface over an abstract class?
