# Java-Classes-and-Objects-Master-Guide-Part-3.md

# Java Classes and Objects Master Guide

## Part 3 – Constructors, Object Initialization & Constructor Chaining

---

# Table of Contents

1. Introduction to Constructors
2. Why Constructors Are Needed
3. Constructor vs Method
4. Default Constructor
5. No-Argument Constructor
6. Parameterized Constructor
7. Constructor Overloading
8. Constructor Chaining
9. this() Keyword
10. Object Initialization Using Constructors
11. JVM Constructor Execution Flow
12. Constructor Memory Flow
13. Real-World Examples
14. Selenium Framework Examples
15. Interview Questions
16. Revision Notes

---

# Introduction

In previous parts we learned:

```text
Class
↓
Blueprint

Object
↓
Real Instance

new
↓
Creates Object
```

But object creation is not complete until initialization happens.

Example:

```java
Employee emp =
new Employee();
```

Question:

```text
Who Initializes The Object?

Who Assigns Default Values?

Who Sets Initial Data?
```

Answer:

```text
Constructor
```

Constructors are one of the most frequently asked Java interview topics because they are directly related to:

* Object Creation
* Memory Allocation
* JVM Internals
* Framework Design
* Dependency Injection
* Spring Framework

---

# 1. What is a Constructor?

## Definition

A Constructor is a special member of a class that executes automatically when an object is created.

Example:

```java
class Employee {

    Employee() {

        System.out.println(
        "Constructor Called"
        );

    }

}
```

Object Creation:

```java
Employee emp =
new Employee();
```

Output:

```text
Constructor Called
```

---

## Important Characteristics

### Same Name As Class

```java
class Employee {

    Employee() {

    }

}
```

Valid.

---

### No Return Type

Wrong:

```java
void Employee() {

}
```

This becomes a method.

---

### Called Automatically

No need to call explicitly.

---

# 2. Why Constructors Are Needed?

Imagine:

```java
Employee emp =
new Employee();
```

Without constructor:

```text
Object Created

But Not Initialized
```

Constructor helps initialize object state.

Example:

```java
Employee() {

    name = "Rahul";

    id = 101;

}
```

Now every object starts with valid values.

---

## Real World Example

Bank Account

Without Constructor:

```text
Account Created

Balance Unknown
```

With Constructor:

```text
Account Created

Balance Initialized
```

---

# 3. Constructor vs Method

| Constructor             | Method              |
| ----------------------- | ------------------- |
| Same Name As Class      | Any Name            |
| No Return Type          | Has Return Type     |
| Executes Automatically  | Called Explicitly   |
| Used For Initialization | Used For Behavior   |
| Runs Once Per Object    | Runs Multiple Times |

---

## Example

Constructor:

```java
Employee() {

}
```

Method:

```java
void work() {

}
```

---

# Interview Question

Can Constructor Return Value?

Answer:

```text
No
```

Constructors never have a return type.

---

# 4. Default Constructor

## Definition

A constructor automatically provided by JVM when no constructor is written.

Example:

```java
class Employee {

    String name;

}
```

Compiler internally creates:

```java
Employee() {

}
```

---

## Object Creation

```java
Employee emp =
new Employee();
```

Works successfully.

---

## Important Rule

Default constructor exists only if developer does not create any constructor.

---

# Example

```java
class Employee {

    Employee(String name){

    }

}
```

Now:

```java
Employee emp =
new Employee();
```

Compiler Error.

Because JVM no longer creates default constructor.

---

# 5. No-Argument Constructor

Developer-created constructor with no parameters.

Example:

```java
class Employee {

    Employee(){

        System.out.println(
        "Object Created"
        );

    }

}
```

---

## Difference

Default Constructor:

```text
Created By JVM
```

No-Arg Constructor:

```text
Created By Developer
```

---

# 6. Parameterized Constructor

## Definition

Constructor that accepts parameters.

Example:

```java
class Employee {

    String name;
    int id;

    Employee(
    String name,
    int id
    ){

        this.name = name;
        this.id = id;

    }

}
```

Object:

```java
Employee emp =
new Employee(
"Rahul",
101
);
```

---

## Benefits

```text
Flexible Initialization

Cleaner Code

Better Design
```

---

## Output

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

# 7. Constructor Overloading

## Definition

Having multiple constructors with different parameter lists.

Example:

```java
class Employee {

    Employee(){

    }

    Employee(String name){

    }

    Employee(
    String name,
    int id
    ){

    }

}
```

---

## Why Use It?

Provide multiple ways to create objects.

Example:

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee(
"Rahul"
);

Employee e3 =
new Employee(
"Rahul",
101
);
```

---

# Real World Example

User Registration

```text
User()

User(name)

User(name,email)

