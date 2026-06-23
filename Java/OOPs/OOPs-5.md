# Java OOP Master Guide

# Part 5 - Polymorphism Deep Dive

---

# Table of Contents

1. What is Polymorphism?
2. Why Polymorphism is Needed
3. Types of Polymorphism
4. Compile-Time Polymorphism
5. Method Overloading
6. Rules of Method Overloading
7. Runtime Polymorphism
8. Method Overriding
9. Rules of Method Overriding
10. Dynamic Method Dispatch
11. Upcasting
12. Downcasting
13. instanceof Operator
14. Covariant Return Types
15. Polymorphism and Constructors
16. Polymorphism in Selenium Frameworks
17. Polymorphism in API Frameworks
18. Real Project Scenarios
19. Advantages of Polymorphism
20. Common Interview Traps
21. Top Interview Questions
22. Revision Notes
23. Final Cheat Sheet

---

# 1. What is Polymorphism?

Polymorphism is one of the four pillars of OOP.

Definition:

```text id="poly001"
Polymorphism means one entity
existing in multiple forms.
```

---

Word Breakdown:

```text id="poly002"
Poly

↓

Many

Morph

↓

Forms
```

---

Simple Definition:

```text id="poly003"
One Interface

Multiple Implementations
```

---

Real Example:

```text id="poly004"
Payment

↓

Credit Card

UPI

Net Banking

Wallet
```

---

Same Action:

```java id="poly005"
pay();
```

Different Behaviors.

---

# 2. Why Polymorphism is Needed

Without Polymorphism:

```java id="poly006"
creditCardPay();

upiPay();

walletPay();
```

---

Problem:

```text id="poly007"
Too Many Methods

Poor Flexibility

Hard Maintenance
```

---

With Polymorphism:

```java id="poly008"
pay();
```

---

Benefits:

```text id="poly009"
Loose Coupling

Extensibility

Cleaner Design
```

---

# 3. Types of Polymorphism

Java Supports:

```text id="poly010"
1. Compile-Time Polymorphism

2. Runtime Polymorphism
```

---

Also Known As:

| Type         | Alternative Name     |
| ------------ | -------------------- |
| Compile-Time | Static Polymorphism  |
| Runtime      | Dynamic Polymorphism |

---

Interview Favorite.

---

# 4. Compile-Time Polymorphism

Achieved Through:

```text id="poly011"
Method Overloading
```

---

Compiler decides:

```text id="poly012"
Which Method To Execute
```

During:

```text id="poly013"
Compilation
```

---

Example:

```java id="poly014"
class Calculator {

    int add(int a,int b){

        return a+b;
    }

    int add(int a,int b,int c){

        return a+b+c;
    }
}
```

---

Method Selected At:

```text id="poly015"
Compile Time
```

---

# 5. Method Overloading

Definition:

```text id="poly016"
Multiple methods having the same name
but different parameter lists.
```

---

Example:

```java id="poly017"
class Employee {

    void login(){

    }

    void login(String user){

    }

    void login(String user,
               String pass){

    }
}
```

---

Valid Overloading:

```text id="poly018"
Different Number Of Parameters

Different Types

Different Order
```

---

# 6. Rules of Method Overloading

Valid:

```java id="poly019"
void test(int a)
```

---

```java id="poly020"
void test(int a,int b)
```

---

Valid:

```java id="poly021"
void test(int a)
```

---

```java id="poly022"
void test(String a)
```

---

Invalid:

```java id="poly023"
int test(int a)
```

---

```java id="poly024"
double test(int a)
```

---

Reason:

```text id="poly025"
Return Type Alone Cannot Differentiate Methods
```

---

# 7. Runtime Polymorphism

Achieved Through:

```text id="poly026"
Method Overriding
```

---

Decision Made At:

```text id="poly027"
Runtime
```

---

Parent:

```java id="poly028"
class Animal {

    void sound(){

        System.out.println("Animal Sound");
    }
}
```

---

Child:

```java id="poly029"
class Dog extends Animal {

    void sound(){

        System.out.println("Bark");
    }
}
```

---

Usage:

```java id="poly030"
Animal a = new Dog();

a.sound();
```

Output:

```text id="poly031"
Bark
```

---

# 8. Method Overriding

Definition:

```text id="poly032"
Child class provides its own implementation
of a parent method.
```

---

Example:

```java id="poly033"
class Animal {

    void eat(){

    }
}
```

---

```java id="poly034"
class Dog extends Animal {

    @Override

    void eat(){

        System.out.println("Dog Eating");
    }
}
```

---

Output:

```text id="poly035"
Dog Eating
```

---

# 9. Rules of Method Overriding

Rule 1

```text id="poly036"
Method Name Must Be Same
```

---

Rule 2

```text id="poly037"
Parameters Must Match
```

---

Rule 3

```text id="poly038"
Inheritance Required
```

---

Rule 4

```text id="poly039"
Access Modifier Cannot Be More Restrictive
```

---

Example:

Valid:

```java id="poly040"
protected
```

↓

```java id="poly041"
public
```

---

Invalid:

```java id="poly042"
public
```

↓

```java id="poly043"
private
```

---

# 10. Dynamic Method Dispatch

Most Important Runtime Polymorphism Concept.

Example:

```java id="poly044"
Animal animal =
new Dog();
```

---

Reference Type:

```text id="poly045"
Animal
```

---

Object Type:

```text id="poly046"
Dog
```

---

Method Call:

```java id="poly047"
animal.sound();
```

---

JVM Chooses:

```text id="poly048"
Dog Version
```

At Runtime.

---

Called:

```text id="poly049"
Dynamic Method Dispatch
```

---

# 11. Upcasting

Child Object Stored In Parent Reference.

Example:

```java id="poly050"
Dog dog =
new Dog();
```

---

Upcasting:

```java id="poly051"
Animal animal = dog;
```

---

Or:

```java id="poly052"
Animal animal =
new Dog();
```

---

Benefits:

```text id="poly053"
Loose Coupling

Runtime Flexibility
```

---

Most Frameworks Use Upcasting.

---

# 12. Downcasting

Parent Reference Converted Back To Child.

Example:

```java id="poly054"
Animal animal =
new Dog();
```

---

```java id="poly055"
Dog dog =
(Dog) animal;
```

---

Required When:

```text id="poly056"
Child Specific Methods Needed
```

---

Danger:

```java id="poly057"
Animal animal =
new Animal();

Dog dog =
(Dog) animal;
```

---

Runtime Error:

```text id="poly058"
ClassCastException
```

---

# 13. instanceof Operator

Used Before Downcasting.

Example:

```java id="poly059"
if(animal instanceof Dog){

}
```

---

Purpose:

```text id="poly060"
Safe Casting
```

---

Real Usage:

```java id="poly061"
if(driver instanceof ChromeDriver){

}
```

---

Frequently Used In Frameworks.

---

# 14. Covariant Return Types

Advanced Interview Topic.

Parent:

```java id="poly062"
class Animal {

}
```

---

Child:

```java id="poly063"
class Dog extends Animal {

}
```

---

Parent Method:

```java id="poly064"
Animal getObject(){

}
```

---

Override:

```java id="poly065"
Dog getObject(){

}
```

---

Allowed.

---

Called:

```text id="poly066"
Covariant Return Type
```

---

# 15. Polymorphism and Constructors

Interview Question:

```text id="poly067"
Can Constructors Be Overridden?
```

Answer:

```text id="poly068"
No
```

---

Reason:

```text id="poly069"
Constructors Are Not Inherited
```

---

Can Constructors Be Overloaded?

```text id="poly070"
Yes
```

---

Very Common Interview Question.

---

# 16. Polymorphism in Selenium Frameworks

Example:

```java id="poly071"
WebDriver driver =
new ChromeDriver();
```

---

Reference Type:

```text id="poly072"
WebDriver
```

---

Object Type:

```text id="poly073"
ChromeDriver
```

---

Runtime Polymorphism.

---

Can Easily Replace:

```java id="poly074"
new FirefoxDriver()
```

---

Without Changing Code.

---

Framework Benefit:

```text id="poly075"
Browser Independence
```

---

# 17. Polymorphism in API Frameworks

Interface:

```java id="poly076"
PaymentService
```

---

Implementations:

```java id="poly077"
UPIPayment

CardPayment

WalletPayment
```

---

Usage:

```java id="poly078"
PaymentService payment =
new UPIPayment();
```

