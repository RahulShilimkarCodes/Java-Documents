# Java-Classes-and-Objects-Master-Guide-Part-7.md

# Java Classes and Objects Master Guide

## Part 7 – Object Cloning, equals(), hashCode(), toString() & Immutable Objects

---

# Table of Contents

1. Introduction to Object Class
2. Object Class Methods Overview
3. Object Cloning
4. Cloneable Interface
5. Shallow Copy
6. Deep Copy
7. Object Equality
8. == Operator vs equals()
9. Overriding equals()
10. hashCode() Method
11. Contract Between equals() and hashCode()
12. toString() Method
13. Immutable Objects
14. Creating Immutable Classes
15. Real-World Examples
16. Selenium Framework Usage
17. JVM Internals
18. Interview Questions
19. Revision Notes

---

# Introduction

Every class in Java directly or indirectly extends:

```java
java.lang.Object
```

Hierarchy:

```text
Object
  ↑
Employee
  ↑
Manager
  ↑
Developer
```

This means every Java object automatically inherits important methods:

```text
equals()

hashCode()

toString()

clone()

getClass()

wait()

notify()

notifyAll()
```

Understanding these methods is critical for:

* Core Java Interviews
* Collections Framework
* Selenium Framework Design
* API Automation Projects
* Product-Based Companies

---

# 1. What is Object Class?

## Definition

Object class is the root class of Java.

Package:

```java
java.lang.Object
```

Every Java class inherits from Object.

Example:

```java
class Employee {

}
```

Compiler internally treats it as:

```java
class Employee extends Object {

}
```

---

# Why is Object Class Important?

Because it provides common behavior to all Java objects.

Examples:

```text
Object Comparison

String Representation

Hashing

Synchronization

Runtime Information
```

---

# 2. Important Methods of Object Class

| Method      | Purpose               |
| ----------- | --------------------- |
| equals()    | Compare Objects       |
| hashCode()  | Generate Hash Value   |
| toString()  | String Representation |
| clone()     | Copy Object           |
| getClass()  | Runtime Class Info    |
| wait()      | Thread Communication  |
| notify()    | Wake Thread           |
| notifyAll() | Wake Multiple Threads |

---

# 3. Object Cloning

## Definition

Cloning creates an exact copy of an existing object.

Example:

```java
Employee emp1 =
new Employee();

Employee emp2 =
emp1;
```

Question:

How many objects exist?

Answer:

```text
1 Object

2 References
```

---

## Actual Copy

To create a separate object:

```java
Employee emp2 =
(Employee) emp1.clone();
```

Now:

```text
2 Objects

2 References
```

---

# Why Cloning?

Sometimes object creation is expensive.

Examples:

```text
Configuration Objects

Database Settings

Complex Framework Objects
```

Instead of creating again:

```text
Clone Existing Object
```

---

# 4. Cloneable Interface

To support cloning:

```java
class Employee
implements Cloneable {

}
```

---

# Example

```java
class Employee
implements Cloneable {

    int id = 101;

    protected Object clone()
    throws CloneNotSupportedException {

        return super.clone();

    }

}
```

Usage:

```java
Employee emp1 =
new Employee();

Employee emp2 =
(Employee) emp1.clone();
```

---

# JVM Flow

```text
Original Object

↓

clone()

↓

New Object

↓

Same Values
```

---

# 5. Shallow Copy

## Definition

Copies primitive values but shares referenced objects.

Example:

```java
class Address {

    String city;

}

class Employee
implements Cloneable {

    Address address;

}
```

---

# Memory Diagram

```text
Employee1
    |
    |
    V

Address Object

Employee2
    |
    |
    V

Same Address Object
```

---

# Problem

Changing:

```java
emp2.address.city =
"Mumbai";
```

also affects:

```java
emp1.address.city
```

because both point to same object.

---

# 6. Deep Copy

## Definition

Creates copy of object and all nested objects.

Memory:

```text
Employee1
    |
    |
    V

Address1

Employee2
    |
    |
    V

Address2
```

Independent objects.

---

# Advantage

```text
No Shared References

Safe Modifications

True Copy
```

---

# Real Project Usage

Deep copy commonly used in:

```text
Financial Applications

Banking Systems

Configuration Management

Microservices
```

---

# 7. Object Equality

Consider:

```java
Employee e1 =
new Employee();

Employee e2 =
new Employee();
```

Question:

```java
e1 == e2
```

Output:

```text
false
```

---

# Why?

Because:

```text
Different Objects

Different Addresses
```

---

# Memory

```text
e1 → Object1

e2 → Object2
```

Different references.

---

# 8. == Operator vs equals()

## == Operator

Compares:

```text
Memory Address

Reference
```

Example:

```java
String s1 =
new String("Java");

String s2 =
new String("Java");

System.out.println(
s1 == s2
);
```

Output:

```text
false
```

---

# equals()

Compares:

```text
Content

Logical Equality
```

Example:

```java
System.out.println(
s1.equals(s2)
);
```

Output:

```text
true
```

---

# Interview Table

| ==                  | equals()           |
| ------------------- | ------------------ |
| Compares References | Compares Content   |
| Faster              | Logical Comparison |
| Default Behavior    | Can Be Overridden  |

---

# 9. Overriding equals()

Example:

```java
class Employee {

    int id;

    Employee(int id){

        this.id = id;

    }

}
```

Objects:

```java
Employee e1 =
new Employee(101);

Employee e2 =
new Employee(101);
```

