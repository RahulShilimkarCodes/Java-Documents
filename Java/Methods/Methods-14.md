# Java Methods Master Guide

# Part 14 - JVM Internals, Stack Frames & Memory Management

---

# Table of Contents

1. Introduction
2. What Happens When a Java Program Starts?
3. JVM Architecture Overview
4. Class Loader Subsystem
5. Runtime Data Areas
6. Method Area / Metaspace
7. Heap Memory
8. Stack Memory
9. Program Counter (PC Register)
10. Native Method Stack
11. Stack Frames Deep Dive
12. Local Variable Table
13. Operand Stack
14. Dynamic Linking
15. Method Invocation Process
16. Method Return Process
17. Object Creation Internals
18. String Pool Internals
19. Static Variables Memory
20. Recursion & StackOverflowError
21. Garbage Collection Internals
22. Memory Leaks in Java
23. JIT Compiler
24. Method Inlining
25. Escape Analysis
26. Selenium Framework Memory Usage
27. API Framework Memory Usage
28. JVM Interview Questions
29. Ultimate Revision Notes
30. Final Cheat Sheet

---

# 1. Introduction

This chapter is one of the most important topics for:

```text
Java Developer Interviews

Automation Testing Interviews

SDET Interviews

Senior Automation Engineer Interviews

Performance Engineering Interviews
```

---

Interviewers frequently ask:

```text
What happens when a Java method executes?

How is memory allocated?

Where are objects stored?

What is StackOverflowError?

What is Heap Memory?

What is Metaspace?
```

---

# 2. What Happens When a Java Program Starts?

Example:

```java
public class Main {

    public static void main(String[] args){

        System.out.println("Hello");
    }
}
```

Execution Flow:

```text
java Main

↓

JVM Starts

↓

Class Loader Loads Main.class

↓

main() Method Located

↓

Stack Frame Created

↓

main() Executes

↓

Program Ends
```

---

# 3. JVM Architecture Overview

Simplified JVM Architecture:

```text
+----------------------+
| Class Loader         |
+----------------------+

+----------------------+
| Runtime Data Areas   |
+----------------------+

+----------------------+
| Execution Engine     |
+----------------------+

+----------------------+
| Garbage Collector    |
+----------------------+
```

---

Interview Answer:

```text
JVM consists of Class Loader,
Runtime Memory Areas,
Execution Engine and Garbage Collector.
```

---

# 4. Class Loader Subsystem

Purpose:

```text
Loads .class files into JVM memory.
```

---

Class Loading Stages

```text
Loading

↓

Linking

↓

Initialization
```

---

Loading:

```text
Read .class file
```

---

Linking:

```text
Verification

Preparation

Resolution
```

---

Initialization:

```text
Static variables initialized
```

---

Example:

```java
static int count = 100;
```

initialized during class loading.

---

# 5. Runtime Data Areas

Main JVM Memory Areas:

```text
Method Area (Metaspace)

Heap

Stack

PC Register

Native Method Stack
```

---

Interview Favorite Topic.

---

# 6. Method Area / Metaspace

Java 8+

```text
Method Area

↓

Metaspace
```

---

Stores:

```text
Class Metadata

Method Metadata

Static Variables

Runtime Constants
```

---

Example:

```java
class Employee{

    static int count = 100;
}
```

---

Stored Here:

```text
Metaspace
```

---

One Copy Shared Across JVM.

---

# 7. Heap Memory

Most Important Memory Area.

Purpose:

```text
Stores Objects
```

---

Example:

```java
Employee emp =
new Employee();
```

---

Memory:

```text
HEAP

Employee Object
```

---

Characteristics:

```text
Shared Memory

GC Managed

Largest Memory Region
```

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

# 8. Stack Memory

Purpose:

```text
Stores Method Execution Data
```

---

Contains:

```text
Method Calls

Local Variables

References

Return Information
```

---

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

# 9. Program Counter (PC Register)

Each thread gets its own:

```text
PC Register
```

---

Stores:

```text
Current Instruction Address
```

---

Purpose:

```text
Track Next Instruction
```

---

Rarely Asked But Important.

---

# 10. Native Method Stack

Stores execution information for:

```text
Native Methods
```

---

Example:

```java
System.loadLibrary()
```

