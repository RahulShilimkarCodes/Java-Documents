# Java-Classes-and-Objects-Master-Guide-Part-5.md

# Java Classes and Objects Master Guide

## Part 5 – Static Variables, Static Methods, Static Blocks & JVM Memory

---

# Table of Contents

1. Introduction to static Keyword
2. Why static is Needed
3. Static Variables
4. Instance Variables vs Static Variables
5. Static Methods
6. Static vs Non-Static Methods
7. Rules of Static Methods
8. Static Blocks
9. Static Block Execution Flow
10. JVM Memory Areas
11. Method Area and Static Members
12. Static Initialization
13. Real-World Examples
14. Selenium Framework Examples
15. Singleton Introduction
16. Interview Questions
17. Revision Notes

---

# Introduction

Until now we have learned:

```text
Class
↓
Blueprint

Object
↓
Instance

Instance Variables
↓
Belong To Object

Constructors
↓
Initialize Object
```

However, sometimes data should not belong to individual objects.

Instead:

```text
One Copy

↓

Shared By All Objects
```

Java provides:

```text
static
```

for such scenarios.

---

# 1. What is static Keyword?

## Definition

The `static` keyword belongs to the class rather than the object.

Example:

```java
class Employee {

    static String company =
    "Google";

}
```

Here:

```text
company
↓
Belongs To Class

NOT

Individual Objects
```

---

# Why static?

Suppose:

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee();

Employee e3 =
new Employee();
```

All employees belong to:

```text
Google
```

Creating separate copies is wasteful.

Instead:

```text
Single Shared Copy
```

using static.

---

# 2. Why static is Needed?

Without static:

```java
class Employee {

    String company =
    "Google";

}
```

Memory:

```text
Object1
-------
company

Object2
-------
company

Object3
-------
company
```

Three copies created.

---

With static:

```java
class Employee {

    static String company =
    "Google";

}
```

Memory:

```text
Class Area
----------
company

Object1

Object2

Object3
```

Only one copy exists.

---

# Benefits

```text
Memory Efficient

Shared Data

Faster Access

Better Design
```

---

# 3. Static Variables

## Definition

Variables declared using static keyword.

Example:

```java
class Employee {

    static String company =
    "Google";

}
```

---

## Accessing Static Variables

Preferred:

```java
System.out.println(
Employee.company
);
```

Output:

```text
Google
```

---

Possible but not recommended:

```java
Employee emp =
new Employee();

System.out.println(
emp.company
);
```

---

# Memory Representation

```text
Method Area

company = Google

↓

Shared By

e1
e2
e3
```

---

# Example

```java
class Employee {

    static String company =
    "Google";

    String name;

}
```

Object Creation:

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee();
```

Memory:

```text
Method Area
-----------
company

Heap
----
e1

e2
```

---

# 4. Instance Variables vs Static Variables

| Instance Variable              | Static Variable              |
| ------------------------------ | ---------------------------- |
| Belongs To Object              | Belongs To Class             |
| Stored In Heap                 | Stored In Method Area        |
| Multiple Copies                | Single Copy                  |
| Access Using Object            | Access Using Class           |
| Created During Object Creation | Created During Class Loading |

---

## Example

```java
class Employee {

    String name;

    static String company =
    "Google";

}
```

Memory:

```text
Shared

company

Individual

name
```

---

# Interview Question

How many copies?

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee();

Employee e3 =
new Employee();
```

Answer:

```text
name
↓
3 Copies

company
↓
1 Copy
```

---

# 5. Static Methods

## Definition

Methods declared using static keyword.

Example:

```java
class Calculator {

    static int add(
    int a,
    int b
    ){

        return a + b;

    }

}
```

Call:

```java
Calculator.add(10,20);
```

Output:

```text
30
```

---

## Why Static Methods?

No object creation required.

Example:

```java
Math.sqrt(25);

Integer.parseInt("100");
```

These are static methods.

---

# Static Method Memory

```text
Class Loaded

↓

Static Method Available

↓

No Object Required
```

---

# 6. Static vs Non-Static Methods

| Static Method                      | Non-Static Method  |
| ---------------------------------- | ------------------ |
| Belongs To Class                   | Belongs To Object  |
| No Object Needed                   | Object Needed      |
| Can Access Static Members Directly | Can Access Both    |
| Loaded During Class Loading        | Loaded With Object |

---

## Example

```java
class Employee {

    static void companyInfo(){

    }

    void employeeInfo(){

    }

}
```

Call:

```java
Employee.companyInfo();
```

No object required.

---

# 7. Rules of Static Methods

## Rule 1

Can directly access static members.

Example:

```java
static int count = 10;

static void display(){

    System.out.println(
    count
    );

}
```

Valid.

---

## Rule 2

Cannot directly access instance variables.

Example:

```java
String name;

static void show(){

    System.out.println(
    name
    );

}
```

Compiler Error.

---

Why?

```text
No Object Exists
```

---

## Correct Way

```java
Employee emp =
new Employee();

