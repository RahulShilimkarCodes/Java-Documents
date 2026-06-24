# Java Abstraction Master Guide – Part 3

## Abstract Methods, Method Overriding & Runtime Polymorphism

---

# Table of Contents

1. Introduction to Abstract Methods
2. Why Abstract Methods Exist
3. Syntax of Abstract Methods
4. Rules of Abstract Methods
5. Method Overriding Fundamentals
6. Abstract Method Implementation
7. Runtime Polymorphism
8. Dynamic Method Dispatch
9. JVM Internal Working
10. Virtual Method Table (V-Table)
11. Upcasting and Downcasting
12. Real Project Examples
13. Selenium Framework Examples
14. Spring Boot Examples
15. Common Coding Scenarios
16. Common Mistakes
17. Advanced Interview Questions
18. Tricky Interview Questions
19. Revision Notes
20. Cheat Sheet
21. Summary
22. Practice Questions

---

# 1. Introduction to Abstract Methods

An abstract method is a method that is declared but not implemented.

It defines:

```text
WHAT should be done
```

but does not define:

```text
HOW it should be done
```

Implementation responsibility is transferred to child classes.

---

## Syntax

```java
abstract void login();
```

Notice:

* No method body
* Ends with semicolon (;)

---

# 2. Why Abstract Methods Exist

Suppose every payment type processes payment differently.

Examples:

```text
Credit Card
UPI
Net Banking
PayPal
Wallet
```

All perform:

```java
pay()
```

But implementation differs.

Therefore parent defines:

```java
abstract class Payment {

    abstract void pay();
}
```

Child classes decide implementation.

---

# 3. Basic Example

```java
abstract class Animal {

    abstract void sound();
}
```

Child:

```java
class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

Usage:

```java
Animal animal = new Dog();
animal.sound();
```

Output:

```text
Bark
```

---

# 4. Rules of Abstract Methods

---

## Rule 1

Must be declared inside:

* Abstract Class

or

* Interface

---

Valid:

```java
abstract class Animal {

    abstract void sound();
}
```

---

Invalid:

```java
class Animal {

    abstract void sound();
}
```

Compilation Error.

---

## Rule 2

Cannot Have Body

Invalid:

```java
abstract void sound() {

}
```

Compiler Error.

---

## Rule 3

Must Be Overridden

Child class must provide implementation.

---

Invalid:

```java
abstract class Animal {

    abstract void sound();
}

class Dog extends Animal {

}
```

Compiler Error.

---

Valid:

```java
class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

---

## Rule 4

Cannot Be Private

Invalid:

```java
private abstract void login();
```

Reason:

Private methods cannot be inherited.

---

## Rule 5

Cannot Be Final

Invalid:

```java
final abstract void login();
```

Reason:

Final prevents overriding.

Abstract requires overriding.

---

## Rule 6

Cannot Be Static

Invalid:

```java
static abstract void login();
```

Reason:

Static methods belong to class.

Abstract methods require runtime overriding.

---

# 5. Method Overriding Fundamentals

Method Overriding means:

Child class provides implementation for inherited method.

---

Example:

```java
abstract class Shape {

    abstract void draw();
}
```

Child:

```java
class Circle extends Shape {

    @Override
    void draw() {

        System.out.println("Drawing Circle");
    }
}
```

---

# Why Overriding?

Without overriding:

Parent contract remains incomplete.

---

# @Override Annotation

Best practice:

```java
@Override
void draw() {

}
```

Benefits:

* Compile-time validation
* Better readability
* Prevents mistakes

---

# 6. Abstract Method Implementation Flow

Parent:

```java
abstract class Vehicle {

    abstract void start();
}
```

Child:

```java
class Car extends Vehicle {

    void start() {

        System.out.println("Car Started");
    }
}
```

Execution:

```java
Vehicle vehicle =
        new Car();

vehicle.start();
```

Output:

```text
Car Started
```

---

# Internal Flow

```text
Vehicle Reference
       |
       V
    Car Object
       |
       V
 start()
```

