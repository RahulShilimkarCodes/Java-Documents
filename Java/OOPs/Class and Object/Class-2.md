# Java-Classes-and-Objects-Master-Guide-Part-2.md

# Java Classes and Objects Master Guide

## Part 2 – Instance Variables, Reference Variables & Object Creation Internals

---

# Table of Contents

1. Instance Variables
2. Local Variables
3. Reference Variables
4. Difference Between Instance, Local and Reference Variables
5. Object References Explained
6. Multiple References to Same Object
7. Null References
8. Object Initialization
9. Accessing Class Members
10. Multiple Objects Creation
11. JVM Internals During Object Creation
12. Memory Diagrams
13. Real-World Examples
14. Interview Questions
15. Revision Notes

---

# Introduction

In Part 1, we learned:

```text
Class
↓
Blueprint

Object
↓
Instance Created From Blueprint
```

However, most Java interview questions are actually asked around:

```text
Variables

↓

References

↓

Object Creation

↓

Memory Allocation

↓

JVM Internals
```

Understanding these concepts is critical for:

* Core Java Interviews
* Selenium Framework Interviews
* API Automation Interviews
* JVM-Based Questions
* Product-Based Company Interviews

---

# 1. What are Instance Variables?

## Definition

Variables declared inside a class but outside methods, constructors, and blocks are called Instance Variables.

Example:

```java
class Employee {

    String name;
    int id;
    double salary;

}
```

Here:

```text
name
id
salary
```

are instance variables.

---

## Why Called Instance Variables?

Because every object (instance) gets its own copy.

Example:

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee();
```

Memory:

```text
e1 Object
---------
name
id
salary

e2 Object
---------
name
id
salary
```

Each object has separate values.

---

# Characteristics of Instance Variables

### Stored In

```text
Heap Memory
```

### Lifetime

```text
Until Object Is Destroyed
```

### Default Values

Java automatically initializes them.

Example:

```java
class Test {

    int number;
    boolean flag;
    String name;

}
```

Values:

```text
number = 0

flag = false

name = null
```

---

# 2. What are Local Variables?

## Definition

Variables declared inside methods, constructors, or blocks.

Example:

```java
public void display() {

    int age = 25;

}
```

Here:

```text
age
```

is a local variable.

---

## Characteristics

### Stored In

```text
Stack Memory
```

### Lifetime

```text
Method Execution Only
```

### Default Value

No default value.

Example:

```java
public void test() {

    int x;

    System.out.println(x);

}
```

Compiler Error:

```text
Variable x might not have been initialized
```

---

# Local Variable Memory

```text
Method Starts
↓
Variable Created

Method Ends
↓
Variable Destroyed
```

---

# 3. What are Reference Variables?

## Definition

Variables that store addresses (references) of objects.

Example:

```java
Employee emp =
new Employee();
```

Here:

```text
emp
```

is a reference variable.

---

## Important Point

Reference variable does NOT store object.

It stores address of object.

Visualization:

```text
emp
 |
 |
 V

Employee Object
```

---

# Reference Variable Example

```java
Employee emp1 =
new Employee();

Employee emp2 =
new Employee();
```

Memory:

```text
emp1 → Object1

emp2 → Object2
```

---

# 4. Difference Between Instance, Local and Reference Variables

| Feature       | Instance Variable | Local Variable  | Reference Variable     |
| ------------- | ----------------- | --------------- | ---------------------- |
| Location      | Inside Class      | Inside Method   | Outside/Inside Methods |
| Memory        | Heap              | Stack           | Stack                  |
| Default Value | Yes               | No              | Null                   |
| Lifetime      | Object Lifetime   | Method Lifetime | Variable Lifetime      |

---

# 5. Object References Explained

Consider:

```java
Employee emp =
new Employee();
```

Internally:

### Step 1

```text
Memory Allocated
```

### Step 2

```text
Object Created
```

### Step 3

```text
Constructor Executed
```

### Step 4

```text
Reference Returned
```

### Step 5

```text
Reference Assigned To emp
```

---

## Diagram

```text
Stack

emp
 |
 |
 V

Heap

Employee Object
```

---

# 6. Multiple References to Same Object

Example:

```java
Employee emp1 =
new Employee();

Employee emp2 =
emp1;
```

Memory:

```text
emp1
  \
   \
    \
     > Employee Object
    /
   /
emp2
```

---

## Example

```java
emp1.name = "Rahul";

System.out.println(
emp2.name
);
```

Output:

```text
Rahul
```

Why?

Because both references point to same object.

---

# Interview Question

How many objects?

```java
Employee e1 =
new Employee();