User(name,email,mobile)
```

Different initialization options.

---

# 8. Constructor Chaining

## Definition

Calling one constructor from another constructor.

Example:

```java
class Employee {

    Employee(){

        this("Rahul");

    }

    Employee(String name){

        System.out.println(
        name
        );

    }

}
```

---

## Output

```text
Rahul
```

---

## Benefits

```text
Code Reuse

Cleaner Constructors

Avoid Duplication
```

---

# 9. this() Keyword

Used to invoke another constructor of same class.

Example:

```java
class Employee {

    Employee(){

        this(
        "Rahul",
        101
        );

    }

    Employee(
    String name,
    int id
    ){

        System.out.println(
        name
        );

    }

}
```

---

## Important Rule

Must be first statement.

Valid:

```java
this("Rahul");
```

Invalid:

```java
System.out.println();

this("Rahul");
```

Compiler Error.

---

# Constructor Chaining Flow

```text
Employee()

↓

Employee(String)

↓

Employee(String,int)
```

---

# 10. Object Initialization Using Constructors

Without Constructor:

```java
Employee emp =
new Employee();

emp.name =
"Rahul";

emp.id =
101;
```

---

With Constructor:

```java
Employee emp =
new Employee(
"Rahul",
101
);
```

---

## Advantage

```text
Less Code

Cleaner Objects

Immutable Design Possible
```

---

# 11. JVM Constructor Execution Flow

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

Default Values Assigned

```text
int → 0

boolean → false

String → null
```

---

## Step 4

Constructor Invoked

```text
Employee()
```

---

## Step 5

Object Initialized

---

## Step 6

Reference Returned

---

# Complete Flow

```text
new Employee()

↓

Class Loading

↓

Heap Allocation

↓

Default Initialization

↓

Constructor Execution

↓

Reference Returned

↓

Stored In Variable
```

---

# 12. Constructor Memory Diagram

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

After Constructor:

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

name = Rahul

id = 101
```

---

# 13. Real World Example

Bank Account

```java
class Account {

    String accountHolder;
    double balance;

    Account(
    String holder,
    double balance
    ){

        this.accountHolder =
        holder;

        this.balance =
        balance;

    }

}
```

Object:

```java
Account acc =
new Account(
"Rahul",
5000
);
```

---

# 14. Selenium Framework Example

Page Object Creation

Example:

```java
public class LoginPage {

    WebDriver driver;

    LoginPage(
    WebDriver driver
    ){

        this.driver =
        driver;

    }

}
```

Usage:

```java
LoginPage page =
new LoginPage(driver);
```

---

## Why Constructor?

Inject dependency.

```text
WebDriver

↓

Passed To Page Object

↓

Available Everywhere
```

This concept is heavily used in:

* Selenium Frameworks
* Spring Framework
* Dependency Injection

---

# Common Interview Questions

## Q1. What is a Constructor?

Special member used to initialize objects.

---

## Q2. Can Constructor Be Private?

Yes.

Example:

```java
private Employee(){

}
```

Used in Singleton Pattern.

---

## Q3. Can Constructor Be Static?

No.

Compiler Error.

---

## Q4. Can Constructor Be Final?

No.

Constructors are never inherited.

---

## Q5. Can We Overload Constructors?

Yes.

Frequently done in real projects.

---

## Q6. Can We Override Constructors?

No.

Constructors are not inherited.

---

## Q7. What Happens If No Constructor Exists?

JVM provides default constructor.

---

## Q8. Which Executes First?

```text
Object Creation

↓

Default Initialization

↓

Constructor Execution
```

---

## Q9. What Is Constructor Chaining?

Calling one constructor from another constructor.

Using:

```java
this()
```

---

## Q10. Why Is Constructor Important In Selenium?

Used for:

```text
WebDriver Injection

Page Object Initialization

Dependency Management
```

---

# Revision Notes

```text
Constructor
↓
Initializes Object

Default Constructor
↓
Created By JVM

No-Arg Constructor
↓
Created By Developer

Parameterized Constructor
↓
Accepts Parameters

Constructor Overloading
↓
Multiple Constructors

Constructor Chaining
↓
One Constructor Calls Another

this()
↓
Calls Constructor

Object Creation
↓
Triggers Constructor
```

---

# Interview Summary

```text
new Keyword
↓
Allocates Memory

Constructor
↓
Initializes Object

Default Constructor
↓
JVM Generated

Parameterized Constructor
↓
Custom Initialization

this()
↓
Constructor Chaining

Constructor Overloading
↓
Multiple Creation Options
```

---

# End of Part 3

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-4.md

Topics:

* this Keyword Complete Guide
* this vs super
* Instance Variables vs Local Variables
* Current Object Reference
* Method Chaining
* Passing Objects as Parameters
* Returning Objects from Methods
* Object Relationships
* Memory Diagrams
* Interview Questions
