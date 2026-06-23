# Java Methods Master Guide

# Part 11 - Complete Methods Revision & Interview Handbook

---

# Table of Contents

1. Methods Complete Roadmap
2. Methods Fundamentals Revision
3. Method Components Revision
4. Method Execution Flow in JVM
5. Method Memory Model
6. Parameter Passing Revision
7. Return Type Revision
8. Method Overloading Revision
9. Method Overriding Revision
10. Static vs Instance Methods Revision
11. Varargs Revision
12. Recursion Revision
13. Method Chaining Revision
14. Builder Pattern Revision
15. Framework Design Revision
16. Selenium Project Scenarios
17. API Framework Scenarios
18. Top 50 Interview Questions
19. One-Day Interview Preparation Notes
20. Ultimate Methods Cheat Sheet

---

# 1. Methods Complete Roadmap

Everything learned in Methods Guide:

```text
Methods
│
├── Method Declaration
├── Method Definition
├── Method Calling
├── Parameters
├── Arguments
├── Return Types
├── Method Memory
├── Pass By Value
├── Method Overloading
├── Method Overriding
├── Static Methods
├── Instance Methods
├── Varargs
├── Recursion
├── Lambda Methods
├── Method References
├── Method Chaining
├── Builder Pattern
└── Framework Design
```

---

# 2. Methods Fundamentals Revision

Definition:

```text
A Method is a reusable block of code
that performs a specific task.
```

---

Example:

```java
public void login(){

    System.out.println("Login Success");
}
```

---

Benefits:

```text
Code Reusability

Maintainability

Readability

Modularity

Reduced Duplication
```

---

Interview Answer:

```text
Methods help organize code into reusable,
maintainable, and logically separated units.
```

---

# 3. Method Components Revision

Method Structure:

```java
accessModifier returnType methodName(parameters){

    // body
}
```

---

Example:

```java
public int add(int a,int b){

    return a+b;
}
```

---

Breakdown:

```text
public      → Access Modifier

int         → Return Type

add         → Method Name

(int a,int b)
            → Parameters

return
            → Returned Value
```

---

# 4. Method Execution Flow in JVM

Example:

```java
public static void main(String[] args){

    greet();
}
```

---

Execution:

```text
JVM Starts

↓

main()

↓

greet()

↓

greet Finishes

↓

main Finishes

↓

Program Ends
```

---

Every method call creates:

```text
Stack Frame
```

---

# 5. Method Memory Model

Example:

```java
display();
```

---

Memory:

```text
JVM Stack

+-------------+
| display()   |
+-------------+
| main()      |
+-------------+
```

---

After display() finishes:

```text
+-------------+
| main()      |
+-------------+
```

---

Interview Point:

```text
Each method call creates
a separate stack frame.
```

---

# 6. Parameter Passing Revision

Most Important Interview Question.

---

Java:

```text
Always Pass By Value
```

---

Primitive Example:

```java
int x = 10;

modify(x);
```

Copy:

```text
10 → 10
```

---

Object Example:

```java
Employee e =
new Employee();
```

Copy:

```text
Reference Value Copied
```

---

Interview Answer:

```text
Java always passes copies.

Primitive → value copied

Object → reference value copied
```

---

# 7. Return Type Revision

Void Method:

```java
public void display(){

}
```

Returns:

```text
Nothing
```

---

Returning Value:

```java
public int add(){

    return 100;
}
```

---

Returning Object:

```java
public Employee getEmployee(){

    return new Employee();
}
```

---

Returning Array:

```java
public int[] getData(){

    return arr;
}
```

---

# 8. Method Overloading Revision

Definition:

```text
Same Method Name

Different Parameters
```

---

Example:

```java
add(int a,int b)

add(int a,int b,int c)

add(double a,double b)
```

---

Characteristics:

```text
Compile Time Polymorphism

Static Binding

Same Class

Flexible API Design
```

---

Method Signature:

```text
Method Name

+

Parameter List
```

---

Return Type:

```text
Not Included
```

---

# 9. Method Overriding Revision

Definition:

```text
Child class provides
its own implementation
of parent method.
```

---

Example:

```java
class Animal{

    void sound(){

    }
}
```

---

```java
class Dog extends Animal{

    void sound(){

    }
}
```

---

Characteristics:

```text
Runtime Polymorphism

Inheritance Required

Dynamic Method Dispatch

Same Signature
```

---

# Overloading vs Overriding

| Feature     | Overloading  | Overriding   |
| ----------- | ------------ | ------------ |
| Class       | Same         | Parent Child |
| Parameters  | Different    | Same         |
| Binding     | Compile Time | Runtime      |
| Inheritance | Not Required | Required     |

---

# 10. Static vs Instance Methods Revision

Static Method:

```java
Math.abs(-10);
```

---

Characteristics:

```text
Class Level

No Object Needed

Cannot Use this

One Copy
```

---

Instance Method:

```java
page.login();
```

---

Characteristics:

```text
Object Required

Can Use this

Supports OOP
```

---

Framework Rule:

```text
Utility → Static

Business Logic → Instance
```

---

# 11. Varargs Revision

Syntax:

```java
public void test(int... nums){

}
```

---

Examples:

```java
test();

test(10);

test(10,20);

test(10,20,30);
```

---

Internal Working:

```text
Compiler Converts

↓

Array
```

---

Rules:

```text
One Varargs Only

Must Be Last Parameter
```

---

# 12. Recursion Revision

Definition:

```text
Method Calling Itself
```

---

Structure:

```java
if(baseCondition){

    return;
}

method();
```

---

Requirements:

```text
Base Case

Recursive Case
```

---

Common Problems:

```text
Factorial

Fibonacci

Tree Traversal

Folder Traversal
```

