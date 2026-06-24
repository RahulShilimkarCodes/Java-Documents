# Java-Classes-and-Objects-Master-Guide-Part-10.md

# Java Classes and Objects Master Guide

## Part 10 – Reflection API, ClassLoader, Runtime Object Inspection & Framework Internals

---

# Table of Contents

1. Introduction to Reflection
2. Why Reflection Exists
3. What is Class Class?
4. Obtaining Class Objects
5. getClass() Method
6. Reflection API Fundamentals
7. Inspecting Fields at Runtime
8. Inspecting Methods at Runtime
9. Inspecting Constructors
10. Creating Objects Dynamically
11. Invoking Methods Dynamically
12. Accessing Private Members
13. ClassLoader Fundamentals
14. Java Class Loading Process
15. Built-in ClassLoaders
16. Annotations Basics
17. Selenium Framework Usage
18. TestNG Reflection Usage
19. JVM Internals
20. Interview Questions
21. Revision Notes

---

# Introduction

Until now we have learned:

```text
Classes

Objects

Constructors

Inheritance

Polymorphism

Object Relationships

Garbage Collection
```

Normally Java programs know everything during compile time.

Example:

```java
Employee emp =
new Employee();
```

Compiler already knows:

```text
Employee Class

Employee Methods

Employee Variables
```

But what if:

```text
Class Name Is Available Only At Runtime?
```

Example:

```text
Read From XML

Read From Properties File

Read From Database

Read From Framework Configuration
```

Java solves this using:

```text
Reflection API
```

---

# 1. What is Reflection?

## Definition

Reflection is the ability of a Java program to inspect and manipulate classes, methods, constructors, and fields at runtime.

---

# Normal Java

```java
Employee emp =
new Employee();
```

Compiler knows everything.

---

# Reflection

```java
Class.forName(
"Employee"
);
```

Class discovered dynamically.

---

# Real Meaning

Reflection allows Java to ask:

```text
What Class Is This?

What Methods Exist?

What Fields Exist?

Can I Create Object Dynamically?

Can I Invoke Methods Dynamically?
```

---

# Why Reflection is Important?

Many frameworks depend heavily on Reflection.

Examples:

```text
Selenium

TestNG

Spring

Hibernate

JUnit

REST Frameworks
```

Without Reflection:

```text
Modern Frameworks Cannot Exist
```

---

# 2. Why Reflection Exists

Imagine:

```text
config.properties

browser=Chrome
```

Framework reads:

```text
ChromeDriver
```

at runtime.

---

# Question

How does framework create:

```java
new ChromeDriver();
```

without hardcoding?

---

# Answer

Reflection.

---

# Runtime Flow

```text
Read Class Name

↓

Load Class

↓

Create Object

↓

Invoke Methods
```

---

# 3. What is Class Class?

Many developers find this confusing.

Java provides:

```java
java.lang.Class
```

---

# Important Concept

Every loaded class has a corresponding:

```java
Class Object
```

inside JVM.

---

# Example

```java
Employee emp =
new Employee();
```

Internally:

```text
Employee.class

↓

Class Object Created
```

---

# Visualization

```text
Employee.java

↓

Employee.class

↓

Class Object

↓

Object Creation
```

---

# Why Class Object?

Stores metadata.

Examples:

```text
Class Name

Methods

Fields

Constructors

Annotations
```

---

# 4. Obtaining Class Objects

There are three common ways.

---

# Method 1

Using .class

```java
Class<?> cls =
Employee.class;
```

---

# Method 2

Using getClass()

```java
Employee emp =
new Employee();

Class<?> cls =
emp.getClass();
```

---

# Method 3

Using Class.forName()

```java
Class<?> cls =
Class.forName(
"Employee"
);
```

---

# Interview Question

Which method loads class dynamically?

Answer:

```java
Class.forName()
```

---

# 5. getClass() Method

Inherited from:

```java
Object Class
```

---

# Example

```java
Employee emp =
new Employee();

System.out.println(
emp.getClass()
);
```

Output:

```text
class Employee
```

---

# Use Cases

```text
Debugging

Framework Design

Logging

Runtime Analysis
```

---