System.out.println(
emp.name
);
```

---

## Rule 3

Cannot Use this

Example:

```java
static void display(){

    System.out.println(
    this
    );

}
```

Compiler Error.

---

Why?

```text
this

↓

Current Object

↓

No Object Exists
```

---

# 8. Static Blocks

## Definition

Block declared using static keyword.

Example:

```java
class Employee {

    static {

        System.out.println(
        "Static Block"
        );

    }

}
```

Output:

```text
Static Block
```

---

# Why Static Blocks?

Used for:

```text
Static Initialization

Configuration Loading

Resource Initialization
```

---

# Example

```java
class Database {

    static String url;

    static {

        url =
        "jdbc:mysql://localhost";

    }

}
```

---

# 9. Static Block Execution Flow

Example:

```java
class Test {

    static {

        System.out.println("A");

    }

    static {

        System.out.println("B");

    }

}
```

Output:

```text
A

B
```

---

# Important Rule

Executed:

```text
Only Once

↓

During Class Loading
```

---

# Execution Order

```text
Class Loading

↓

Static Variables

↓

Static Blocks

↓

main()

↓

Object Creation
```

---

# 10. JVM Memory Areas

Important JVM Areas:

```text
Method Area

Heap

Stack

PC Register

Native Method Stack
```

---

# Method Area

Stores:

```text
Class Metadata

Static Variables

Static Methods

Runtime Constants
```

---

# Heap

Stores:

```text
Objects

Instance Variables
```

---

# Stack

Stores:

```text
Method Calls

Local Variables

References
```

---

# 11. Method Area and Static Members

Example:

```java
class Employee {

    static String company;

}
```

Stored in:

```text
Method Area

↓

Shared By All Objects
```

---

## Visualization

```text
Method Area

company = Google

↓

Heap

e1

e2

e3
```

---

# 12. Static Initialization

Example:

```java
class Employee {

    static String company;

    static {

        company =
        "Google";

    }

}
```

Flow:

```text
Class Loading

↓

Static Block Executes

↓

company Initialized

↓

Object Creation
```

---

# 13. Real-World Example

Employee Count

```java
class Employee {

    static int count = 0;

    Employee(){

        count++;

    }

}
```

Objects:

```java
new Employee();

new Employee();

new Employee();
```

Output:

```java
System.out.println(
Employee.count
);
```

Output:

```text
3
```

---

# Why Static?

Count should be shared among all objects.

---

# 14. Selenium Framework Example

Driver Factory

```java
public class DriverFactory {

    public static WebDriver driver;

}
```

Usage:

```java
DriverFactory.driver
```

---

## Utility Methods

Example:

```java
public class WaitUtil {

    public static void waitForElement(){

    }

}
```

Call:

```java
WaitUtil.waitForElement();
```

No object required.

---

# 15. Singleton Introduction

## Problem

Prevent multiple object creation.

Example:

```text
Database Connection

Configuration Manager

Driver Manager
```

Need:

```text
Only One Object
```

---

## Solution

Singleton Pattern.

Uses:

```java
private static
```

members.

Detailed coverage in upcoming parts.

---

# Common Interview Questions

## Q1. What is static?

Belongs to class rather than object.

---

## Q2. Where are Static Variables Stored?

```text
Method Area
```

---

## Q3. Can Static Method Access Instance Variable Directly?

No.

Object required.

---

## Q4. Can Static Method Use this?

No.

No current object exists.

---

## Q5. Can Constructor Be Static?

No.

Compiler Error.

---

## Q6. Can Static Methods Be Overridden?

No.

They are hidden, not overridden.

---

## Q7. When Do Static Blocks Execute?

```text
During Class Loading
```

---

## Q8. How Many Times Does Static Block Execute?

```text
Only Once
```

---

## Q9. Which Executes First?

```text
Static Block

↓

main()

↓

Constructor
```

---

## Q10. Why Use Static Methods?

```text
Utility Functions

Shared Operations

No Object Required
```

---

# Revision Notes

```text
static
↓
Belongs To Class

Static Variable
↓
Single Copy

Static Method
↓
No Object Needed

Static Block
↓
Runs Once

Method Area
↓
Stores Static Members

Heap
↓
Stores Objects

Stack
↓
Stores References

Class Loading
↓
Triggers Static Initialization
```

---

# Interview Summary

```text
Instance Variable
↓
Object Level

Static Variable
↓
Class Level

Static Method
↓
Called Using Class Name

Static Block
↓
Executed Once

Method Area
↓
Stores Static Data

Shared Data
↓
Use static
```

---

# End of Part 5

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-6.md

Topics:

* Static Nested Classes
* Inner Classes
* Anonymous Inner Classes
* Local Inner Classes
* Singleton Design Pattern
* Object Creation Control
* Factory Pattern Basics
* Selenium Framework Usage
* JVM Internals
* Interview Questions