---

Danger:

```text
Missing Base Case

↓

StackOverflowError
```

---

# 13. Method Chaining Revision

Example:

```java
page.enterUsername()
    .enterPassword()
    .clickLogin();
```

---

Requirement:

```text
Methods Return Objects
```

---

Benefits:

```text
Readable

Compact

Professional
```

---

# 14. Builder Pattern Revision

Traditional:

```java
new Employee(
1,
"Rahul",
30,
"Mumbai"
);
```

---

Builder:

```java
Employee.builder()
        .name("Rahul")
        .age(30)
        .build();
```

---

Benefits:

```text
Readable

Maintainable

Scalable
```

---

# 15. Framework Design Revision

Automation Framework Structure:

```text
Tests

↓

Page Objects

↓

Services

↓

Utilities

↓

Core Components
```

---

Method Categories:

```text
Page Methods

Service Methods

Utility Methods

Validation Methods

Database Methods
```

---

# 16. Selenium Project Scenarios

Common Methods:

```java
login()

logout()

searchProduct()

addToCart()

checkout()
```

---

Utility Methods:

```java
captureScreenshot()

readProperty()

generateReport()

waitForElement()
```

---

Framework Example:

```java
loginPage.login();
```

---

```java
reportUtil.generateReport();
```

---

# 17. API Framework Scenarios

Common Methods:

```java
createUser()

updateUser()

deleteUser()

getUser()
```

---

Utility Methods:

```java
readJson()

generateToken()

validateResponse()
```

---

Builder Example:

```java
User.builder()
    .name("Rahul")
    .build();
```

---

# 18. Top 50 Interview Questions

## Basic

### Q1 What is a Method?

```text
Reusable block of code.
```

---

### Q2 Why Use Methods?

```text
Reusability and Maintainability.
```

---

### Q3 Difference Between Parameter and Argument?

```text
Parameter → Method Definition

Argument → Method Call
```

---

### Q4 Can Main Method Be Overloaded?

```text
Yes
```

---

### Q5 Can Main Method Be Overridden?

```text
No

Because it is static.
```

---

### Q6 Can Constructor Be Overloaded?

```text
Yes
```

---

### Q7 Can Constructor Be Overridden?

```text
No
```

---

### Q8 Can Static Methods Be Overridden?

```text
No

Method Hiding Occurs
```

---

### Q9 What is Method Signature?

```text
Method Name + Parameter List
```

---

### Q10 Can Return Type Overload Methods?

```text
No
```

---

## Intermediate

### Q11 What is Compile Time Polymorphism?

```text
Method Overloading
```

---

### Q12 What is Runtime Polymorphism?

```text
Method Overriding
```

---

### Q13 What is Dynamic Method Dispatch?

```text
Runtime method selection.
```

---

### Q14 What is Covariant Return Type?

```text
Child method returns
more specific type.
```

---

### Q15 Why Can't Static Methods Use this?

```text
No current object exists.
```

---

### Q16 Why Is Java Pass By Value?

```text
Copies are passed.
```

---

### Q17 What Gets Copied For Objects?

```text
Reference Value.
```

---

### Q18 What Is Varargs?

```text
Variable Number Of Arguments.
```

---

### Q19 Why Use Recursion?

```text
Break complex problem
into smaller problems.
```

---

### Q20 What Causes StackOverflowError?

```text
Infinite recursion.
```

---

## Advanced

### Q21–Q50

Focus Areas:

```text
JVM Stack Frames

Method Inlining

Method Handles

Builder Pattern

Fluent APIs

Lambda Expressions

Method References

Framework Architecture

Design Patterns

Performance Optimization
```

---

# 19. One-Day Interview Preparation Notes

Revise In Order:

```text
Methods Basics

↓

Parameters

↓

Return Types

↓

Pass By Value

↓

Overloading

↓

Overriding

↓

Static vs Instance

↓

Varargs

↓

Recursion

↓

Method Chaining

↓

Builder Pattern

↓

Framework Examples
```

---

Most Important Questions:

```text
Overloading vs Overriding

Static vs Instance

Pass By Value

Stack vs Heap

Recursion

Method Signature

Runtime Polymorphism
```

---

# 20. Ultimate Methods Cheat Sheet

```text
METHOD

Reusable Code Block

METHOD SIGNATURE

Name + Parameters

OVERLOADING

Same Name

Different Parameters

Compile Time

OVERRIDING

Same Signature

Inheritance

Runtime

STATIC

Class Level

INSTANCE

Object Level

PASS BY VALUE

Always

VARARGS

int... nums

RECURSION

Method Calls Itself

STACK FRAME

Created Per Method Call

BUILDER

Method Chaining

FLUENT API

Returns Object

FRAMEWORK RULE

Utility → Static

Business Logic → Instance
```

---

# Final Interview Summary

If interviewer asks:

```text
What are the most important method concepts in Java?
```

Strong Answer:

```text
The most important method concepts are
method declaration, parameter passing,
return types, method overloading,
method overriding, runtime polymorphism,
static and instance methods, recursion,
varargs, and method chaining.

In real-world automation frameworks,
methods are used to build reusable page objects,
service layers, utility classes, reporting modules,
and API clients.

A strong understanding of methods is essential
for writing scalable, maintainable, and reusable
enterprise-level Java applications.
```

---

# End of Part 11

## Next Part

Part 12 → Methods Final Revision Notes (50+ Pages Style)

Topics:

* Ultra-Fast Revision
* Memory Diagrams
* Interview Traps
* Framework Scenarios
* Top 100 Questions
* One-Hour Revision Sheet
* Last-Minute Interview Notes
* Complete Methods Mind Map
