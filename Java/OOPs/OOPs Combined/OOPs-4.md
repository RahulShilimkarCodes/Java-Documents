# Java OOP Master Guide

# Part 4 - Inheritance Deep Dive

---

# Table of Contents

1. What is Inheritance?
2. Why Inheritance is Needed
3. Real-World Example
4. IS-A Relationship
5. extends Keyword
6. Types of Inheritance in Java
7. Single Inheritance
8. Multilevel Inheritance
9. Hierarchical Inheritance
10. Why Multiple Inheritance is Not Supported for Classes
11. Constructor Behavior in Inheritance
12. super Keyword
13. Method Inheritance
14. Variable Inheritance
15. Access Modifier Behavior
16. Method Overriding Foundation
17. Runtime Polymorphism Foundation
18. Inheritance in Selenium Frameworks
19. Inheritance in API Frameworks
20. Advantages of Inheritance
21. Disadvantages of Inheritance
22. Common Interview Traps
23. Top Interview Questions
24. Revision Notes
25. Final Cheat Sheet

---

# 1. What is Inheritance?

Inheritance is one of the most important pillars of OOP.

Definition:

```text id="inh001"
Inheritance is the mechanism through which
one class acquires properties and behaviors
of another class.
```

---

Simple Definition:

```text id="inh002"
Code Reusability Through Parent-Child Relationship
```

---

Example:

```java id="inh003"
class Animal {

    void eat(){

        System.out.println("Eating");
    }
}
```

---

```java id="inh004"
class Dog extends Animal {

}
```

---

Usage:

```java id="inh005"
Dog dog = new Dog();

dog.eat();
```

Output:

```text id="inh006"
Eating
```

---

# 2. Why Inheritance is Needed

Without Inheritance:

```java id="inh007"
class Dog {

    void eat(){

    }
}
```

---

```java id="inh008"
class Cat {

    void eat(){

    }
}
```

---

```java id="inh009"
class Lion {

    void eat(){

    }
}
```

---

Problem:

```text id="inh010"
Duplicate Code

Poor Maintainability

Difficult Updates
```

---

With Inheritance:

```java id="inh011"
class Animal {

    void eat(){

    }
}
```

---

```java id="inh012"
class Dog extends Animal {

}
```

---

```java id="inh013"
class Cat extends Animal {

}
```

---

Benefits:

```text id="inh014"
Code Reuse

Cleaner Design

Less Duplication
```

---

# 3. Real-World Example

Parent:

```text id="inh015"
Vehicle
```

---

Common Properties:

```text id="inh016"
start()

stop()

fuelType
```

---

Children:

```text id="inh017"
Car

Bike

Truck
```

---

Each child automatically gets:

```text id="inh018"
start()

stop()
```

---

This is inheritance.

---

# 4. IS-A Relationship

Inheritance Represents:

```text id="inh019"
IS-A Relationship
```

---

Examples:

```text id="inh020"
Dog IS-A Animal

Car IS-A Vehicle

Employee IS-A Person
```

---

Interview Question:

```text id="inh021"
How do you identify inheritance?
```

Answer:

```text id="inh022"
By checking whether an IS-A relationship exists.
```

---

# 5. extends Keyword

Inheritance uses:

```java id="inh023"
extends
```

---

Example:

```java id="inh024"
class Animal {

}
```

---

```java id="inh025"
class Dog extends Animal {

}
```

---

Meaning:

```text id="inh026"
Dog inherits Animal
```

---

Syntax:

```java id="inh027"
class Child extends Parent {

}
```

---

# 6. Types of Inheritance in Java

Java Supports:

```text id="inh028"
Single Inheritance

Multilevel Inheritance

Hierarchical Inheritance
```

---

Java Does Not Support:

```text id="inh029"
Multiple Inheritance Through Classes
```

---

Possible Through:

```text id="inh030"
Interfaces
```

---

# 7. Single Inheritance

One Parent.

One Child.

Example:

```java id="inh031"
class Animal {

    void eat(){

    }
}
```

---

```java id="inh032"
class Dog extends Animal {

}
```

---

Diagram:

```text id="inh033"
Animal

↓

Dog
```

---

Most Basic Type.

---

# 8. Multilevel Inheritance

Inheritance Chain.

Example:

```java id="inh034"
class Animal {

}
```

---