# 6. Reflection API Fundamentals

Package:

```java
java.lang.reflect
```

Contains:

```text
Field

Method

Constructor

Modifier

Proxy
```

---

# Example

```java
Class<?> cls =
Employee.class;
```

Now JVM can inspect:

```text
Fields

Methods

Constructors
```

---

# Reflection Workflow

```text
Class Object

↓

Get Metadata

↓

Inspect Members

↓

Perform Action
```

---

# 7. Inspecting Fields

Example:

```java
class Employee {

    private int id;

    private String name;

}
```

---

# Retrieve Fields

```java
Field[] fields =
Employee.class
.getDeclaredFields();
```

---

# Output

```text
id

name
```

---

# Framework Usage

Frameworks inspect:

```text
Annotations

Configuration Fields

Dependency Fields
```

using reflection.

---

# 8. Inspecting Methods

Example:

```java
Method[] methods =
Employee.class
.getDeclaredMethods();
```

---

# Output

```text
getId()

setId()

display()
```

---

# Real Use Case

TestNG discovers:

```java
@Test
public void loginTest()
```

using reflection.

---

# Flow

```text
Find Methods

↓

Check Annotations

↓

Execute Test
```

---

# 9. Inspecting Constructors

Example:

```java
Constructor<?>[] cons =
Employee.class
.getDeclaredConstructors();
```

---

# Output

```text
Employee()

Employee(int id)
```

---

# Framework Usage

Spring discovers constructors.

Then:

```text
Injects Dependencies
```

automatically.

---

# 10. Creating Objects Dynamically

Traditional Way

```java
Employee emp =
new Employee();
```

---

# Reflection Way

```java
Class<?> cls =
Class.forName(
"Employee"
);

Object obj =
cls.getDeclaredConstructor()
.newInstance();
```

---

# Why Important?

Framework does not know class beforehand.

---

# Runtime Flow

```text
Class Name

↓

Load Class

↓

Create Object

↓

Return Reference
```

---

# 11. Invoking Methods Dynamically

Example

```java
Method method =
cls.getDeclaredMethod(
"display"
);
```

Invoke:

```java
method.invoke(obj);
```

---

# Equivalent To

```java
obj.display();
```

but dynamically.

---

# Real Framework Example

TestNG:

```text
Discovers Method

↓

Invokes Method

↓

Runs Test
```

---

# 12. Accessing Private Members

Normally:

```java
private int salary;
```

cannot be accessed.

---

# Reflection Can Access

```java
Field field =
Employee.class
.getDeclaredField(
"salary"
);

field.setAccessible(
true
);
```

---

# Why Dangerous?

Breaks encapsulation.

---

# Therefore

Use carefully.

---

# Interview Question

Can Reflection Access Private Members?

Answer:

```text
Yes
```

using:

```java
setAccessible(true)
```

---

# 13. What is ClassLoader?

ClassLoader loads classes into JVM.

---

# Example

```java
Employee emp =
new Employee();
```

Before object creation:

```text
Employee.class

↓

Loaded By ClassLoader
```

---

# Without ClassLoader

```text
No Class

↓

No Object

↓

No Program
```

---

# Responsibilities

```text
Locate Class

Load Class

Verify Class

Prepare Class

Initialize Class
```

---

# 14. Java Class Loading Process

Step 1

```text
Loading
```

---

Step 2

```text
Linking
```

---

Step 3

```text
Initialization
```

---

# Flow

```text
Class File

↓

Load

↓

Verify

↓

Prepare

↓

Resolve

↓

Initialize
```

---

# Example

```java
new Employee();
```

Before execution:

```text
Employee.class Loaded
```

---

# 15. Built-in ClassLoaders

Java provides three main loaders.

---

# Bootstrap ClassLoader

Loads:

```text
java.lang

java.util

java.io
```

---

# Extension ClassLoader

Loads:

```text
Extension Libraries
```

---

# Application ClassLoader

Loads:

```text
Project Classes

Employee.class

Manager.class
```

---

# Hierarchy

```text
Bootstrap

↓

Extension

↓

Application
```

---

# 16. Annotations Basics

Annotations provide metadata.

Example:

```java
@Override
```

---