Default:

```java
e1.equals(e2)
```

Output:

```text
false
```

---

# Custom equals()

```java
@Override

public boolean equals(
Object obj
){

    Employee emp =
    (Employee)obj;

    return this.id ==
           emp.id;

}
```

Now:

```text
true
```

---

# Why Override equals()?

Logical comparison.

Examples:

```text
Employee ID

Account Number

User ID
```

---

# 10. hashCode() Method

## Definition

Returns integer hash value of object.

Example:

```java
Employee emp =
new Employee();

System.out.println(
emp.hashCode()
);
```

Output:

```text
Random Integer Value
```

---

# Why hashCode()?

Used by:

```text
HashMap

HashSet

Hashtable

LinkedHashMap
```

for faster lookup.

---

# HashMap Flow

```text
Key

↓

hashCode()

↓

Bucket

↓

Storage
```

---

# 11. equals() and hashCode() Contract

Important Interview Question.

Rule:

```text
Equal Objects

↓

Must Have Same hashCode()
```

---

# Wrong Implementation

Override:

```java
equals()
```

but not:

```java
hashCode()
```

May break:

```text
HashMap

HashSet
```

behavior.

---

# Correct Practice

Override both together.

Example:

```java
@Override
public int hashCode(){

    return id;
}
```

---

# 12. toString() Method

## Definition

Returns string representation of object.

Default:

```java
Employee emp =
new Employee();

System.out.println(emp);
```

Output:

```text
Employee@15db9742
```

---

# Meaning

```text
ClassName

@

Hexadecimal Hash
```

---

# Custom toString()

```java
@Override

public String toString(){

    return "Employee[id=" +
            id + "]";
}
```

Output:

```text
Employee[id=101]
```

---

# Why Override toString()?

Useful for:

```text
Debugging

Logging

Reports

Frameworks
```

---

# Selenium Example

```java
System.out.println(driver);
```

Internally:

```text
driver.toString()
```

is called.

---

# 13. Immutable Objects

## Definition

Objects whose state cannot change after creation.

Best Example:

```java
String
```

---

# Example

```java
String s =
"Java";

s.concat(" Selenium");
```

Original string remains unchanged.

---

# Characteristics

```text
Final Class

Final Fields

No Setters

State Cannot Change
```

---

# Benefits

```text
Thread Safe

Secure

Predictable

Easy To Cache
```

---

# 14. Creating Immutable Class

Example:

```java
final class Employee {

    private final int id;

    Employee(int id){

        this.id = id;

    }

    public int getId(){

        return id;

    }

}
```

---

# Why Immutable?

Useful in:

```text
Configuration Objects

DTOs

Value Objects

API Responses
```

---

# 15. Real-World Example

Bank Account:

```text
Account Number
```

should not change.

Therefore:

```text
Immutable Design
```

is preferred.

---

# 16. Selenium Framework Usage

Page Object Comparison:

```java
LoginPage page1;

LoginPage page2;
```

Frameworks often override:

```text
equals()

hashCode()

toString()
```

for logging and reporting.

---

# Test Data Objects

```java
UserData

EmployeeData

AccountData
```

often implemented as immutable classes.

---

# 17. JVM Internals

Object Creation:

```text
Heap Memory

↓

Object Created

↓

Object Header

↓

Instance Variables
```

---

# hashCode()

Generated from:

```text
Object Metadata

Memory Information

JVM Algorithm
```

---

# equals()

Executed during runtime comparison.

---

# Common Interview Questions

## Q1. Which Class Is Parent Of Every Java Class?

```java
Object
```

---

## Q2. Difference Between == and equals()?

```text
==

↓

Reference Comparison

equals()

↓

Content Comparison
```

---

## Q3. Why Override hashCode()?

Required for collections.

---

## Q4. What Happens If equals() Is Overridden But hashCode() Is Not?

Breaks HashMap and HashSet behavior.

---

## Q5. What is Cloning?

Creating copy of object.

---

## Q6. Difference Between Shallow Copy and Deep Copy?

```text
Shallow

↓

Shared References

Deep

↓

Independent References
```

---

## Q7. Why Is String Immutable?

Security and thread safety.

---

## Q8. What Is Default Output Of toString()?

```text
ClassName@HashCode
```

---

## Q9. Can Immutable Object Be Modified?

No.

---

## Q10. Which Collections Depend Heavily On hashCode()?

```text
HashMap

HashSet

Hashtable
```

---

# Revision Notes

```text
Object Class
↓
Root Class

clone()
↓
Creates Copy

Shallow Copy
↓
Shared References

Deep Copy
↓
Independent References

==
↓
Reference Comparison

equals()
↓
Content Comparison

hashCode()
↓
Hash Value

toString()
↓
String Representation

Immutable Object
↓
Cannot Change State
```

---

# Interview Summary

```text
Object
↓
Parent Of All Classes

equals()
↓
Logical Equality

hashCode()
↓
Collection Performance

toString()
↓
Debugging

clone()
↓
Copy Object

Immutable Class
↓
Thread Safe

Deep Copy
↓
Independent Objects
```

---

# End of Part 7

## Next Part

Java-Classes-and-Objects-Master-Guide-Part-8.md

Topics:

* Association
* Aggregation
* Composition
* HAS-A Relationship
* IS-A vs HAS-A
* Object Relationships in OOP
* Real Framework Design
* Selenium Framework Architecture
* Dependency Injection Basics
* Spring Framework Connection
* Interview Questions