Employee e2 =
e1;
```

Answer:

```text
1 Object

2 References
```

---

# 7. Null References

Example:

```java
Employee emp =
null;
```

Meaning:

```text
Reference Exists

↓

Object Does Not Exist
```

---

## Accessing Null Reference

```java
emp.name = "Java";
```

Output:

```text
NullPointerException
```

---

# Why Null Is Important?

Most runtime failures occur due to:

```text
NullPointerException
```

One of the most asked interview topics.

---

# 8. Object Initialization

Object variables can be initialized in multiple ways.

---

## Method 1 – Using Reference

```java
Employee emp =
new Employee();

emp.name =
"Rahul";

emp.id =
101;
```

---

## Method 2 – Using Method

```java
class Employee {

    void setData(
    String name,
    int id
    ){

    }

}
```

---

## Method 3 – Using Constructor

```java
Employee emp =
new Employee(
"Rahul",
101
);
```

Most preferred approach.

---

# 9. Accessing Class Members

Example:

```java
class Employee {

    String name;

}
```

Object:

```java
Employee emp =
new Employee();

emp.name =
"Rahul";
```

Access:

```java
System.out.println(
emp.name
);
```

Output:

```text
Rahul
```

---

## Dot Operator

Used to access:

```text
Variables

Methods

Constructors
```

Example:

```java
emp.name

emp.work()
```

---

# 10. Multiple Objects Creation

Example:

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee();

Employee e3 =
new Employee();
```

Memory:

```text
e1 → Object1

e2 → Object2

e3 → Object3
```

---

## Benefits

Every object maintains independent state.

Example:

```java
e1.name = "A";

e2.name = "B";

e3.name = "C";
```

---

# 11. JVM Internals During Object Creation

Code:

```java
Employee emp =
new Employee();
```

---

## Step 1

Class Loading

```text
Employee.class Loaded
```

---

## Step 2

Memory Allocation

```text
Heap Memory Allocated
```

---

## Step 3

Default Initialization

```text
String → null

int → 0

boolean → false
```

---

## Step 4

Constructor Execution

```text
Constructor Called
```

---

## Step 5

Reference Assignment

```text
Reference Stored In Stack
```

---

# Complete Flow

```text
new Employee()

↓

Heap Allocation

↓

Default Initialization

↓

Constructor Execution

↓

Reference Returned

↓

Stored In emp
```

---

# 12. Memory Diagram

Example:

```java
Employee emp =
new Employee();
```

Memory:

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

name = null

id = 0
```

---

# 13. Real-World Example

Class:

```java
class Car {

    String brand;

}
```

Objects:

```java
Car c1 =
new Car();

Car c2 =
new Car();
```

Values:

```java
c1.brand =
"BMW";

c2.brand =
"Audi";
```

Memory:

```text
BMW Object

Audi Object
```

Independent objects.

---

# Common Interview Questions

## Q1. Where Are Objects Stored?

```text
Heap Memory
```

---

## Q2. Where Are References Stored?

```text
Stack Memory
```

---

## Q3. Does Reference Variable Store Object?

No.

Stores address of object.

---

## Q4. How Many Objects?

```java
Employee e1 =
new Employee();

Employee e2 =
e1;
```

Answer:

```text
1 Object

2 References
```

---

## Q5. What Happens If Reference Becomes Null?

Object becomes inaccessible.

Eligible for:

```text
Garbage Collection
```

---

## Q6. Do Local Variables Get Default Values?

No.

---

## Q7. Do Instance Variables Get Default Values?

Yes.

Example:

```text
int → 0

boolean → false

String → null
```

---

# Revision Notes

```text
Instance Variable
↓
Inside Class

Local Variable
↓
Inside Method

Reference Variable
↓
Stores Address

Object
↓
Heap Memory

Reference
↓
Stack Memory

Multiple References
↓
Can Point To Same Object

Null Reference
↓
No Object

new Keyword
↓
Creates Object

Constructor
↓
Initializes Object
```

---

# Interview Summary

```text
Class
↓
Blueprint

Object
↓
Heap Memory

Reference
↓
Stack Memory

Instance Variable
↓
Belongs To Object

Local Variable
↓
Belongs To Method

One Object
↓
Many References Possible
```

---

# End of Part 2

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-3.md

Topics:

* Constructors Introduction
* Default Constructor
* Parameterized Constructor
* Constructor Overloading
* Constructor Chaining
* this Keyword
* Object Initialization Through Constructors
* JVM Constructor Execution Flow
* Interview Questions
* Real Project Examples
