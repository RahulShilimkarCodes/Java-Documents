# Java-Classes-and-Objects-Master-Guide-Part-8.md

# Java Classes and Objects Master Guide

## Part 8 – Association, Aggregation, Composition & Object Relationships

---

# Table of Contents

1. Introduction to Object Relationships
2. Why Relationships are Important
3. IS-A Relationship
4. HAS-A Relationship
5. Association
6. Types of Association
7. Aggregation
8. Composition
9. Association vs Aggregation vs Composition
10. Dependency Relationship
11. Dependency Injection Basics
12. Real Framework Design
13. Selenium Framework Architecture
14. Spring Framework Connection
15. JVM Perspective
16. Interview Questions
17. Revision Notes

---

# Introduction

In real-world applications, classes rarely exist alone.

Consider:

```text
Employee

Address

Department

Company

Project
```

Question:

```text
How Do These Objects Communicate?

How Are They Connected?

How Does One Object Use Another?
```

The answer is:

```text
Object Relationships
```

Understanding object relationships is extremely important because:

* OOP Design depends on them.
* Selenium Frameworks use them heavily.
* Spring Framework is built around them.
* Most design pattern questions are based on relationships.

---

# Why Relationships Matter?

Imagine a Selenium Framework.

Classes:

```text
LoginPage

HomePage

DriverFactory

ConfigReader

ReportManager
```

These classes must interact.

Without relationships:

```text
Independent Classes

↓

No Communication

↓

No Framework
```

Relationships enable:

```text
Code Reuse

Maintainability

Loose Coupling

Scalability
```

---

# 1. IS-A Relationship

## Definition

IS-A represents inheritance.

Example:

```text
Dog IS-A Animal

Car IS-A Vehicle

Manager IS-A Employee
```

---

# Java Example

```java
class Animal {

}

class Dog
extends Animal {

}
```

Relationship:

```text
Dog

↓

IS-A

↓

Animal
```

---

# Why IS-A?

Allows:

```text
Inheritance

Polymorphism

Code Reuse
```

---

# Interview Question

Which keyword creates IS-A relationship?

Answer:

```java
extends
```

and

```java
implements
```

---

# Real Example

```java
class Employee {

}

class Manager
extends Employee {

}
```

Manager automatically gets:

```text
Variables

Methods

Behavior
```

from Employee.

---

# 2. HAS-A Relationship

## Definition

One class contains another class object.

Example:

```text
Employee HAS-A Address

Car HAS-A Engine

Company HAS-A Department
```

---

# Java Example

```java
class Address {

}

class Employee {

    Address address;

}
```

Relationship:

```text
Employee

↓

HAS-A

↓

Address
```

---

# Why HAS-A?

Used for:

```text
Composition

Aggregation

Object Collaboration
```

---

# Real World Example

```text
Laptop HAS-A Processor

Laptop HAS-A RAM

Laptop HAS-A Battery
```

---

# 3. Association

## Definition

Association represents a relationship between two independent objects.

Example:

```text
Teacher ↔ Student

Doctor ↔ Patient

Customer ↔ Order
```

---

# Characteristics

```text
Objects Are Independent

Can Exist Separately

Uses Object References
```

---

# Java Example

```java
class Teacher {

    String name;

}

class Student {

    Teacher teacher;

}
```

---

# Relationship Diagram

```text
Student

↓

Teacher
```

Both can exist independently.

---

# Key Point

If Teacher object is deleted:

```text
Student

Still Exists
```

---

# Association Example

```java
Teacher teacher =
new Teacher();

Student student =
new Student();

student.teacher =
teacher;
```

---

# Types of Association

```text
One-To-One

One-To-Many

Many-To-One

Many-To-Many
```

---

# One-To-One

Example:

```text
Person ↔ Passport
```

---

# One-To-Many

Example:

```text
Department

↓

Many Employees
```

---

# Many-To-One

Example:

```text
Many Employees

↓

One Department
```

---

# Many-To-Many

Example:

```text
Students

↓

Courses

↑

Multiple Students
```

---

# 4. Aggregation

## Definition

Special type of Association.

Represents:

```text
Weak HAS-A Relationship
```

---

# Key Characteristic

Contained object can exist independently.

Example:

```text
Department HAS-A Employee
```

Even if:

```text
Department Removed
```

Employee can still exist.

---

# Java Example

```java
class Employee {

}

class Department {

    Employee employee;

}
```

---

# Memory Representation

```text
Department
     |
     |
     V
Employee
```

Employee lives independently.

---

# Real World Example

```text
School HAS-A Teacher

University HAS-A Professor

Company HAS-A Employee
```

Remove company:

```text
Employee Still Exists
```

---

# Why Called Weak Relationship?

Because lifecycle is independent.

---

# Aggregation Diagram

```text
Department

◇──── Employee
```

(Hollow Diamond)

---

# 5. Composition

## Definition

Strong HAS-A relationship.

Contained object cannot exist independently.

---

# Example

```text
House HAS-A Room

Human HAS-A Heart

Car HAS-A Engine
```

---

# Key Characteristic

Destroy parent:

```text
Child Destroyed
```

---

# Java Example

```java
class Engine {

}

class Car {

    private Engine engine =
    new Engine();

}
```

---

# Relationship

```text
Car

↓

Engine
```

Engine belongs completely to Car.

---

# Memory Diagram

```text
Car Object
   |
   |
   V
Engine Object
```

---

# Real Example

If Car is removed:

```text
Engine Also Removed
```

