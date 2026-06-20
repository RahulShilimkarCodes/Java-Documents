# Java Variables Interview Master Guide
## Part 1 – Fundamentals

# Table of Contents

1. What is a Variable?
2. Why Variables are Needed?
3. Variable Declaration
4. Variable Initialization
5. Variable Naming Rules
6. Variable Scope
7. Variable Lifecycle
8. Types of Variables
9. Interview Questions
10. Revision Notes

---

# 1. What is a Variable?

A variable is a named memory location used to store data during program execution.

Example:

```java
int age = 25;
```

- Variable Name = age
- Data Type = int
- Value = 25

---

# Why Variables are Required?

Benefits:

- Reusability
- Maintainability
- Readability
- Dynamic behavior

Example:

```java
int salary = 50000;

System.out.println(salary);
System.out.println(salary + 10000);
```

---

# Variable Declaration

```java
int age;
String name;
double salary;
```

Declaration reserves memory.

---

# Variable Initialization

```java
int age = 25;
String city = "Mumbai";
```

Initialization assigns a value to a variable.

---

# Declaration vs Initialization

Declaration:

```java
int age;
```

Initialization:

```java
age = 25;
```

Combined:

```java
int age = 25;
```

---

# Variable Naming Rules

Valid:

```java
studentName
employeeSalary
totalMarks
```

Rules:

- Must begin with letter, _ or $
- Cannot start with number
- Cannot use Java keywords
- Java is case-sensitive

---

# Variable Scope

Scope is the area where a variable is accessible.

```java
public void display() {
    int age = 25;
    System.out.println(age);
}
```

---

# Variable Lifetime

Created when execution enters scope.

Destroyed when execution exits scope.

---

# Types of Variables

1. Local Variable
2. Instance Variable
3. Static Variable

---

# Quick Revision Notes

- Variable stores data.
- Declaration creates variable.
- Initialization assigns value.
- Scope determines accessibility.
- Lifetime determines existence.
- Java supports Local, Instance and Static variables.

---

# Interview Questions

1. What is a variable?
2. Difference between declaration and initialization?
3. What are naming rules for variables?
4. What is scope?
5. What are types of variables in Java?
6. Why are variables important?
