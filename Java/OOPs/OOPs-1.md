# Java OOP Master Guide

# Part 1 - Class, Object & JVM Memory Model

---

# Table of Contents

1. What is OOP?
2. Why OOP Was Introduced
3. Procedural Programming vs OOP
4. Four Pillars of OOP
5. What is a Class?
6. What is an Object?
7. Class vs Object
8. Object Lifecycle
9. Reference Variables
10. JVM Memory Model
11. Heap vs Stack
12. Object Creation Internals
13. Multiple References
14. Anonymous Objects
15. Garbage Collection Basics
16. Real-World Examples
17. OOP in Selenium Framework
18. OOP in API Framework
19. Common Interview Mistakes
20. Top Interview Questions
21. Revision Notes
22. Cheat Sheet

---

# 1. What is OOP?

OOP stands for:

```text
Object Oriented Programming
```

---

Definition:

```text
A programming paradigm that organizes
software around objects rather than
functions and logic.
```

---

Java is primarily an:

```text
Object-Oriented Programming Language
```

---

Everything in enterprise Java revolves around:

```text
Classes

Objects

Inheritance

Polymorphism

Abstraction

Encapsulation
```

---

# Why OOP Is Important

Without OOP:

```text
Large Applications Become Difficult

Code Duplication Increases

Maintenance Becomes Hard

Reusability Reduces
```

---

With OOP:

```text
Reusable Code

Scalable Design

Easy Maintenance

Modular Architecture

Better Security
```

---

# 2. Why OOP Was Introduced

Earlier languages followed:

```text
Procedural Programming
```

---

Example:

```c
createUser();

createOrder();

processPayment();
```

---

Problems:

```text
Global Variables

Code Duplication

Tight Coupling

Poor Scalability
```

---

Solution:

```text
Object-Oriented Programming
```

---

Instead of functions:

```text
User Object

Order Object

Payment Object
```

---

Each object manages its own:

```text
Data

Behavior
```

---

# 3. Procedural Programming vs OOP

| Procedural            | OOP                |
| --------------------- | ------------------ |
| Function Based        | Object Based       |
| Less Secure           | More Secure        |
| Difficult Maintenance | Easy Maintenance   |
| Low Reusability       | High Reusability   |
| Data Exposed          | Data Hidden        |
| Top-Down Approach     | Bottom-Up Approach |

---

Interview Answer:

```text
Procedural programming focuses on functions,
while OOP focuses on objects containing
both data and behavior.
```

---

# 4. Four Pillars of OOP

The foundation of OOP:

```text
1. Encapsulation

2. Inheritance

3. Polymorphism

4. Abstraction
```

---

### Encapsulation

```text
Data Hiding
```

---

### Inheritance

```text
Code Reusability
```

---

### Polymorphism

```text
One Interface

Multiple Forms
```

---

### Abstraction

```text
Hide Implementation Details
```

---

These four concepts dominate Java interviews.

---

# 5. What is a Class?

Definition:

```text
A class is a blueprint used to create objects.
```

---

Example:

```java
public class Employee {

    String name;

    int age;

}
```

---

Class Contains:

```text
Variables

Methods

Constructors

Blocks

Nested Classes
```

---

Real World Example:

```text
House Blueprint

↓

Class
```

---

```text
Actual House

↓

Object
```

---

Interview Definition:

```text
A class is a logical template that
defines state and behavior.
```

---

# 6. What is an Object?

Definition:

```text
An object is an instance of a class.
```

---

Example:

```java
Employee emp =
new Employee();
```

---

Breakdown:

```text
Employee

↓

Class
```

---

```text
emp

↓

Reference Variable
```

---

```text
new Employee()

↓

Object
```

---

# Object Has Two Things

## State

```java
name

age

salary
```

---

## Behavior

```java
login()

logout()

calculateSalary()
```

---

# 7. Class vs Object

| Class               | Object             |
| ------------------- | ------------------ |
| Blueprint           | Instance           |
| Logical Entity      | Physical Entity    |
| No Memory Allocated | Memory Allocated   |
| One Definition      | Multiple Instances |

---

Example:

```java
class Employee
```

Class.

---

```java
Employee e1 =
new Employee();
```

Object.

---

```java
Employee e2 =
new Employee();
```

Another Object.

---

# 8. Object Lifecycle

Object Lifecycle:

```text
Creation

↓

Initialization

↓

Usage

↓

Eligible For GC

↓

Garbage Collection
```

---

Example:

```java
Employee emp =
new Employee();
```

---

Object Created.

---

```java
emp = null;
```

---

Object becomes:

```text
Eligible For Garbage Collection
```

---

# 9. Reference Variables

Example:

```java
Employee emp;
```

---

emp is NOT object.

emp is:

```text
Reference Variable
```

---

Purpose:

```text
Stores Address Of Object
```

---

Example:

```java
Employee emp =
new Employee();
```

---

Memory Representation:

```text
emp -----> Employee Object
```

---

Interview Question:

```text
What does reference variable store?
```

Answer:

```text
Object Address / Reference Value
```

---

# 10. JVM Memory Model

Extremely Important Topic.

JVM Memory:

