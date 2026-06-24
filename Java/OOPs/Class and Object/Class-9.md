# Java-Classes-and-Objects-Master-Guide-Part-9.md

# Java Classes and Objects Master Guide

## Part 9 – Object Life Cycle, Garbage Collection & JVM Memory Management

---

# Table of Contents

1. Introduction to Object Life Cycle
2. Stages of Object Life Cycle
3. Object Creation Process
4. Object Usage
5. Object Eligibility for Garbage Collection
6. Garbage Collection Fundamentals
7. How Garbage Collector Works
8. Reachability Analysis
9. Types of References
10. Strong References
11. Weak References
12. Soft References
13. Phantom References
14. finalize() Method
15. Memory Leaks in Java
16. JVM Heap Internals
17. Selenium Framework Memory Management
18. Interview Questions
19. Revision Notes

---

# Introduction

When developers write:

```java
Employee emp =
new Employee();
```

most people think:

```text
Object Created

↓

Program Uses It

↓

Program Ends
```

But internally JVM performs many operations.

The actual lifecycle is:

```text
Object Creation

↓

Memory Allocation

↓

Initialization

↓

Usage

↓

Eligible For GC

↓

Garbage Collection

↓

Memory Reclaimed
```

Understanding this topic is extremely important for:

* Java Interviews
* Product-Based Companies
* JVM Internals Questions
* Selenium Framework Design
* Performance Optimization

---

# 1. What is Object Life Cycle?

## Definition

Object Life Cycle refers to all stages through which an object passes during its existence in JVM.

---

# Complete Life Cycle

```text
Created

↓

Initialized

↓

Used

↓

Unreachable

↓

Garbage Collected

↓

Memory Reclaimed
```

---

# Real World Analogy

Think of a car.

```text
Manufactured

↓

Purchased

↓

Used

↓

Abandoned

↓

Scrapped
```

Similarly:

```text
Object Created

↓

Used

↓

No Longer Needed

↓

Collected By JVM
```

---

# 2. Stages of Object Life Cycle

### Stage 1

```text
Class Loading
```

---

### Stage 2

```text
Object Creation
```

---

### Stage 3

```text
Object Initialization
```

---

### Stage 4

```text
Object Usage
```

---

### Stage 5

```text
Object Becomes Unreachable
```

---

### Stage 6

```text
Garbage Collection
```

---

# Visualization

```text
Class Loaded

↓

new Employee()

↓

Object Created

↓

Used

↓

Reference Lost

↓

GC Runs

↓

Memory Freed
```

---

# 3. Object Creation Process

Code:

```java
Employee emp =
new Employee();
```

---

# JVM Steps

### Step 1

Class Loaded

```text
Employee.class
```

loaded into memory.

---

### Step 2

Heap Memory Allocated

```text
Heap

↓

Memory Reserved
```

---

### Step 3

Default Values Assigned

```text
int → 0

boolean → false

String → null
```

---

### Step 4

Constructor Executes

```java
Employee()
```

---

### Step 5

Reference Returned

```java
emp
```

receives object address.

---

# Memory Diagram

```text
STACK
-----

emp
 |
 |
 V

HEAP
-----

Employee Object
```

---

# 4. Object Usage

Once created:

```java
emp.setName("Rahul");
```

Object becomes active.

---

# During Usage

JVM maintains:

```text
Reference

↓

Object

↓

State
```

---

# Example

```java
emp.name =
"Rahul";
```

Object state changes.

---

# 5. When Does Object Become Eligible for GC?

Many developers think:

```text
Object Deleted
```

But Java does not allow explicit deletion.

There is no:

```java
delete object;
```

statement.

---

# Instead

Object becomes:

```text
Eligible For Garbage Collection
```

---

# Scenario 1

Reference Set To Null

```java
Employee emp =
new Employee();

emp = null;
```

---

# Memory

```text
Heap

Employee Object

No Reference
```

Eligible for GC.

---

# Scenario 2

Reference Reassigned

