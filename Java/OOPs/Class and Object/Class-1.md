# Java-Classes-and-Objects-Master-Guide-Part-1.md

# Java Classes and Objects Master Guide

## Part 1 – Introduction to Classes and Objects

---

# Table of Contents

1. What is Object-Oriented Programming?
2. What is a Class?
3. What is an Object?
4. Real-World Analogy of Classes and Objects
5. Why Do We Need Classes?
6. Why Do We Need Objects?
7. Class vs Object
8. How Java Creates Objects
9. Memory Allocation of Objects
10. First Java Class Example
11. First Java Object Example
12. How Objects Communicate
13. Interview Questions
14. Revision Notes

---

# Introduction

Everything in Java revolves around Objects.

Java is known as an Object-Oriented Programming Language because it models real-world entities using:

* Classes
* Objects
* Inheritance
* Polymorphism
* Encapsulation
* Abstraction

Before learning advanced OOP concepts, it is important to understand:

```text
Class
↓
Blueprint

Object
↓
Real Instance Created From Blueprint
```

---

# 1. What is Object-Oriented Programming (OOP)?

## Definition

Object-Oriented Programming is a programming paradigm that organizes software around objects rather than functions.

An object contains:

```text
State
↓
Variables

Behavior
↓
Methods
```

Example:

```text
Car

State:
Color
Brand
Speed

Behavior:
Start()
Stop()
Accelerate()
```

---

## Benefits of OOP

### Code Reusability

Code can be reused using inheritance.

### Modularity

Applications can be divided into smaller classes.

### Scalability

Large applications become easier to manage.

### Maintainability

Code changes become easier.

---

# 2. What is a Class?

## Definition

A Class is a blueprint or template used to create objects.

A class defines:

```text
Properties
↓
Variables

Actions
↓
Methods
```

Example:

```java
class Employee {

    String name;
    int id;

    void work() {

        System.out.println("Working");

    }

}
```

---

## Understanding Class

Think of a class as:

```text
Building Blueprint

↓

Actual Building
```

Blueprint:

```text
Class
```

Building:

```text
Object
```

---

# 3. What is an Object?

## Definition

An Object is an instance of a class.

When memory is allocated for a class, it becomes an object.

Example:

```java
Employee emp =
new Employee();
```

Here:

```text
Employee
↓
Class

emp
↓
Reference Variable

new Employee()
↓
Object
```

---

# 4. Real-World Analogy

Consider a Car.

### Class

```text
Car
```

Defines:

```text
Color

Brand

Speed

Start()

Stop()
```

### Objects

```text
BMW

Audi

Mercedes
```

All are objects of Car class.

---

# Example

Blueprint:

```text
Car
```

Objects:

```text
BMW X5

Audi A6

Mercedes C-Class
```

---

# 5. Why Do We Need Classes?

Without classes:

```text
Thousands of Variables

Thousands of Functions

Difficult Maintenance
```

Classes help group related data and behavior together.

Example:

Instead of:

```java
String employeeName;
int employeeId;
double employeeSalary;
```

Use:

```java
class Employee {

    String name;
    int id;
    double salary;

}
```

---

## Benefits

```text
Organization

Reusability

Maintainability

Readability
```

---

# 6. Why Do We Need Objects?

Class alone cannot perform any operation.

Example:

```java
class Employee {

    String name;

}
```

The above class occupies no runtime memory for actual data.

Object creation is required.

Example:

```java
Employee emp =
new Employee();
```

Now memory is allocated.

---

# 7. Difference Between Class and Object

| Class              | Object             |
| ------------------ | ------------------ |
| Blueprint          | Instance           |
| Logical Entity     | Physical Entity    |
| No Memory for Data | Occupies Memory    |
| Defined Once       | Created Many Times |
| Template           | Real Entity        |

---

## Example

Class:

```java
class Student {

}
```

Objects:

```java
Student s1 =
new Student();

Student s2 =
new Student();

Student s3 =
new Student();
```

---

# 8. How Java Creates Objects

Object creation process:

```java
Employee emp =
new Employee();
```

Step 1

```text
new Keyword Executed
```

Step 2

```text
Memory Allocated in Heap
```

Step 3

```text
Constructor Invoked
```

Step 4

```text
Reference Assigned
```

---

## Visual Representation

```text
Stack Memory

emp
 |
 |
 V

Heap Memory

Employee Object
```

---

# 9. Memory Allocation of Objects

Java uses:

```text
Stack Memory

Heap Memory
```

### Stack

Stores:

```text
Reference Variables

Method Calls
```

Example:

```java
Employee emp;
```

Stored in Stack.

---

### Heap

Stores:

```text
Objects

Instance Variables
```

Example:

```java
new Employee();
```

Stored in Heap.

---

## Diagram

```text
Stack
-----
emp
 |
 |
 V

Heap
-----
Employee Object
```

---

# 10. First Java Class Example

```java
class Employee {

    String name;
    int id;

}
```

Explanation:

```text
Employee
↓
Class Name

name
↓
Instance Variable

id
↓
Instance Variable
```

---

# 11. First Java Object Example

```java
class Employee {

    String name;
    int id;

}

public class Test {

    public static void main(String[] args) {

        Employee emp =
        new Employee();

    }

}
```

---

## What Happens Internally?

```text
Employee Class Loaded

↓

Object Created

↓

Memory Allocated

↓

Reference Stored
```

---

# 12. How Objects Communicate?

Objects communicate through method calls.

Example:

```java
class Employee {

    void work() {

        System.out.println(
        "Employee Working"
        );

    }

}
```

Object Call:

```java
Employee emp =
new Employee();

emp.work();
```

Output:

```text
Employee Working
```

---

# Common Interview Questions

## Q1. What is a Class?

A blueprint used to create objects.

---

## Q2. What is an Object?

An instance of a class.

---

## Q3. Can We Create Multiple Objects from One Class?

Yes.

Example:

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee();

Employee e3 =
new Employee();
```

---

## Q4. Does a Class Occupy Memory?

Class metadata is loaded into JVM memory.

Actual object data occupies memory only after object creation.

---

## Q5. Where Are Objects Stored?

Heap Memory.

---

## Q6. Where Are References Stored?

Stack Memory.

---

## Q7. What Does the new Keyword Do?

```text
Allocates Memory

Calls Constructor

Returns Reference
```

---

# Revision Sheet

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

Stack
↓
Reference Variables

Heap
↓
Objects

Class
↓
Logical Entity

Object
↓
Physical Entity

State
↓
Variables

Behavior
↓
Methods
```

---

# Key Interview Summary

```text
Class
↓
Template

Object
↓
Real Entity

One Class
↓
Many Objects

Objects Stored
↓
Heap Memory

References Stored
↓
Stack Memory
```

---

# End of Part 1

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-2.md

Topics:

* Instance Variables
* Local Variables
* Reference Variables
* Object References
* Object Initialization
* Accessing Class Members
* Multiple Objects
* Memory Diagrams
* JVM Internals During Object Creation
* Interview Questions
