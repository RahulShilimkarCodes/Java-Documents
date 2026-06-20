# Java Variables Interview Master Guide
# Part 2 - Local, Instance, Static and Final Variables

## Table of Contents

1. Local Variables
2. Instance Variables
3. Static Variables
4. Final Variables
5. Memory Internals
6. Selenium Framework Examples
7. TestNG Framework Examples
8. REST Assured Examples
9. Interview Questions
10. MCQs
11. Quick Revision Notes

---

# 1. Local Variables

## Definition

Variables declared inside methods, constructors, or blocks.

```java
public void display() {
    int age = 25;
}
```

## Characteristics

- Stored in Stack Memory
- Scope limited to method/block
- No default value
- Must be initialized before use

Example:

```java
int x;
System.out.println(x);
```

Compilation Error

Why?

Local variables do not receive default values.

---

## Memory Representation

Stack

display()
------------
age = 25

Destroyed immediately after method execution.

---

## Interview Question

Why must local variables be initialized?

Answer:

Java does not assign default values to local variables because they exist temporarily and are expected to be explicitly initialized by developers.

---

# 2. Instance Variables

## Definition

Variables declared inside a class but outside methods.

```java
public class Employee {

    String name;
    int age;
}
```

## Characteristics

- Stored in Heap Memory
- Belong to object
- Receive default values
- Created when object is created

---

## Default Values

| Type | Default |
|--------|---------|
| int | 0 |
| long | 0L |
| double | 0.0 |
| boolean | false |
| String | null |
| Object | null |

---

## Example

```java
Employee emp = new Employee();

System.out.println(emp.age);
```

Output:

```text
0
```

---

## Heap Representation

Employee Object

-------------------
name = null
age = 0
-------------------

---

# 3. Static Variables

## Definition

Variables shared across all objects.

```java
class Employee {

    static String company = "Google";
}
```

---

## Characteristics

- Belong to class
- Single copy exists
- Shared by all objects
- Loaded when class loads

---

## Memory Storage

Metaspace

Employee.class
-------------------
company = Google
-------------------

---

## Example

```java
Employee e1 = new Employee();
Employee e2 = new Employee();

System.out.println(Employee.company);
```

Output:

Google

---

## Interview Question

Why use static variables?

Answer:

To share common data among all objects and reduce memory consumption.

---

# Static Variables in Selenium Framework

Most Asked Question

```java
public class DriverManager {

    public static WebDriver driver;
}
```

Why static?

Single driver instance accessible globally.

Benefits:

- Easy access
- Shared across framework

Disadvantages:

- Thread safety issues
- Parallel execution failures

---

# Singleton Alternative

```java
private static DriverManager instance;
```

More suitable for enterprise frameworks.

---

# 4. Final Variables

## Definition

Variable whose value cannot be changed.

```java
final int AGE = 25;
```

Invalid:

```java
AGE = 30;
```

Compilation Error

---

## Final Reference Variable

```java
final List<String> names = new ArrayList<>();
```

Allowed:

```java
names.add("Rahul");
```

Not Allowed:

```java
names = new ArrayList<>();
```

---

## final vs finally vs finalize

final

Keyword

finally

Exception Handling Block

finalize()

Garbage Collector Method

---

# Project Usage

```java
public static final String BASE_URL =
"https://api.company.com";
```

Common in automation frameworks.

---

# Memory Comparison

| Variable Type | Memory |
|---------------|---------|
| Local | Stack |
| Instance | Heap |
| Static | Metaspace |
| Final | Depends on declaration |

---

# Selenium Interview Example

Question:

Why should WebDriver not always be static?

Answer:

Static WebDriver breaks parallel execution because multiple threads overwrite the same driver instance.

---

# TestNG Example

Bad Design

```java
public static WebDriver driver;
```

Problem:

Parallel execution failures.

Better:

```java
private WebDriver driver;
```

or ThreadLocal.

---

# REST Assured Example

```java
public static RequestSpecification requestSpec;
```

Used for:

- Base URI
- Headers
- Authentication

Shared across tests.

---

# Top Interview Questions

1. Difference between Local and Instance Variable?
2. Difference between Instance and Static Variable?
3. Why local variables must be initialized?
4. Why instance variables get default values?
5. Can local variable be static?
6. Can static variable access non-static variable?
7. Why use final keyword?
8. Explain final reference variable.
9. Difference between final, finally and finalize?
10. Why static WebDriver is risky?

---

# MCQs

Q1. Local variables are stored in?

A. Heap
B. Stack
C. Metaspace
D. Method Area

Answer: B

---

Q2. Instance variables are stored in?

Answer: Heap

---

Q3. Static variables belong to?

Answer: Class

---

Q4. Can local variable have default value?

Answer: No

---

Q5. Can final variable be reassigned?

Answer: No

---

# Quick Revision Notes

LOCAL VARIABLE

- Method level
- Stack memory
- No default value
- Short lifetime

INSTANCE VARIABLE

- Object level
- Heap memory
- Default values
- One copy per object

STATIC VARIABLE

- Class level
- Shared across objects
- Loaded once
- Useful for constants

FINAL VARIABLE

- Constant value
- Cannot be reassigned
- Frequently used in frameworks

---

# Interview Cheat Sheet

Local = Stack

Instance = Heap

Static = Class Level

Final = Constant

Static + Final = Constant shared by all objects

Example:

```java
public static final String BASE_URL =
"https://company.com";
```

One of the most common patterns in Selenium and REST Assured frameworks.