```java
Employee e1 =
new Employee();

e1 =
new Employee();
```

First object becomes unreachable.

---

# Memory

```text
Object1
↓

No Reference

↓

GC Candidate
```

---

# Scenario 3

Local Variable Ends

```java
void test(){

    Employee emp =
    new Employee();

}
```

Method exits.

Reference disappears.

Object becomes eligible.

---

# 6. What is Garbage Collection?

## Definition

Garbage Collection is JVM's automatic process of reclaiming memory occupied by unused objects.

---

# Why GC Exists?

Without GC:

```text
Program Creates Objects

↓

Memory Keeps Growing

↓

OutOfMemoryError
```

---

# GC Solution

```text
Unused Objects

↓

Detected

↓

Removed

↓

Memory Released
```

---

# Benefits

```text
Automatic Memory Management

Reduced Memory Leaks

Safer Programming
```

---

# 7. How Garbage Collector Works

Many beginners think:

```text
GC Deletes Object Immediately
```

Wrong.

---

# Actual Flow

```text
Object Unreachable

↓

Marked

↓

GC Runs Later

↓

Memory Reclaimed
```

---

# Important Point

JVM decides:

```text
When To Run GC

How Often To Run GC
```

Developer cannot force it.

---

# System.gc()

Example:

```java
System.gc();
```

Meaning:

```text
Request JVM To Run GC
```

Not guaranteed.

---

# Interview Question

Does System.gc() guarantee garbage collection?

Answer:

```text
No
```

Only requests JVM.

---

# 8. Reachability Analysis

Modern JVM uses:

```text
Reachability Analysis
```

to determine whether object is alive.

---

# Concept

Starting point:

```text
GC Roots
```

Examples:

```text
Stack References

Static Variables

Active Threads
```

---

# Rule

If object is reachable from GC Root:

```text
Alive
```

Else:

```text
Garbage
```

---

# Diagram

```text
GC Root

↓

Employee

↓

Address

↓

City
```

All reachable.

---

# Unreachable Example

```text
GC Root

↓

Employee

Address
```

If Address disconnected:

```text
Address

↓

Garbage
```

---

# 9. Types of References

Java provides:

```text
Strong Reference

Soft Reference

Weak Reference

Phantom Reference
```

---

# 10. Strong References

Default references.

Example:

```java
Employee emp =
new Employee();
```

---

# Characteristics

```text
Object Cannot Be Collected

As Long As Reference Exists
```

---

# Most Common Type

Used in:

```text
Almost Every Java Program
```

---

# 11. Weak References

Example:

```java
WeakReference<Employee>
ref =
new WeakReference<>(
new Employee()
);
```

---

# Behavior

```text
GC Runs

↓

Object Removed

Even If Weak Reference Exists
```

---

# Usage

```text
Caching

Memory Sensitive Applications
```

---

# 12. Soft References

Example:

```java
SoftReference<Employee>
ref =
new SoftReference<>(
new Employee()
);
```

---

# Behavior

```text
Object Retained

Until Memory Becomes Low
```

---

# Usage

```text
Image Caches

Large Data Caches
```

---

# Difference

```text
Weak Reference

↓

Removed Quickly

Soft Reference

↓

Retained Longer
```

---

# 13. Phantom References

Most advanced reference type.

Example:

```java
PhantomReference<Employee>
```

---

# Purpose

Track object cleanup.

---

# Usage

```text
Advanced Memory Management

JVM Framework Development
```

---

# Rarely Asked

Mostly asked in:

```text
Senior Java Interviews
```

---

# 14. finalize() Method

Before Java 9:

```java
protected void finalize(){

}
```

could be overridden.

---

# Example

```java
@Override

protected void finalize(){

    System.out.println(
    "Cleanup"
    );

}
```

---

# Problems

```text
Unpredictable

Slow

Not Reliable
```

---

# Current Status

```text
Deprecated

Avoid Usage
```

---

# Modern Alternative

```text
try-with-resources

AutoCloseable
```

---

# 15. Memory Leaks in Java

