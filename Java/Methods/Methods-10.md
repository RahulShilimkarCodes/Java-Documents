# Java Methods Master Guide

# Part 10 - Advanced Method Concepts & Interview Mastery

---

# Table of Contents

1. Introduction
2. Method References
3. Functional Interfaces
4. Lambda Expressions
5. Method References Types
6. Fluent APIs
7. Builder Pattern
8. Advanced Method Chaining
9. Method Handles
10. JVM Method Optimizations
11. Method Inlining
12. Stack Frames Revisited
13. Real Project Framework Design
14. Selenium Framework Design
15. API Framework Design
16. Method Design Best Practices
17. Common Interview Mistakes
18. Top 25 Advanced Interview Questions
19. Quick Revision Notes
20. Final Cheat Sheet

---

# 1. Introduction

By now we have covered:

```text
Method Fundamentals

Method Calling

Parameters

Arguments

Return Types

Overloading

Overriding

Pass By Value

Varargs

Recursion

Static vs Instance Methods
```

This chapter focuses on:

```text
Modern Java

Framework Design

Performance

Enterprise Coding Practices

Advanced Interview Questions
```

---

# 2. Method References

Introduced in Java 8.

Method References provide a shorter syntax for calling methods through lambda expressions.

---

Without Method Reference

```java
List<String> names =
Arrays.asList("Java","Selenium","API");

names.forEach(name ->
System.out.println(name));
```

---

With Method Reference

```java
names.forEach(System.out::println);
```

---

Benefits

```text
Cleaner Code

Readable

Functional Programming Style
```

---

# 3. Functional Interfaces

Definition:

```text
Interface containing exactly one
abstract method.
```

---

Example:

```java
@FunctionalInterface
interface Calculator{

    int add(int a,int b);
}
```

---

Valid:

```java
Calculator c =
(a,b) -> a+b;
```

---

Common Functional Interfaces

```text
Runnable

Callable

Predicate

Consumer

Supplier

Function
```

---

Interview Question:

```text
Can Functional Interface contain
default methods?
```

Answer:

```text
Yes
```

---

# 4. Lambda Expressions

Before Java 8:

```java
Runnable r =
new Runnable(){

    public void run(){

        System.out.println("Running");
    }
};
```

---

Java 8:

```java
Runnable r =
() -> System.out.println("Running");
```

---

Structure

```java
(parameters) -> expression
```

---

Examples

```java
(a,b) -> a+b
```

---

```java
name -> name.length()
```

---

```java
() -> System.out.println("Hello")
```

---

# 5. Method Reference Types

---

## Static Method Reference

```java
ClassName::staticMethod
```

Example:

```java
Math::abs
```

---

## Instance Method Reference

```java
object::method
```

Example:

```java
System.out::println
```

---

## Arbitrary Object Method

```java
String::toUpperCase
```

---

## Constructor Reference

```java
Employee::new
```

---

Interview Favorite.

---

# 6. Fluent APIs

Definition:

```text
Methods returning current object
to enable chaining.
```

---

Example:

```java
builder
.setName("Rahul")
.setAge(30)
.setCity("Mumbai");
```

---

Advantages:

```text
Readable

Compact

Professional Design
```

---

# 7. Builder Pattern

Extremely Important For Interviews.

Traditional:

```java
Employee e =
new Employee(
1,
"Rahul",
30,
"Mumbai",
"QA"
);
```

Hard to read.

---

Builder Pattern:

```java
Employee e =
Employee.builder()
.name("Rahul")
.age(30)
.city("Mumbai")
.build();
```

---

Benefits:

```text
Readable

Immutable Objects

Flexible Design
```

---

Used heavily in:

```text
Lombok

Spring Boot

REST APIs

Enterprise Applications
```

---

# 8. Advanced Method Chaining

Example:

```java
String result =
" java "
.trim()
.toUpperCase()
.substring(1);
```

---

Execution:

```text
trim()

↓

returns String

↓

toUpperCase()

↓

returns String

↓

substring()
```

---

Why Works?

```text
Every Method Returns Object
```

---

Selenium Example:

```java
driver.manage()
      .window()
      .maximize();
```

---

# 9. Method Handles

Advanced JVM Topic.

Package:

```java
java.lang.invoke
```

---

Purpose:

```text
High Performance Method Access
```

---

Traditional Reflection:

```java
Method method =
Employee.class
.getMethod("login");
```

---

Method Handle:

```java
MethodHandle handle
```

provides faster execution.

---

Interview Level:

```text
Advanced Java Developers
```

---

# 10. JVM Method Optimizations

Modern JVM performs:

```text
Inlining

Dead Code Elimination

Escape Analysis

Loop Optimization
```

---

Goal:

```text
Reduce Method Call Cost
```

---

Interview Point:

```text
JVM optimizes methods aggressively.
```

---

# 11. Method Inlining

Frequently Asked.

Definition:

```text
JVM replaces method call
with actual method body.
```

---

Example:

```java
public int getValue(){

    return 10;
}
```

---

Instead of:

```java
getValue();
```

JVM may directly use:

```java
10
```

---

Benefits:

```text
Faster Execution

Reduced Stack Calls
```

---

# 12. Stack Frames Revisited

Every method call creates:

```text
Stack Frame
```

Contains:

```text
Parameters

Local Variables

Return Address

Intermediate Values
```

---

Example:

```java
add(10,20);
```