---

Benefits:

```text id="poly079"
Flexible Design

Extensible Services
```

---

# 18. Real Project Scenarios

Automation Framework:

```java id="poly080"
WebDriver driver;
```

---

Depending On Config:

```java id="poly081"
ChromeDriver

FirefoxDriver

EdgeDriver
```

---

Same Reference.

Different Behavior.

---

API Framework:

```java id="poly082"
NotificationService service;
```

---

Implementations:

```java id="poly083"
EmailService

SMSService

SlackService
```

---

Same Method:

```java id="poly084"
sendNotification();
```

---

Different Execution.

---

# 19. Advantages of Polymorphism

```text id="poly085"
Flexibility

Loose Coupling

Scalability

Maintainability

Extensibility
```

---

Enterprise Benefit:

```text id="poly086"
Easy Replacement Of Components
```

---

# 20. Common Interview Traps

### Trap 1

```text id="poly087"
Can Constructors Be Overridden?
```

Answer:

```text id="poly088"
No
```

---

### Trap 2

```text id="poly089"
Can Static Methods Be Overridden?
```

Answer:

```text id="poly090"
No
```

---

### Trap 3

```text id="poly091"
Can Private Methods Be Overridden?
```

Answer:

```text id="poly092"
No
```

---

### Trap 4

```text id="poly093"
Can Return Type Alone Overload Methods?
```

Answer:

```text id="poly094"
No
```

---

### Trap 5

```text id="poly095"
Is WebDriver driver = new ChromeDriver()
Polymorphism?
```

Answer:

```text id="poly096"
Yes
```

---

# 21. Top Interview Questions

### Q1 What Is Polymorphism?

```text id="poly097"
One entity existing in multiple forms.
```

---

### Q2 Types Of Polymorphism?

```text id="poly098"
Compile-Time

Runtime
```

---

### Q3 What Is Method Overloading?

```text id="poly099"
Same method name with different parameters.
```

---

### Q4 What Is Method Overriding?

```text id="poly100"
Child provides its own implementation of parent method.
```

---

### Q5 What Is Dynamic Method Dispatch?

```text id="poly101"
Runtime selection of overridden method.
```

---

### Q6 What Is Upcasting?

```text id="poly102"
Child object stored in parent reference.
```

---

### Q7 What Is Downcasting?

```text id="poly103"
Converting parent reference back to child.
```

---

# 22. Revision Notes

```text id="poly104"
Polymorphism

↓

Many Forms

Types

↓

Compile-Time

Runtime

Compile-Time

↓

Method Overloading

Runtime

↓

Method Overriding

↓

Dynamic Method Dispatch

↓

Upcasting

↓

Downcasting
```

---

# 23. Final Cheat Sheet

```text id="poly105"
Method Overloading

↓

Compile-Time

Method Overriding

↓

Runtime

Animal a = new Dog()

↓

Upcasting

a.sound()

↓

Dog Version Executes

↓

Dynamic Dispatch

instanceof

↓

Safe Downcasting

Framework Example

WebDriver driver =
new ChromeDriver();
```

---

# Interview Takeaway

If interviewer asks:

```text id="poly106"
Explain Polymorphism with Selenium Example.
```

Strong Answer:

```text id="poly107"
Polymorphism allows one interface to represent
multiple implementations.

In Selenium, WebDriver driver = new ChromeDriver()
is a classic example of runtime polymorphism.

The reference type is WebDriver while the actual
object is ChromeDriver. This allows switching
between ChromeDriver, FirefoxDriver and EdgeDriver
without changing the framework code.

Compile-time polymorphism is achieved through
method overloading, while runtime polymorphism
is achieved through method overriding and
dynamic method dispatch.
```

---

# End of OOP Part 5

## Next Part

```text id="poly108"
Part 6 → Abstraction Deep Dive

Topics:

✓ What Is Abstraction

✓ Abstract Classes

✓ Abstract Methods

✓ Concrete Methods

✓ Rules Of Abstract Classes

✓ Partial Abstraction

✓ 100% Abstraction

✓ Abstract Class vs Interface

✓ Template Design Pattern

✓ Selenium Examples

✓ API Examples

✓ Framework Design

✓ Interview Questions

✓ Revision Notes
```