---

Used for:

```text
C

C++

OS Calls
```

---

# 11. Stack Frames Deep Dive

Most Important JVM Topic.

Example:

```java
main();

login();

validate();
```

---

Memory:

```text
+---------------+
| validate()    |
+---------------+
| login()       |
+---------------+
| main()        |
+---------------+
```

---

Each block is:

```text
Stack Frame
```

---

Created:

```text
Method Call
```

Destroyed:

```text
Method Completion
```

---

# 12. Local Variable Table

Inside every stack frame:

```text
Local Variable Table
```

---

Example:

```java
public void add(int a,int b){

    int sum = a+b;
}
```

---

Stored:

```text
a

b

sum
```

---

Inside:

```text
Local Variable Table
```

---

# 13. Operand Stack

Used for:

```text
Intermediate Calculations
```

---

Example:

```java
int c = a+b;
```

---

Execution:

```text
Push a

Push b

Add

Store c
```

---

Interview Level Topic.

---

# 14. Dynamic Linking

Purpose:

```text
Connect Method References
To Actual Methods
```

---

Example:

```java
employee.login();
```

---

JVM Locates:

```text
Actual login() Method
```

during execution.

---

Required For:

```text
Runtime Polymorphism
```

---

# 15. Method Invocation Process

Example:

```java
login();
```

---

Execution:

```text
Method Found

↓

Stack Frame Created

↓

Parameters Passed

↓

Execution Starts

↓

Result Returned

↓

Frame Removed
```

---

# 16. Method Return Process

Example:

```java
int add(){

   return 100;
}
```

---

Execution:

```text
Return Value Generated

↓

Sent To Caller

↓

Current Frame Destroyed
```

---

Interview Question:

```text
What happens after method returns?
```

Answer:

```text
Stack Frame Removed
```

---

# 17. Object Creation Internals

Example:

```java
Employee emp =
new Employee();
```

---

Steps:

```text
Class Loaded

↓

Heap Memory Allocated

↓

Default Values Assigned

↓

Constructor Executes

↓

Reference Returned
```

---

Memory Diagram:

```text
STACK

emp
 |
 v

HEAP

Employee Object
```

---

# 18. String Pool Internals

Important Interview Topic.

Example:

```java
String s1 = "Java";
String s2 = "Java";
```

---

Memory:

```text
String Pool

"Java"
```

---

Both References:

```text
Point To Same Object
```

---

Interview Question:

```java
s1 == s2
```

Output:

```text
true
```

---

Reason:

```text
String Pool Reuse
```

---

# 19. Static Variables Memory

Example:

```java
static int count = 100;
```

---

Stored In:

```text
Metaspace
```

---

Characteristics:

```text
One Copy

Shared

Class Level
```

---

Not Stored In Objects.

---

# 20. Recursion & StackOverflowError

Example:

```java
public void test(){

    test();
}
```

---

Execution:

```text
Frame

Frame

Frame

Frame

Frame

...
```

---

Eventually:

```text
Stack Memory Full
```

---

Result:

```text
StackOverflowError
```

---

Interview Answer:

```text
Infinite recursion continuously creates
stack frames until stack memory is exhausted.
```

---

# 21. Garbage Collection Internals

Purpose:

```text
Automatically Free Heap Memory
```

---

Example:

```java
Employee emp =
new Employee();

emp = null;
```

---

Object:

```text
Unreachable
```

---

Becomes:

```text
Eligible For GC
```

---

GC Responsibilities:

```text
Detect Unused Objects

Reclaim Heap Memory
```

---

# 22. Memory Leaks in Java

Interview Favorite.

Java Can Have Memory Leaks.

Example:

```java
Map<String,Object> cache =
new HashMap<>();
```

---

Continuously Add Data:

```text
Objects Never Removed
```

---

Result:

```text
Heap Memory Growth
```

---

Eventually:

```text
OutOfMemoryError
```

---

# 23. JIT Compiler

Execution Engine Component.

Purpose:

```text
Convert Bytecode

↓

Machine Code
```

---

Benefits:

```text
Faster Execution

Optimization
```

---

Interview Question:

```text
Why Is Java Fast?
```

Answer:

```text
JIT Compiler Optimizations
```

---

# 24. Method Inlining