```java id="inh035"
class Dog extends Animal {

}
```

---

```java id="inh036"
class Puppy extends Dog {

}
```

---

Diagram:

```text id="inh037"
Animal

↓

Dog

↓

Puppy
```

---

Puppy Gets:

```text id="inh038"
Animal Features

Dog Features
```

---

# 9. Hierarchical Inheritance

One Parent.

Multiple Children.

Example:

```java id="inh039"
class Animal {

}
```

---

```java id="inh040"
class Dog extends Animal {

}
```

---

```java id="inh041"
class Cat extends Animal {

}
```

---

```java id="inh042"
class Lion extends Animal {

}
```

---

Diagram:

```text id="inh043"
          Animal
         /   |   \
       Dog  Cat  Lion
```

---

Very Common In Enterprise Projects.

---

# 10. Why Multiple Inheritance Is Not Supported

Example:

```java id="inh044"
class A {

    void display(){

    }
}
```

---

```java id="inh045"
class B {

    void display(){

    }
}
```

---

Hypothetical:

```java id="inh046"
class C extends A,B {

}
```

---

Problem:

```text id="inh047"
Which display() Should Be Called?
```

---

Known As:

```text id="inh048"
Diamond Problem
```

---

Java Solution:

```text id="inh049"
No Multiple Inheritance Through Classes
```

---

Supported Through:

```text id="inh050"
Interfaces
```

---

# 11. Constructor Behavior in Inheritance

Example:

```java id="inh051"
class Parent {

    Parent(){

        System.out.println("Parent");
    }
}
```

---

```java id="inh052"
class Child extends Parent {

    Child(){

        System.out.println("Child");
    }
}
```

---

Usage:

```java id="inh053"
new Child();
```

---

Output:

```text id="inh054"
Parent

Child
```

---

Rule:

```text id="inh055"
Parent Constructor Executes First
```

---

# 12. super Keyword

Used To Access Parent Members.

Example:

```java id="inh056"
class Animal {

    String type = "Animal";
}
```

---

```java id="inh057"
class Dog extends Animal {

    void show(){

        System.out.println(super.type);
    }
}
```

---

Output:

```text id="inh058"
Animal
```

---

super Can Access:

```text id="inh059"
Parent Variable

Parent Method

Parent Constructor
```

---

# 13. Method Inheritance

Parent Method:

```java id="inh060"
class Animal {

    void eat(){

        System.out.println("Eating");
    }
}
```

---

Child:

```java id="inh061"
class Dog extends Animal {

}
```

---

Usage:

```java id="inh062"
Dog d = new Dog();

d.eat();
```

---

Output:

```text id="inh063"
Eating
```

---

Method inherited automatically.

---

# 14. Variable Inheritance

Parent:

```java id="inh064"
class Animal {

    int age = 10;
}
```

---

Child:

```java id="inh065"
class Dog extends Animal {

}
```

---

Usage:

```java id="inh066"
Dog d = new Dog();

System.out.println(d.age);
```

---

Output:

```text id="inh067"
10
```

---

Variables can also be inherited.

---

# 15. Access Modifier Behavior

| Modifier  | Inherited?        |
| --------- | ----------------- |
| public    | Yes               |
| protected | Yes               |
| default   | Same Package Only |
| private   | No                |

---

Example:

```java id="inh068"
private int salary;
```

---

Cannot Access Directly In Child Class.

---

Interview Favorite.

---

# 16. Method Overriding Foundation

Parent:

```java id="inh069"
class Animal {

    void sound(){

        System.out.println("Animal Sound");
    }
}
```

---

Child:

```java id="inh070"
class Dog extends Animal {

    void sound(){

        System.out.println("Bark");
    }
}
```

---

Usage:

```java id="inh071"
new Dog().sound();
```

Output:

```text id="inh072"
Bark
```

---

This is:

```text id="inh073"
Method Overriding
```

---

Covered deeply in Polymorphism chapter.

---

# 17. Runtime Polymorphism Foundation

Example:

```java id="inh074"
Animal a = new Dog();
```

---

Method Call:

```java id="inh075"
a.sound();
```

---

Output:

```text id="inh076"
Bark
```

---

Reason:

```text id="inh077"
Method Resolved At Runtime
```

---

Foundation Of:

```text id="inh078"
Runtime Polymorphism
```

---

