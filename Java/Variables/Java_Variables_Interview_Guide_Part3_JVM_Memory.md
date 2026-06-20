# Java Variables Interview Master Guide
# Part 3 - JVM Memory & Variable Storage Internals

## Table of Contents

1. JVM Architecture Overview
2. Class Loader Subsystem
3. Runtime Data Areas
4. Stack Memory Deep Dive
5. Heap Memory Deep Dive
6. Metaspace (Method Area)
7. String Constant Pool
8. Object Creation Process
9. Primitive vs Reference Storage
10. Garbage Collection Impact
11. Memory Leak Scenarios
12. Selenium Framework Memory Design
13. Interview Questions
14. Revision Notes

---

# 1. JVM Architecture Overview

JVM (Java Virtual Machine) executes Java bytecode.

Flow:

Source Code (.java)
        ↓
Compiler (javac)
        ↓
Bytecode (.class)
        ↓
JVM
        ↓
Machine Code

---

## Major Components

1. Class Loader
2. Runtime Memory Areas
3. Execution Engine
4. Garbage Collector
5. JNI
6. Native Libraries

---

# 2. Class Loader Subsystem

Responsible for loading classes into memory.

Example:

```java
Employee emp = new Employee();
```

Before object creation:

Employee.class must be loaded.

---

## Class Loading Phases

### Loading

Class file loaded into memory.

### Linking

Verification
Preparation
Resolution

### Initialization

Static variables initialized.

Example:

```java
static int count = 100;
```

Initialized during class loading.

---

# 3. Runtime Data Areas

JVM Memory Structure

```text
+-----------------------+
|     Metaspace         |
+-----------------------+
|         Heap          |
+-----------------------+
|       Stack           |
+-----------------------+
| Program Counter       |
+-----------------------+
| Native Method Stack   |
+-----------------------+
```

---

# 4. Stack Memory Deep Dive

Stores:

- Local Variables
- Method Calls
- Partial Results

Example:

```java
public void test() {
    int x = 10;
}
```

Memory:

```text
Stack Frame
-------------
x = 10
-------------
```

Destroyed after method completion.

---

## Stack Characteristics

- Thread specific
- Fast access
- Automatically managed
- No Garbage Collection required

---

## Stack Overflow Error

Example:

```java
public void test() {
    test();
}
```

Infinite recursion creates frames endlessly.

Result:

```text
StackOverflowError
```

---

# 5. Heap Memory Deep Dive

Stores:

- Objects
- Arrays
- Instance Variables

Example:

```java
Employee emp = new Employee();
```

Memory:

```text
Stack
------
emp -----> 0x101

Heap
------
Employee Object
name = null
age = 0
```

---

## Heap Regions

Modern JVM:

- Young Generation
- Survivor Space
- Old Generation

---

### Young Generation

New objects created here.

Example:

```java
new Employee();
```

---

### Old Generation

Long living objects move here.

---

# 6. Metaspace

Introduced in Java 8.

Stores:

- Class Metadata
- Static Variables
- Method Information

Example:

```java
static String company = "Google";
```

Stored in class metadata area.

---

## Why Metaspace Replaced PermGen?

Advantages:

- Dynamic sizing
- Better memory management
- Reduced OutOfMemory errors

---

# 7. String Constant Pool

One of the most important interview topics.

Example:

```java
String s1 = "Java";
String s2 = "Java";
```

Only one object created.

Memory:

```text
String Pool
------------
Java
------------
```

Both references point to same object.

---

## Using new Keyword

```java
String s1 = new String("Java");
```

Creates:

1. Pool Object
2. Heap Object

Total = 2 objects

---

## Interview Question

Why String is Immutable?

Benefits:

- Security
- Thread Safety
- Pool Optimization
- HashMap efficiency

---

# 8. Object Creation Process

Example:

```java
Employee emp = new Employee();
```

Step 1:

Class loaded.

Step 2:

Memory allocated in Heap.

Step 3:

Default values assigned.

Step 4:

Constructor executed.

Step 5:

Reference stored in Stack.

---

## Memory Diagram

```text
Stack
-------------
emp ---> 101
-------------

Heap
-------------
Employee
name = Rahul
age = 25
-------------
```

---

# 9. Primitive vs Reference Storage

Primitive

```java
int age = 25;
```

Stored directly in stack frame.

---

Reference

```java
Employee emp = new Employee();
```

Reference in Stack

Object in Heap

---

## Comparison

| Primitive | Reference |
|------------|------------|
| Value Stored | Address Stored |
| Faster | Slightly Slower |
| Fixed Size | Variable Size |
| Stack | Heap + Stack |

---

# 10. Garbage Collection Impact

Garbage Collector removes unused objects.

Example:

```java
Employee emp = new Employee();

emp = null;
```

Object becomes eligible for GC.

---

## Eligible != Immediately Removed

Interview Favorite Question

Eligibility does not guarantee immediate collection.

GC decides timing.

---

# Common GC Algorithms

- Serial GC
- Parallel GC
- G1 GC
- ZGC

---

# 11. Memory Leak Scenarios

Java can have memory leaks.

Example:

```java
List<Employee> list = new ArrayList<>();
```

Continuously adding objects:

```java
while(true) {
   list.add(new Employee());
}
```

Heap eventually fills.

---

## Selenium Memory Leak Example

Bad Practice:

```java
WebDriver driver = new ChromeDriver();
```

Without:

```java
driver.quit();
```

Resources remain allocated.

---

# 12. Selenium Framework Memory Design

## Driver Lifecycle

```java
@BeforeMethod
public void setup() {

    driver = new ChromeDriver();
}

@AfterMethod
public void teardown() {

    driver.quit();
}
```

Ensures memory cleanup.

---

## Static Driver Problem

```java
public static WebDriver driver;
```

Issues:

- Shared state
- Memory retention
- Parallel execution conflicts

---

## Better Design

```java
ThreadLocal<WebDriver> driver;
```

Thread-safe implementation.

---

# Frequently Asked Interview Questions

### Q1. Difference between Stack and Heap?

Stack:

Stores local variables and method calls.

Heap:

Stores objects and instance variables.

---

### Q2. Why Stack is faster?

Because memory allocation/deallocation is automatic and sequential.

---

### Q3. Where are static variables stored?

Metaspace (class metadata area).

---

### Q4. Where are String literals stored?

String Constant Pool.

---

### Q5. Why String Pool exists?

To save memory and improve performance.

---

### Q6. What causes StackOverflowError?

Excessive method calls or recursion.

---

### Q7. What causes OutOfMemoryError?

Heap memory exhaustion.

---

### Q8. Can Java have memory leaks?

Yes.

Unused references retained in collections are a common reason.

---

# Quick Revision Notes

JVM

- Executes bytecode
- Platform independent

STACK

- Local variables
- Method calls
- Thread specific

HEAP

- Objects
- Arrays
- Instance variables

METASPACE

- Class metadata
- Static members

STRING POOL

- Stores string literals
- Avoids duplicate objects

GC

- Removes unreachable objects

STACK OVERFLOW

- Too many stack frames

OUT OF MEMORY

- Heap exhausted

---

# One Minute Interview Cheat Sheet

Local Variable = Stack

Object = Heap

Reference = Stack

Static Variable = Metaspace

String Literal = String Pool

new Object() = Heap Allocation

GC = Cleans unreachable objects

StackOverflowError = Recursion

OutOfMemoryError = Heap Full

ThreadLocal = Better than static WebDriver for parallel execution