---

# Why Composition?

Provides:

```text
Strong Encapsulation

Better Design

High Cohesion
```

---

# Composition Diagram

```text
Car

◆──── Engine
```

(Filled Diamond)

---

# 6. Association vs Aggregation vs Composition

| Feature      | Association     | Aggregation         | Composition  |
| ------------ | --------------- | ------------------- | ------------ |
| Relationship | Uses Object     | HAS-A               | Strong HAS-A |
| Dependency   | Independent     | Weak                | Strong       |
| Lifecycle    | Independent     | Independent         | Dependent    |
| Ownership    | No              | Partial             | Complete     |
| Example      | Teacher-Student | Department-Employee | Car-Engine   |

---

# Interview Trick Question

Which is stronger?

```text
Association

↓

Aggregation

↓

Composition
```

Composition is strongest.

---

# 7. Dependency Relationship

## Definition

One object temporarily uses another object.

Example:

```java
class EmployeeService {

    void save(
    Employee employee
    ){

    }

}
```

---

# Relationship

```text
EmployeeService

↓

Uses

↓

Employee
```

No permanent reference stored.

---

# Characteristics

```text
Temporary Usage

Loose Coupling

Common In Frameworks
```

---

# Real Examples

```text
REST Assured Requests

WebDriver Usage

Page Objects

Utility Methods
```

---

# 8. Dependency Injection Basics

## Problem

Tightly Coupled Design:

```java
class LoginPage {

    WebDriver driver =
    new ChromeDriver();

}
```

Issue:

```text
Hardcoded Dependency
```

---

# Better Approach

```java
class LoginPage {

    WebDriver driver;

    LoginPage(
    WebDriver driver
    ){

        this.driver = driver;

    }

}
```

---

# Benefits

```text
Flexible

Testable

Reusable
```

---

# This Is Dependency Injection

Dependency provided externally.

---

# Flow

```text
DriverFactory

↓

Creates Driver

↓

Injects Driver

↓

LoginPage Uses Driver
```

---

# 9. Selenium Framework Architecture

Typical Framework:

```text
Test Class
     |
     |
     V

Page Object
     |
     |
     V

WebDriver
```

---

# Relationship Analysis

Page Object:

```text
HAS-A

WebDriver
```

DriverFactory:

```text
Creates Driver
```

ConfigReader:

```text
Provides Configuration
```

ReportManager:

```text
Uses Test Information
```

---

# Framework Design

```text
Aggregation

Composition

Dependency Injection
```

all work together.

---

# 10. Spring Framework Connection

Spring Framework heavily uses:

```text
Dependency Injection
```

---

# Example

Without Spring:

```java
EmployeeService service =
new EmployeeService();
```

---

# With Spring

```java
@Autowired

EmployeeService service;
```

Spring injects dependency.

---

# Benefits

```text
Loose Coupling

Scalability

Easy Testing
```

---

# 11. JVM Perspective

Object Creation:

```text
Heap Memory

↓

Employee Object

↓

Address Object
```

References connect objects.

---

# Example

```java
Employee emp =
new Employee();

Address addr =
new Address();

emp.address = addr;
```

Memory:

```text
Employee Object
      |
      |
      V
Address Object
```

---

# JVM Stores

```text
Object References

Not Actual Objects
```

inside fields.

---

# Common Interview Questions

## Q1. What is IS-A Relationship?

Inheritance.

---

## Q2. What is HAS-A Relationship?

One class contains another class object.

---

## Q3. Which Relationship Uses extends?

```text
IS-A
```

---

## Q4. What is Association?

Relationship between independent objects.

---

## Q5. What is Aggregation?

Weak HAS-A relationship.

---

## Q6. What is Composition?

Strong HAS-A relationship.

---

## Q7. Which Relationship Has Strong Ownership?

```text
Composition
```

---

## Q8. Which Relationship Is Used Most In Frameworks?

```text
HAS-A

Aggregation

Dependency Injection
```

---

## Q9. What Happens If Parent Object Dies In Composition?

Child object also becomes unavailable.

---

## Q10. Why Is Dependency Injection Important?

```text
Loose Coupling

Easy Testing

Reusable Code
```

---

## Q11. Which Is Better: Inheritance or Composition?

Modern design prefers:

```text
Composition Over Inheritance
```

because it provides:

```text
Flexibility

Loose Coupling

Maintainability
```

---

# Real Interview Scenario

Question:

```text
LoginPage has WebDriver.

What relationship is this?
```

Answer:

```text
HAS-A Relationship

Aggregation
```

---

# Revision Notes

```text
IS-A
↓
Inheritance

HAS-A
↓
Object Relationship

Association
↓
Independent Objects

Aggregation
↓
Weak HAS-A

Composition
↓
Strong HAS-A

Dependency
↓
Temporary Usage

Dependency Injection
↓
External Dependency Supply

Spring
↓
DI Framework
```

---

# Interview Summary

```text
Inheritance
↓
IS-A

Object Containment
↓
HAS-A

Weak Ownership
↓
Aggregation

Strong Ownership
↓
Composition

Framework Design
↓
Dependency Injection

Modern OOP
↓
Composition Over Inheritance
```

---

# End of Part 8

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-9.md

Topics:

* Object Life Cycle
* Garbage Collection
* finalize() Method
* Memory Leaks
* Reachability Analysis
* Weak References
* Soft References
* Phantom References
* JVM Heap Internals
* Selenium Memory Management
* Interview Questions