# 18. Inheritance in Selenium Frameworks

Example:

```java id="inh079"
public class BaseTest {

    WebDriver driver;

    public void launchBrowser(){

    }
}
```

---

Child:

```java id="inh080"
public class LoginTest
extends BaseTest {

}
```

---

LoginTest Gets:

```text id="inh081"
driver

launchBrowser()
```

---

Without Duplicating Code.

---

# 19. Inheritance in API Frameworks

Parent:

```java id="inh082"
public class BaseAPI {

    RequestSpecification request;
}
```

---

Child:

```java id="inh083"
public class UserAPI
extends BaseAPI {

}
```

---

Benefits:

```text id="inh084"
Shared Request Setup

Shared Utilities

Reusable Framework
```

---

# 20. Advantages of Inheritance

```text id="inh085"
Code Reusability

Maintainability

Reduced Duplication

Cleaner Design

Extensibility
```

---

Enterprise Framework Benefit:

```text id="inh086"
Centralized Common Logic
```

---

# 21. Disadvantages of Inheritance

Overuse Causes:

```text id="inh087"
Tight Coupling

Complex Hierarchies

Difficult Maintenance
```

---

Design Principle:

```text id="inh088"
Favor Composition Over Deep Inheritance
```

---

Senior-Level Interview Topic.

---

# 22. Common Interview Traps

### Trap 1

```text id="inh089"
Does Java Support Multiple Inheritance?
```

Answer:

```text id="inh090"
Not Through Classes.
```

---

### Trap 2

```text id="inh091"
Are Constructors Inherited?
```

Answer:

```text id="inh092"
No
```

---

### Trap 3

```text id="inh093"
Can Private Members Be Inherited?
```

Answer:

```text id="inh094"
No
```

---

### Trap 4

```text id="inh095"
Can Child Access Parent Constructor?
```

Answer:

```text id="inh096"
Yes Through super()
```

---

# 23. Top Interview Questions

### Q1 What Is Inheritance?

```text id="inh097"
Mechanism through which one class
acquires properties and behaviors of another.
```

---

### Q2 Why Use Inheritance?

```text id="inh098"
Code Reusability
```

---

### Q3 What Is IS-A Relationship?

```text id="inh099"
Relationship indicating inheritance.
```

---

### Q4 What Is super Keyword?

```text id="inh100"
Used to access parent members.
```

---

### Q5 Why Doesn't Java Support Multiple Inheritance?

```text id="inh101"
To avoid Diamond Problem.
```

---

### Q6 Which Inheritance Types Are Supported?

```text id="inh102"
Single

Multilevel

Hierarchical
```

---

# 24. Revision Notes

```text id="inh103"
Inheritance

↓

Code Reuse

↓

extends

↓

IS-A Relationship

Types

Single

Multilevel

Hierarchical

super()

↓

Parent Access

Foundation

↓

Method Overriding

Runtime Polymorphism
```

---

# 25. Final Cheat Sheet

```text id="inh104"
Parent Class

↓

Child Class

↓

Inherited Variables

↓

Inherited Methods

↓

super()

↓

Parent Access

Benefits

✓ Reuse

✓ Maintainability

✓ Scalability

Restrictions

✗ Multiple Inheritance (Classes)

✗ Constructor Inheritance

✗ Private Member Access
```

---

# Interview Takeaway

If interviewer asks:

```text id="inh105"
Explain Inheritance with a framework example.
```

Strong Answer:

```text id="inh106"
Inheritance allows a child class to reuse
properties and methods of a parent class.

In Selenium frameworks, common functionality
such as WebDriver initialization, reporting,
and configuration is placed in a BaseTest class.
Individual test classes inherit from BaseTest,
eliminating duplication and improving maintainability.

Inheritance represents an IS-A relationship and
forms the foundation for method overriding and
runtime polymorphism.
```

---

# End of OOP Part 4

## Next Part

```text id="inh107"
Part 5 → Polymorphism Deep Dive

Topics:

✓ Compile-Time Polymorphism

✓ Runtime Polymorphism

✓ Method Overloading

✓ Method Overriding

✓ Dynamic Method Dispatch

✓ Upcasting

✓ Downcasting

✓ Covariant Return Types

✓ Real Project Examples

✓ Selenium Framework Examples

✓ API Framework Examples

✓ Interview Questions

✓ Revision Notes
```