```text
+----------------------+
| Method Area          |
+----------------------+
| Heap Memory          |
+----------------------+
| Stack Memory         |
+----------------------+
| PC Register          |
+----------------------+
| Native Method Stack  |
+----------------------+
```

---

For OOP interviews:

Focus on:

```text
Heap

Stack

Method Area
```

---

# 11. Heap vs Stack

Example:

```java
Employee emp =
new Employee();
```

---

Stack:

```text
emp
```

---

Heap:

```text
Employee Object
```

---

Comparison:

| Heap          | Stack           |
| ------------- | --------------- |
| Objects       | References      |
| Shared Memory | Thread Specific |
| Large Memory  | Small Memory    |
| GC Managed    | Auto Cleanup    |

---

Interview Question:

```text
Where are objects stored?
```

Answer:

```text
Heap Memory
```

---

# 12. Object Creation Internals

Code:

```java
Employee emp =
new Employee();
```

---

Step 1

```text
Class Loaded
```

---

Step 2

```text
Heap Memory Allocated
```

---

Step 3

```text
Default Values Assigned
```

---

Step 4

```text
Constructor Executes
```

---

Step 5

```text
Reference Returned
```

---

Memory Diagram:

```text
STACK

emp
 |
 |
 v

HEAP

Employee Object
```

---

# 13. Multiple References

Example:

```java
Employee e1 =
new Employee();

Employee e2 = e1;
```

---

Memory:

```text
e1 ----+
       |
       v

     Object

       ^
       |
e2 ----+
```

---

Interview Question:

```text
How many objects?
```

Answer:

```text
One Object

Two References
```

---

# 14. Anonymous Objects

Object without reference.

Example:

```java
new Employee();
```

---

Another Example:

```java
new Employee().display();
```

---

Advantages:

```text
Less Memory Usage

One-Time Use
```

---

Disadvantage:

```text
Cannot Reuse Object
```

---

# 15. Garbage Collection Basics

Example:

```java
Employee emp =
new Employee();

emp = null;
```

---

Object becomes:

```text
Unreachable
```

---

Eligible for:

```text
Garbage Collection
```

---

Interview Point:

```text
Garbage Collector removes
unreachable heap objects.
```

---

# 16. Real-World Examples

Class:

```text
Car
```

---

Objects:

```text
BMW

Audi

Mercedes
```

---

Class:

```text
Employee
```

---

Objects:

```text
Rahul

Rohini

Amit
```

---

# 17. OOP in Selenium Framework

Page Object Model:

```java
LoginPage login =
new LoginPage(driver);
```

---

Class:

```text
LoginPage
```

---

Object:

```text
login
```

---

Benefits:

```text
Reusable Pages

Maintainable Design

Encapsulation
```

---

# 18. OOP in API Framework

Example:

```java
UserService service =
new UserService();
```

---

```java
TokenManager manager =
new TokenManager();
```

---

Everything revolves around:

```text
Objects
```

---

# 19. Common Interview Mistakes

### Mistake 1

```text
Class Allocates Memory
```

Wrong.

---

Correct:

```text
Object Allocates Memory
```

---

### Mistake 2

```text
Reference = Object
```

Wrong.

---

Reference points to object.

---

### Mistake 3

```text
Stack Stores Objects
```

Wrong.

---

Objects reside in heap.

---

# 20. Top Interview Questions

### Q1 What is OOP?

```text
Programming paradigm based on objects.
```

---

### Q2 What is a Class?

```text
Blueprint for creating objects.
```

---

### Q3 What is an Object?

```text
Instance of a class.
```

---

### Q4 Where Are Objects Stored?

```text
Heap Memory
```

---

### Q5 What Does new Keyword Do?

```text
Creates Object
Allocates Heap Memory
```

---

### Q6 What Is Reference Variable?

```text
Stores Address Of Object
```

---

### Q7 What Is Garbage Collection?

```text
Automatic Heap Cleanup
```

---

# 21. Revision Notes

```text
Class

↓

Blueprint

Object

↓

Instance

new

↓

Creates Object

Heap

↓

Stores Objects

Stack

↓

Stores References

GC

↓

Removes Unreachable Objects
```

---

# 22. Cheat Sheet

```text
OOP

↓

Class

↓

Object

↓

Reference Variable

↓

Heap Allocation

↓

Constructor Execution

↓

Object Usage

↓

Unreachable

↓

Garbage Collection
```

---

# Interview Takeaway

If interviewer asks:

```text
Explain Class and Object with JVM Memory.
```

Answer:

```text
A class is a blueprint that defines
state and behavior, while an object
is a runtime instance of that class.

When an object is created using the
new keyword, memory is allocated in
the heap. The reference variable is
stored in stack memory and points
to the heap object.

If no references point to the object,
it becomes eligible for garbage collection.
```

---

# End of OOP Part 1

## Next Part

Part 2 → Constructors Deep Dive

Topics:

* Default Constructor
* No-Arg Constructor
* Parameterized Constructor
* Constructor Overloading
* Constructor Chaining
* this() vs super()
* Object Initialization Flow
* Singleton Pattern
* Selenium Examples
* API Framework Examples
* Interview Questions
* Revision Notes