Advanced JVM Optimization.

Example:

```java
int getValue(){

    return 10;
}
```

---

Instead Of:

```text
Calling Method Repeatedly
```

JVM May Replace With:

```text
10
```

directly.

---

Benefits:

```text
Reduce Method Call Cost
```

---

# 25. Escape Analysis

Advanced JVM Optimization.

Purpose:

```text
Determine Whether Object
Escapes Current Method
```

---

If Not:

```text
Allocate Efficiently
```

---

Benefits:

```text
Better Performance
```

---

# 26. Selenium Framework Memory Usage

Example:

```java
LoginPage page =
new LoginPage(driver);
```

---

Memory:

```text
Page Object

↓

Heap
```

---

Reference:

```text
Stack
```

---

Screenshots:

```text
Stored On Disk
```

---

Driver:

```text
Heap Objects
```

---

# 27. API Framework Memory Usage

Example:

```java
Response response =
given().get();
```

---

Response Object:

```text
Heap
```

---

Reference:

```text
Stack
```

---

JSON Data:

```text
Heap Memory
```

---

# 28. JVM Interview Questions

### Q1 Where Are Objects Stored?

```text
Heap
```

---

### Q2 Where Are References Stored?

```text
Stack
```

---

### Q3 What Is Metaspace?

```text
Stores Class Metadata
```

---

### Q4 What Is Stack Frame?

```text
Memory Block For Method Execution
```

---

### Q5 Why StackOverflowError Occurs?

```text
Infinite Stack Frame Creation
```

---

### Q6 What Is Garbage Collection?

```text
Automatic Heap Cleanup
```

---

### Q7 What Is JIT?

```text
Bytecode To Machine Code Compiler
```

---

### Q8 What Causes OutOfMemoryError?

```text
Heap Exhaustion
```

---

# 29. Ultimate Revision Notes

```text
Heap

Stores Objects

Stack

Stores Method Calls

Metaspace

Stores Class Metadata

PC Register

Current Instruction

Stack Frame

Per Method Call

String Pool

Shared String Objects

GC

Heap Cleanup

JIT

Performance Optimization
```

---

# 30. Final Cheat Sheet

```text
JVM

↓

Class Loader

↓

Runtime Data Areas

├─ Heap
├─ Stack
├─ Metaspace
├─ PC Register
└─ Native Stack

↓

Execution Engine

↓

Garbage Collector

Objects → Heap

References → Stack

Static Variables → Metaspace

Method Call → Stack Frame

Recursion → Multiple Frames

Infinite Recursion

↓

StackOverflowError

Unused Objects

↓

Garbage Collection
```

---

# Interview Takeaway

If interviewer asks:

```text
Explain what happens when a method executes in Java.
```

Strong Answer:

```text
When a method is invoked, the JVM creates a new
stack frame in the thread's stack memory.

The frame contains local variables,
parameters, operand stack and return information.

The method executes using this frame.

When execution completes, the return value is
sent back to the caller and the stack frame is removed.

Objects used by the method reside in heap memory,
while references and local variables remain in stack memory.
```

---

# End of Java Methods Master Guide

### Complete Coverage

```text
Part 1  → Method Fundamentals & JVM Execution
Part 2  → Parameters & Arguments
Part 3  → Return Types
Part 4  → Method Overloading
Part 5  → Method Overriding
Part 6  → Pass By Value
Part 7  → Varargs & Recursion
Part 8  → Static vs Instance Methods
Part 9  → Advanced Method Concepts
Part 10 → Advanced Methods & Interview Mastery
Part 11 → Complete Revision Handbook
Part 12 → Final Revision Notes
Part 13 → Selenium/TestNG/API Framework Methods
Part 14 → JVM Internals & Memory Management
```

### Next Guide

```text
Java OOP Master Guide

Part 1 → Class, Object & Memory Model
Part 2 → Constructors
Part 3 → Encapsulation
Part 4 → Inheritance
Part 5 → Polymorphism
Part 6 → Abstraction
Part 7 → Interfaces
Part 8 → Association, Aggregation & Composition
Part 9 → Object Class & equals/hashCode
Part 10 → OOP Design Patterns
Part 11 → OOP Interview Handbook
Part 12 → OOP Final Revision
```
