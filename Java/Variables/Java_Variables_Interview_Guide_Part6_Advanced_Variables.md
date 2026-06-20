# Java Variables Interview Master Guide
# Part 6 - Advanced Variable Concepts & Scope Resolution

## Table of Contents

1. Variable Shadowing
2. Variable Hiding
3. this Keyword Deep Dive
4. super Keyword Deep Dive
5. Scope Resolution Rules
6. Static vs Instance Access
7. Nested Classes & Variable Access
8. Lambda Expressions & Effectively Final Variables
9. Anonymous Classes
10. Selenium Framework Scenarios
11. Common Coding Mistakes
12. Advanced Interview Questions
13. MCQs
14. Revision Notes

---

# 1. Variable Shadowing

Variable Shadowing occurs when a local variable or method parameter has the same name as an instance variable.

Example:

```java
class Employee {

    String name;

    Employee(String name) {
        name = name;
    }
}
```

Problem:

Parameter shadows instance variable.

Both name variables refer to parameter.

---

## Correct Solution

```java
class Employee {

    String name;

    Employee(String name) {

        this.name = name;
    }
}
```

---

## Interview Question

Why use this keyword?

Answer:

To differentiate instance variables from local variables or parameters.

---

# Memory Representation

```text
Object

name = null
```

Constructor

```text
name = Rahul
```

Without this:

Object value never updated.

---

# 2. Variable Hiding

Occurs when child class declares variable with same name as parent class.

Example:

```java
class Parent {

    int x = 10;
}

class Child extends Parent {

    int x = 20;
}
```

---

## Access

```java
Child c = new Child();

System.out.println(c.x);
```

Output:

```text
20
```

Parent variable hidden.

---

## Access Parent Variable

```java
super.x
```

---

# Interview Question

Difference between Shadowing and Hiding?

Shadowing:

Local variable hides instance variable.

Hiding:

Child variable hides parent variable.

---

# 3. this Keyword Deep Dive

Represents current object.

---

## Access Current Object Variable

```java
this.name
```

---

## Constructor Chaining

```java
public Employee() {

    this("Rahul");
}
```

Calls another constructor.

---

## Passing Current Object

```java
method(this);
```

Current object reference passed.

---

## Returning Current Object

```java
return this;
```

Useful for Method Chaining.

---

Example

```java
builder.setName("Rahul")
       .setAge(25)
       .build();
```

---

# 4. super Keyword Deep Dive

Represents parent class object.

---

## Access Parent Variable

```java
super.name
```

---

## Access Parent Method

```java
super.display();
```

---

## Parent Constructor Call

```java
super();
```

Automatically executed if omitted.

---

Example

```java
class Parent {

    Parent() {

        System.out.println("Parent");
    }
}
```

---

# Constructor Flow

```java
Child()
    ↓
super()
    ↓
Parent()
```

---

# 5. Scope Resolution Rules

Java searches variables in order.

Rule:

1. Local Variable
2. Method Parameter
3. Instance Variable
4. Parent Variable
5. Static Variable

---

Example

```java
int x = 100;

public void test() {

    int x = 10;

    System.out.println(x);
}
```

Output:

10

Local variable wins.

---

# Scope Hierarchy Diagram

```text
Local
  ↓
Method Parameter
  ↓
Instance
  ↓
Parent
  ↓
Static
```

---

# 6. Static vs Instance Access

## Static Method

```java
public static void display() {

}
```

Cannot directly access instance variables.

---

Example

```java
int age = 10;

static void test() {

    System.out.println(age);
}
```

Compilation Error

---

Reason

Static context has no object.

---

## Solution

```java
Employee e = new Employee();

System.out.println(e.age);
```

---

# Instance Method

Can access:

- Static variables
- Instance variables
- Local variables

---

# Interview Question

Why static method cannot access non-static variable?

Answer:

Because non-static variable belongs to object while static method belongs to class.

---

# 7. Nested Classes & Variable Access

## Inner Class

```java
class Outer {

    int x = 10;

    class Inner {

        void display() {

            System.out.println(x);
        }
    }
}
```

Inner class can access outer class members.

---

# Variable Resolution

Order:

1. Local
2. Inner
3. Outer

---

# Static Nested Class

```java
static class Inner {

}
```

Can only access static members directly.

---

# 8. Lambda Expressions

Important Java 8 Interview Topic

Example

```java
int x = 10;

Runnable r = () -> {

    System.out.println(x);
};
```

Works.

---

## Modification

```java
x = 20;
```

Compilation Error

---

# Effectively Final

Variable must not change after initialization.

---

Valid

```java
int x = 10;
```

Invalid

```java
int x = 10;

x = 20;
```

Used inside lambda.

---

# Why Restriction Exists?

To avoid concurrency issues.

To preserve consistency.

---

# 9. Anonymous Classes

Example

```java
Runnable r = new Runnable() {

    public void run() {

        System.out.println("Hello");
    }
};
```

---

Anonymous classes also require effectively final variables.

---

Example

```java
int age = 10;
```

Allowed.

Changing age later causes compilation error.

---

# 10. Selenium Framework Scenarios

## Scenario 1

```java
public LoginPage(WebDriver driver) {

    this.driver = driver;
}
```

Question:

Why this.driver?

Answer:

Avoid variable shadowing.

---

## Scenario 2

```java
private static WebDriver driver;
```

Shared across objects.

Can cause parallel execution issues.

---

## Scenario 3

```java
ThreadLocal<WebDriver> driver;
```

Thread specific storage.

Preferred for parallel execution.

---

# Page Object Example

```java
class LoginPage {

    private WebDriver driver;

    LoginPage(WebDriver driver) {

        this.driver = driver;
    }
}
```

Most common interview discussion.

---

# 11. Common Coding Mistakes

Mistake 1

```java
name = name;
```

Should be

```java
this.name = name;
```

---

Mistake 2

Using static where instance variable required.

---

Mistake 3

Trying to access instance variable inside static method.

---

Mistake 4

Confusing variable hiding with method overriding.

---

Mistake 5

Modifying variable used in lambda.

---

# Advanced Interview Questions

### Q1. What is Variable Shadowing?

Local variable hides instance variable.

---

### Q2. What is Variable Hiding?

Child variable hides parent variable.

---

### Q3. Difference between this and super?

this → Current Object

super → Parent Object

---

### Q4. Can static method use this keyword?

No.

No object exists.

---

### Q5. Why use constructor chaining?

Code reuse.

---

### Q6. What is Effectively Final Variable?

Variable not modified after initialization.

---

### Q7. Why lambdas require effectively final variables?

Thread safety and consistency.

---

### Q8. Can inner class access outer variables?

Yes.

---

### Q9. Why this.driver = driver is common?

Avoids variable shadowing.

---

### Q10. Can variable hiding be overridden?

No.

Variables are hidden, not overridden.

---

# MCQs

Q1. Which keyword refers current object?

A. super
B. this

Answer: B

---

Q2. Which keyword refers parent object?

A. super
B. this

Answer: A

---

Q3. Variable shadowing occurs between?

A. Parent and Child
B. Local and Instance

Answer: B

---

Q4. Variable hiding occurs between?

A. Parent and Child
B. Local and Instance

Answer: A

---

Q5. Lambda variables must be?

A. Mutable
B. Effectively Final

Answer: B

---

# Quick Revision Notes

SHADOWING

- Local hides instance variable

HIDING

- Child hides parent variable

THIS

- Current object

SUPER

- Parent object

STATIC METHOD

- Cannot access instance members directly

INSTANCE METHOD

- Can access everything

LAMBDA

- Requires effectively final variables

INNER CLASS

- Can access outer members

THREADLOCAL

- Thread-specific variable storage

---

# One Minute Interview Cheat Sheet

this.name = name

→ Fixes Shadowing

super.x

→ Access Parent Variable

Shadowing

→ Local vs Instance

Hiding

→ Child vs Parent

Static Method

→ No direct instance access

Lambda

→ Effectively Final Variables

Page Object Model

→ this.driver = driver

Most Asked Selenium Interview Line:

```java
public LoginPage(WebDriver driver) {

    this.driver = driver;
}
```

Reason:

Avoids variable shadowing and stores driver reference in object.