Many believe:

```text
Java Has No Memory Leaks
```

Wrong.

---

# Example

```java
List<Employee> list =
new ArrayList<>();
```

Adding objects:

```java
list.add(emp);
```

---

# Problem

Even if object is unused:

```text
List Still Holds Reference
```

GC cannot remove it.

---

# Memory Leak

```text
Object Exists

↓

Still Referenced

↓

Never Collected
```

---

# Common Causes

```text
Static Collections

Caches

Listeners

Large Maps

Thread Locals
```

---

# 16. JVM Heap Internals

Heap divided into:

```text
Young Generation

Old Generation

Metaspace
```

---

# Young Generation

Stores:

```text
New Objects
```

---

# Old Generation

Stores:

```text
Long-Lived Objects
```

---

# Metaspace

Stores:

```text
Class Metadata
```

---

# Heap Diagram

```text
Heap

├── Young Generation

├── Old Generation

└── Metaspace
```

---

# GC Flow

```text
New Object

↓

Young Gen

↓

Survives

↓

Old Gen

↓

Eventually Collected
```

---

# 17. Selenium Framework Memory Management

Large Selenium frameworks create:

```text
WebDriver

Page Objects

Test Data Objects

Reports

Screenshots
```

---

# Common Memory Problems

```text
Driver Not Closed

Large Logs

Unused Collections

Screenshot Storage
```

---

# Best Practices

```java
driver.quit();
```

---

```java
list.clear();
```

---

```java
extent.flush();
```

---

# Real Framework Example

Wrong:

```java
static List<String> logs =
new ArrayList<>();
```

Never cleared.

Memory grows continuously.

---

# Better

```java
logs.clear();
```

after execution.

---

# Common Interview Questions

## Q1. What is Garbage Collection?

Automatic memory cleanup process.

---

## Q2. Can Developer Delete Objects Explicitly?

No.

---

## Q3. What Makes Object Eligible For GC?

No reachable references.

---

## Q4. Does System.gc() Guarantee GC?

No.

---

## Q5. What is Reachability Analysis?

Technique used to determine whether object is alive.

---

## Q6. What are GC Roots?

```text
Stack References

Static Variables

Threads
```

---

## Q7. Difference Between Soft and Weak Reference?

```text
Soft

↓

Retained Longer

Weak

↓

Collected Earlier
```

---

## Q8. What is Memory Leak?

Unused object still referenced.

---

## Q9. Why Was finalize() Deprecated?

```text
Unpredictable

Slow

Unsafe
```

---

## Q10. Which Memory Area Stores Objects?

```text
Heap
```

---

## Q11. Which Memory Area Stores Local Variables?

```text
Stack
```

---

## Q12. Which Memory Area Stores Class Metadata?

```text
Metaspace
```

---

# Revision Notes

```text
Object Lifecycle
↓
Create → Use → GC

GC
↓
Automatic Cleanup

Reachability
↓
Determines Alive Objects

Strong Reference
↓
Normal Reference

Weak Reference
↓
Collected Quickly

Soft Reference
↓
Collected During Memory Pressure

Phantom Reference
↓
Cleanup Tracking

Heap
↓
Stores Objects

Stack
↓
Stores References

Metaspace
↓
Stores Class Metadata
```

---

# Interview Summary

```text
new Keyword
↓
Creates Object

GC
↓
Reclaims Memory

Reachability Analysis
↓
Determines Garbage

Heap
↓
Object Storage

Memory Leak
↓
Unwanted References

Soft Reference
↓
Cache Friendly

Weak Reference
↓
Short-Lived Cache

Modern Java
↓
Avoid finalize()
```

---

# End of Part 9

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-10.md

Topics:

* Complete Object Class Deep Dive
* Reflection API
* Runtime Object Inspection
* Class Class
* getClass()
* ClassLoader Internals
* Dynamic Object Creation
* Annotations Basics
* Selenium Reflection Usage
* Framework Design Concepts
* Advanced Interview Questions
