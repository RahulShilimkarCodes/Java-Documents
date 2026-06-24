# Java-Classes-and-Objects-Master-Guide-Part-6.md

# Java Classes and Objects Master Guide

## Part 6 – Inner Classes, Nested Classes & Singleton Design Pattern

---

# Table of Contents

1. Introduction to Nested Classes
2. Why Nested Classes are Needed
3. Types of Nested Classes
4. Static Nested Classes
5. Non-Static Inner Classes
6. Local Inner Classes
7. Anonymous Inner Classes
8. Inner Class Memory Model
9. Singleton Design Pattern
10. Eager Singleton
11. Lazy Singleton
12. Thread-Safe Singleton
13. Factory Pattern Basics
14. Selenium Framework Examples
15. Real Project Usage
16. JVM Internals
17. Interview Questions
18. Revision Notes

---

# Introduction

So far we have learned:

```text
Class
↓
Blueprint

Object
↓
Instance

Static Members
↓
Class Level Data
```

Now we move into advanced class design concepts.

Large applications often contain classes that are tightly related.

Example:

```text
Employee

↓

Address

↓

Contact Details

↓

Salary Details
```

Creating all classes separately may expose implementation details.

Java provides:

```text
Nested Classes

↓

Classes Inside Classes
```

---

# 1. What are Nested Classes?

## Definition

A class declared inside another class is called a Nested Class.

Example:

```java
class Outer {

    class Inner {

    }

}
```

Here:

```text
Outer
↓
Outer Class

Inner
↓
Nested Class
```

---

# Why Use Nested Classes?

### Better Encapsulation

Hide helper classes.

### Improved Readability

Related classes stay together.

### Logical Grouping

Keep dependent classes close.

### Security

Reduce visibility.

---

# Real World Example

```text
Employee

↓

Address

↓

Contact
```

Address belongs only to Employee.

Therefore:

```text
Address

↓

Can Become Inner Class
```

---

# 2. Types of Nested Classes

Java provides four types.

```text
Nested Classes

├── Static Nested Class

├── Non-Static Inner Class

├── Local Inner Class

└── Anonymous Inner Class
```

---

# Classification

```text
Static Nested Class
↓
Uses static

Inner Class
↓
Uses object

Local Class
↓
Inside method

Anonymous Class
↓
No name
```

---

# 3. Static Nested Class

## Definition

Nested class declared using static keyword.

Example:

```java
class Outer {

    static class Inner {

    }

}
```

---

## Characteristics

```text
Belongs To Outer Class

No Outer Object Needed

Can Access Static Members Directly
```

---

# Creating Object

```java
Outer.Inner obj =
new Outer.Inner();
```

---

# Example

```java
class Company {

    static class Employee {

        void display(){

            System.out.println(
            "Employee"
            );

        }

    }

}
```

Usage:

```java
Company.Employee emp =
new Company.Employee();
```

---

# Memory Behavior

```text
Outer Class Loaded

↓

Inner Class Loaded

↓

Object Created
```

No Outer Object Required.

---

# Interview Question

Can Static Nested Class Access Non-Static Members?

Answer:

```text
No

Direct Access Not Allowed
```

Object required.

---

# 4. Non-Static Inner Class

## Definition

Nested class without static keyword.

Example:

```java
class Outer {

    class Inner {

    }

}
```

---

# Characteristics

```text
Requires Outer Object

Can Access All Members

Associated With Outer Instance
```

---

# Creating Object

```java
Outer outer =
new Outer();

Outer.Inner inner =
outer.new Inner();
```

---

# Why Outer Object Needed?

Because inner class belongs to object.

Not class.

---

# Example

```java
class Employee {

    private String name =
    "Rahul";

    class Address {

        void show(){

            System.out.println(
            name
            );

        }

    }

}
```

Output:

```text
Rahul
```

---

# Important Feature

Inner class can access:

```text
Private Variables

Private Methods

Protected Members
```

of outer class.

---

# 5. Local Inner Class

## Definition

Class declared inside a method.

Example:

```java
class Employee {

    void display(){

        class LocalClass {

            void show(){

                System.out.println(
                "Inside Local"
                );

            }

        }

    }

}
```

---

# Characteristics

```text
Scope Limited To Method

Cannot Be Accessed Outside

Created During Method Execution
```

---

# Real Usage

Rarely used in modern frameworks.

Mostly used for:

```text
Specialized Logic

Temporary Helper Classes
```

---

# 6. Anonymous Inner Class

## Definition

Inner class without a name.

Example:

```java
Runnable task =
new Runnable(){

    @Override

    public void run(){

        System.out.println(
        "Running"
        );

    }

};
```

---

# Why Anonymous?

```text
One-Time Usage

No Need To Create Separate Class
```

---

# Traditional Way

```java
class MyTask
implements Runnable {

}
```

---

# Anonymous Way

```java
new Runnable(){

};
```

Shorter code.

---

# Common Usage

Before Java 8:

```text
Event Handling

Thread Creation

Listeners
```

---

# Modern Alternative

```java
Lambda Expressions
```

---

# 7. Inner Class Memory Model

Example:

```java
class Outer {

    int x = 10;

    class Inner {

    }

}
```

Memory:

```text
Heap

Outer Object
-------------
x = 10

↓

Inner Object
```

---

# Important Concept

Inner object stores reference to outer object.