# Common Annotations

```java
@Override

@Deprecated

@SuppressWarnings
```

---

# Custom Annotation

```java
@interface TestData {

}
```

---

# Why Annotations?

Frameworks use them heavily.

---

# Example

```java
@Test
```

in TestNG.

---

# Runtime Flow

```text
Reflection

↓

Reads Annotation

↓

Performs Action
```

---

# 17. Selenium Framework Usage

Reflection appears in:

```text
PageFactory

TestNG

Listeners

Annotations

Driver Factories
```

---

# PageFactory Example

```java
@FindBy(id="username")
WebElement username;
```

---

# Internally

Reflection discovers:

```text
@FindBy

↓

Locates Element

↓

Assigns WebElement
```

---

# Without Reflection

PageFactory cannot work.

---

# 18. TestNG Reflection Usage

Example:

```java
@Test

@BeforeMethod

@AfterMethod
```

---

# How TestNG Works

```text
Scan Class

↓

Find Annotation

↓

Invoke Method

↓

Generate Result
```

All through Reflection.

---

# Test Execution Flow

```text
Class

↓

Reflection

↓

@Test Found

↓

Method Executed
```

---

# 19. JVM Internals

When class loads:

```text
Method Area

↓

Class Metadata Stored
```

---

# Metadata Contains

```text
Fields

Methods

Constructors

Annotations
```

---

# Reflection Reads

```text
Metadata

Not Source Code
```

---

# Memory Diagram

```text
Method Area

Employee Metadata

↓

Reflection API

↓

Runtime Inspection
```

---

# Common Interview Questions

## Q1. What is Reflection?

Runtime inspection and manipulation of classes.

---

## Q2. Which Package Contains Reflection API?

```java
java.lang.reflect
```

---

## Q3. What is Class Class?

Represents metadata of loaded class.

---

## Q4. How Many Ways Can We Get Class Object?

```text
3

.class

getClass()

Class.forName()
```

---

## Q5. Which Method Loads Class Dynamically?

```java
Class.forName()
```

---

## Q6. Can Reflection Access Private Members?

Yes.

Using:

```java
setAccessible(true)
```

---

## Q7. Why Is Reflection Slower?

Because operations occur dynamically at runtime.

---

## Q8. Which Frameworks Use Reflection?

```text
Spring

Hibernate

TestNG

JUnit

Selenium
```

---

## Q9. What is ClassLoader?

Loads classes into JVM.

---

## Q10. What Are The Three Built-in ClassLoaders?

```text
Bootstrap

Extension

Application
```

---

## Q11. How Does TestNG Find @Test Methods?

Using Reflection.

---

## Q12. How Does PageFactory Work?

Using Reflection + Annotations.

---

## Q13. What Is Metadata?

Information about class structure.

---

## Q14. Why Are Annotations Important?

Provide runtime metadata to frameworks.

---

## Q15. What Memory Area Stores Class Metadata?

```text
Method Area

(Metaspace in Modern JVM)
```

---

# Revision Notes

```text
Reflection
↓
Runtime Inspection

Class Object
↓
Metadata Holder

getClass()
↓
Returns Runtime Class

Class.forName()
↓
Dynamic Loading

Field
↓
Variable Metadata

Method
↓
Method Metadata

Constructor
↓
Constructor Metadata

ClassLoader
↓
Loads Classes

Annotations
↓
Metadata

TestNG
↓
Uses Reflection

PageFactory
↓
Uses Reflection
```

---

# Interview Summary

```text
Class File
↓
Loaded By ClassLoader

Class Object
↓
Stores Metadata

Reflection
↓
Reads Metadata

Annotations
↓
Guide Framework Behavior

TestNG
↓
Discovers Tests

PageFactory
↓
Discovers Elements

Spring
↓
Performs Dependency Injection
```

---

# End of Part 10

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-11.md

Topics:

* Advanced JVM Internals
* Method Area Deep Dive
* Stack Frames
* Object Headers
* String Pool Internals
* Escape Analysis
* JIT Compilation
* TLAB (Thread Local Allocation Buffer)
* Memory Optimization
* Selenium Framework Performance Considerations
* Advanced Interview Questions