---

# 7. Runtime Polymorphism

One of the most important Java interview topics.

---

Definition:

Ability of a reference variable to point to different object types at runtime.

---

Example:

```java
Animal animal =
        new Dog();
```

Later:

```java
animal =
        new Cat();
```

Same reference.

Different implementations.

---

# Example

```java
abstract class Animal {

    abstract void sound();
}
```

---

Dog:

```java
class Dog extends Animal {

    void sound() {

        System.out.println("Bark");
    }
}
```

---

Cat:

```java
class Cat extends Animal {

    void sound() {

        System.out.println("Meow");
    }
}
```

---

Execution:

```java
Animal animal;

animal = new Dog();
animal.sound();

animal = new Cat();
animal.sound();
```

Output:

```text
Bark
Meow
```

---

# 8. Dynamic Method Dispatch

Frequently asked in interviews.

---

Definition:

JVM decides which overridden method to execute at runtime.

---

Example:

```java
Animal animal =
        new Dog();
```

Method Call:

```java
animal.sound();
```

Compiler sees:

```java
Animal
```

Runtime sees:

```java
Dog
```

Therefore JVM executes:

```java
Dog.sound()
```

This is Dynamic Method Dispatch.

---

# 9. JVM Internal Working

Code:

```java
Animal animal =
        new Dog();
```

---

Memory Representation

```text
STACK
-----------------

animal
  |
  |
  V

HEAP
-----------------
Dog Object
```

---

Method Call

```java
animal.sound();
```

JVM Steps:

Step 1:

Check actual object type.

```text
Dog
```

Step 2:

Locate overridden method.

```text
sound()
```

Step 3:

Execute Dog implementation.

---

# 10. Virtual Method Table (V-Table)

Advanced Interview Topic

---

Java internally maintains structures for method lookup.

Conceptually:

```text
Dog
--------------
sound()
eat()
run()
```

When:

```java
animal.sound();
```

JVM quickly finds method address.

---

Result:

Fast runtime dispatch.

---

# 11. Upcasting and Downcasting

---

## Upcasting

Child Object → Parent Reference

```java
Dog dog = new Dog();

Animal animal = dog;
```

Automatic.

Safe.

---

## Downcasting

Parent Reference → Child Reference

```java
Animal animal =
        new Dog();

Dog dog =
        (Dog) animal;
```

Requires explicit cast.

---

Risky Example

```java
Animal animal =
        new Cat();

Dog dog =
        (Dog) animal;
```

Runtime Error:

```text
ClassCastException
```

---

# 12. Real Project Example

Banking System

---

Parent:

```java
abstract class Account {

    abstract void calculateInterest();
}
```

---

Savings:

```java
class SavingsAccount
        extends Account {

    void calculateInterest() {

        System.out.println("6%");
    }
}
```

---

Current:

```java
class CurrentAccount
        extends Account {

    void calculateInterest() {

        System.out.println("4%");
    }
}
```

---

Usage:

```java
Account account =
    new SavingsAccount();

account.calculateInterest();
```

Output:

```text
6%
```

---

# 13. Selenium Framework Example

Very Important Interview Topic.

---

WebDriver:

```java
WebDriver driver;
```

Runtime:

```java
driver =
    new ChromeDriver();
```

or

```java
driver =
    new FirefoxDriver();
```

Method:

```java
driver.get(url);
```

Actual implementation decided at runtime.

---

Abstraction + Runtime Polymorphism.

---

# Example

```java
WebDriver driver =
        new ChromeDriver();
```

Compiler:

```text
WebDriver
```

Runtime:

```text
ChromeDriver
```

JVM executes ChromeDriver implementation.

---

# 14. Spring Boot Example

Repository Layer

---

Interface:

```java
public interface UserRepository {

}
```

Implementation:

```java
@Repository
public class UserRepositoryImpl
        implements UserRepository {

}
```

---

Injection:

```java
@Autowired
UserRepository repository;
```

Runtime:

Spring injects actual implementation.

---

Again:

Abstraction + Polymorphism.

---

# 15. Common Coding Scenarios

Scenario 1

---

Design Notification Service.

```java
abstract class Notification {

    abstract void send();
}
```

Implementations:

```java
EmailNotification
SMSNotification
PushNotification
```

---

Scenario 2

Payment Gateway

```java
abstract class Payment {

    abstract void process();
}
```

Implementations:

```java
UPI
CreditCard
NetBanking
```

---

# 16. Common Mistakes

---

## Mistake 1

Forgetting Override

```java
class Dog extends Animal {

}
```

Compilation Error.

---

## Mistake 2

Changing Method Signature

Parent:

```java
abstract void sound();
```

Child:

```java
void sound(String name);
```

Not overriding.

Overloading.

---

## Mistake 3

Reducing Access Modifier

Parent:

```java
public abstract void login();
```

Child:

```java
protected void login();
```

Compilation Error.

---

# 17. Advanced Interview Questions

---

## Q1

What is an abstract method?

Answer:

A method declared without implementation and implemented by child classes.

---

## Q2

Can abstract method have body?

Answer:

No.

---

## Q3

Must child class override abstract methods?

Answer:

Yes.

Unless child is abstract.

---

## Q4

Can abstract methods be static?

Answer:

No.

---

## Q5

Can abstract methods be final?

Answer:

No.

---

## Q6

Explain Runtime Polymorphism.

Answer:

Method implementation is selected at runtime based on actual object type.

---

## Q7

Explain Dynamic Method Dispatch.

Answer:

JVM determines overridden method execution during runtime.

---

## Q8

Difference between Overloading and Overriding?

Answer:

| Overloading          | Overriding     |
| -------------------- | -------------- |
| Same class           | Parent-Child   |
| Compile Time         | Runtime        |
| Different Parameters | Same Signature |

---

# 18. Tricky Interview Questions

---

## Q1

Can abstract class contain no abstract methods?

Answer:

Yes.

---

## Q2

Can abstract child class skip implementation?

Answer:

Yes.

Example:

```java
abstract class Animal {

    abstract void sound();
}

abstract class Dog extends Animal {

}
```

Valid.

---

## Q3

Can constructor call abstract method?

Answer:

Possible but dangerous.

Reason:

Child object not fully initialized.

---

## Q4

Can abstract method throw exception?

Answer:

Yes.

---

## Q5

Can abstract method be synchronized?

Answer:

No.

No implementation exists.

---

# 19. Revision Notes

```text
Abstract Method
-------------------

No Body

Must Override

Cannot Be:
-------------
private
static
final

Supports Runtime Polymorphism

Implemented by Child Class

Used In:
-------------
Frameworks
Design Patterns
Enterprise Applications
```

---

# 20. Cheat Sheet

```text
Abstract Method
=
Contract

Override Required

Runtime Dispatch

Parent Reference
Child Object

Dynamic Method Dispatch

Compiler:
Reference Type

JVM:
Actual Object Type
```

---

# 21. Summary

Abstract methods are the foundation of:

* Runtime Polymorphism
* Framework Design
* Dependency Injection
* Enterprise Architecture
* Design Patterns

Understanding abstract methods helps in mastering:

* Interfaces
* Spring Framework
* Selenium WebDriver
* REST Assured
* Microservices Architecture

Abstract methods define behavior contracts while child classes provide implementation.

---

# 22. Practice Questions

1. What is an abstract method?
2. Why are abstract methods used?
3. Can abstract methods have implementation?
4. Why can't abstract methods be private?
5. Why can't abstract methods be final?
6. Explain runtime polymorphism.
7. Explain dynamic method dispatch.
8. Explain V-Table concept.
9. Explain method overriding.
10. Difference between overriding and overloading?
11. Explain WebDriver polymorphism.
12. Explain Spring dependency injection using abstraction.
13. Explain upcasting and downcasting.
14. What happens during runtime method execution?
15. Explain JVM method lookup process.