Visualization:

```text
Inner Object

↓

Outer Reference

↓

Outer Object
```

---

# JVM Behavior

Compiler generates:

```text
Outer.class

Outer$Inner.class
```

---

# 8. Singleton Design Pattern

One of the most important Java interview topics.

---

# Definition

Singleton ensures:

```text
Only One Object

Exists In JVM
```

---

# Why Singleton?

Resources are expensive.

Examples:

```text
Database Connection

Logger

Configuration Manager

Driver Manager
```

Only one instance needed.

---

# Traditional Object Creation

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee();

Employee e3 =
new Employee();
```

Creates:

```text
3 Objects
```

---

# Singleton Goal

```text
Only 1 Object

Shared Everywhere
```

---

# 9. Eager Singleton

## Definition

Object created immediately during class loading.

Example:

```java
class Singleton {

    private static final
    Singleton INSTANCE =
    new Singleton();

    private Singleton(){

    }

    public static Singleton
    getInstance(){

        return INSTANCE;

    }

}
```

---

# Usage

```java
Singleton obj =
Singleton.getInstance();
```

---

# Advantages

```text
Simple

Thread Safe
```

---

# Disadvantages

```text
Object Created Even If Not Used
```

---

# 10. Lazy Singleton

## Definition

Object created only when needed.

Example:

```java
class Singleton {

    private static
    Singleton instance;

    private Singleton(){

    }

    public static Singleton
    getInstance(){

        if(instance == null){

            instance =
            new Singleton();

        }

        return instance;

    }

}
```

---

# Advantages

```text
Memory Efficient
```

---

# Disadvantages

```text
Not Thread Safe
```

---

# 11. Thread-Safe Singleton

Example:

```java
public static synchronized
Singleton getInstance(){

    if(instance == null){

        instance =
        new Singleton();

    }

    return instance;

}
```

---

# Benefits

```text
Multiple Threads

↓

Single Object
```

---

# JVM View

```text
Thread 1

↓

getInstance()

↓

Object Created

↓

Returned To All Threads
```

---

# 12. Factory Pattern Basics

## Definition

Object creation delegated to factory method.

Instead of:

```java
new ChromeDriver();
```

Use:

```java
DriverFactory
.getDriver();
```

---

# Benefits

```text
Loose Coupling

Centralized Creation

Easy Maintenance
```

---

# Example

```java
class DriverFactory {

    static WebDriver
    getDriver(){

        return new ChromeDriver();

    }

}
```

---

# 13. Selenium Framework Example

Driver Factory:

```java
public class DriverFactory {

    private static
    WebDriver driver;

}
```

---

# Why Singleton?

Because:

```text
One Browser

↓

One Driver

↓

One Instance
```

---

# Page Objects

```java
LoginPage

HomePage

DashboardPage
```

Often created through:

```text
Factory Pattern
```

---

# 14. Real Project Example

Configuration Manager

```java
ConfigManager
```

Loads:

```text
URL

Username

Password

Environment
```

Only one instance required.

Therefore:

```text
Singleton Pattern
```

---

# 15. JVM Internals

Singleton Object Flow:

```text
Class Loaded

↓

Static Variable Created

↓

Singleton Object Created

↓

Reference Stored

↓

Shared Across Application
```

---

# Memory Diagram

```text
Method Area

Singleton Reference

↓

Heap

Singleton Object
```

---

# Common Interview Questions

## Q1. What is a Nested Class?

Class declared inside another class.

---

## Q2. How Many Types of Nested Classes Exist?

```text
4
```

* Static Nested
* Inner
* Local
* Anonymous

---

## Q3. Can Inner Class Access Private Members?

Yes.

---

## Q4. Can Static Nested Class Access Instance Variables Directly?

No.

---

## Q5. Why Use Anonymous Inner Class?

One-time implementation.

---

## Q6. What is Singleton Pattern?

Design pattern ensuring only one object exists.

---

## Q7. Why Constructor is Private in Singleton?

Prevent external object creation.

---

## Q8. Which Singleton is Thread Safe?

```text
Eager Singleton

OR

Synchronized Lazy Singleton
```

---

## Q9. What is Factory Pattern?

Pattern that centralizes object creation.

---

## Q10. Why Is Singleton Used In Selenium Frameworks?

```text
Single Driver Instance

Shared Configuration

Resource Optimization
```

---

# Revision Notes

```text
Nested Class
↓
Class Inside Class

Static Nested
↓
No Outer Object Needed

Inner Class
↓
Requires Outer Object

Local Class
↓
Inside Method

Anonymous Class
↓
No Name

Singleton
↓
One Object Only

Factory
↓
Creates Objects

Private Constructor
↓
Prevents Object Creation
```

---

# Interview Summary

```text
Static Nested Class
↓
Class Level

Inner Class
↓
Object Level

Anonymous Class
↓
One-Time Use

Singleton
↓
Single Instance

Factory Pattern
↓
Centralized Object Creation

Framework Design
↓
Uses Singleton + Factory
```

---

# End of Part 6

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-7.md

Topics:

* Object Cloning
* Shallow Copy
* Deep Copy
* Object Equality
* equals() Method
* hashCode() Method
* Object Class Internals
* toString() Method
* Immutable Objects
* Selenium & Framework Use Cases
* JVM Internals
* Interview Questions