Stack Frame:

```text
a = 10

b = 20
```

---

After completion:

```text
Frame Removed
```

---

# 13. Real Project Framework Design

Large Framework Structure:

```text
Tests

↓

Page Objects

↓

Services

↓

Utilities

↓

Core Engine
```

---

Method Design:

```java
login()

logout()

searchProduct()

captureScreenshot()

generateReport()
```

---

Rules:

```text
Single Responsibility

Reusable

Small Methods

Clear Names
```

---

# 14. Selenium Framework Design

Page Object Example:

```java
public LoginPage enterUsername(){

}
```

---

```java
public LoginPage enterPassword(){

}
```

---

```java
public HomePage clickLogin(){

}
```

---

Method Chaining:

```java
page.enterUsername()
    .enterPassword()
    .clickLogin();
```

---

Professional Framework Design.

---

# 15. API Framework Design

Service Layer:

```java
createUser()

updateUser()

deleteUser()

getUser()
```

---

Utility Layer:

```java
readJson()

generateToken()

validateResponse()
```

---

DTO Builder:

```java
User.builder()
    .name("Rahul")
    .age(30)
    .build();
```

---

Common Enterprise Design.

---

# 16. Method Design Best Practices

---

## Keep Methods Small

Bad:

```java
loginAndSearchAndCheckoutAndReport();
```

---

Good:

```java
login();

search();

checkout();

generateReport();
```

---

## Meaningful Names

Bad:

```java
abc();
```

---

Good:

```java
captureScreenshot();
```

---

## Avoid Long Parameter Lists

Bad:

```java
createUser(
name,
age,
city,
email,
phone,
salary,
department
);
```

---

Use Builder Pattern.

---

# 17. Common Interview Mistakes

---

## Mistake 1

Confusing Lambda With Anonymous Class

---

## Mistake 2

Thinking Method References Are Faster

Main advantage:

```text
Readability
```

---

## Mistake 3

Using Huge Methods

Bad design.

---

## Mistake 4

Ignoring Reusability

Framework methods should be reusable.

---

# 18. Top 25 Advanced Interview Questions

---

## Q1 What is Method Reference?

```text
Compact syntax for referring to methods.
```

---

## Q2 What is Functional Interface?

```text
Interface with exactly one abstract method.
```

---

## Q3 What is Lambda Expression?

```text
Anonymous function implementation.
```

---

## Q4 What is Fluent API?

```text
Method chaining based API design.
```

---

## Q5 What is Builder Pattern?

```text
Object creation pattern using chained methods.
```

---

## Q6 Why Use Builder Pattern?

```text
Readable

Maintainable

Immutable Objects
```

---

## Q7 What is Method Inlining?

```text
JVM optimization replacing method call
with method body.
```

---

## Q8 What is Method Handle?

```text
High performance method access API.
```

---

## Q9 Why Use Functional Interfaces?

```text
Support Lambda Expressions.
```

---

## Q10 Why Is Method Chaining Possible?

```text
Methods return objects.
```

---

## Q11 Difference Between Lambda and Method Reference?

```text
Lambda

() -> method()

Method Reference

Class::method
```

---

## Q12 What Design Pattern Uses Method Chaining?

```text
Builder Pattern
```

---

## Q13 What Is a Fluent Interface?

```text
Interface designed around chained calls.
```

---

## Q14 Can Constructors Be Referenced?

```text
Yes

ClassName::new
```

---

## Q15 What Is the Purpose of JVM Inlining?

```text
Reduce method call overhead.
```

---

(Questions 16–25)

```text
Focus on:
Polymorphism
Method Design
JVM Internals
Framework Architecture
Performance Optimization
```

---

# 19. Quick Revision Notes

```text
Method Reference

Class::method

Lambda

() -> {}

Functional Interface

One Abstract Method

Builder Pattern

Method Chaining

Fluent API

Returns Current Object

Method Handle

High Performance Invocation

Method Inlining

JVM Optimization

Framework Design

Small Reusable Methods
```

---

# 20. Final Cheat Sheet

```text
Advanced Methods

Lambda

(a,b)->a+b

Method Reference

System.out::println

Builder

User.builder()
    .name("Rahul")
    .build()

Fluent API

object.method1()
      .method2()

JVM Optimizations

Inlining

Dead Code Removal

Escape Analysis

Best Practice

Small Methods

Reusable Methods

Meaningful Names

Single Responsibility
```

---

# Interview Takeaway

If interviewer asks:

```text
How are methods used in real automation frameworks?
```

Strong Answer:

```text
Methods form the foundation of automation frameworks.

Page Object Models expose business actions through methods
such as login(), searchProduct(), and checkout().

Utility classes provide reusable static methods like
captureScreenshot(), generateReport(), and readProperty().

Modern frameworks also use method chaining,
builder patterns, functional interfaces,
and lambda expressions to improve readability,
maintainability, and scalability.

Well-designed methods make automation frameworks
modular, reusable, and easy to maintain.
```

---

# End of Part 10

## Next Part

Part 11 → Java Methods Complete Revision & Interview Handbook

Topics:

* Complete Methods Revision
* JVM Internals Summary
* Memory Diagrams
* Overloading vs Overriding
* Static vs Instance
* Pass By Value
* Recursion
* Varargs
* Top 100 Interview Questions
* Framework-Based Scenarios
* Rapid Revision Notes
* One-Day Interview Preparation Guide
