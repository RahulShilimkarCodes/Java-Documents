# Java OOP Master Guide

# Part 8 - Association, Aggregation & Composition Deep Dive

---

# Table of Contents

1. What is Association?
2. Why Relationships Matter in OOP
3. HAS-A Relationship
4. Types of Association
5. One-to-One Association
6. One-to-Many Association
7. Many-to-Many Association
8. Aggregation
9. Composition
10. Aggregation vs Composition
11. Strong vs Weak Relationships
12. Dependency Relationship
13. Dependency Injection Foundation
14. UML Representation
15. Association in Selenium Frameworks
16. Composition in Selenium Page Object Model
17. Relationships in API Frameworks
18. Real Project Examples
19. Advantages of Composition
20. Composition Over Inheritance Principle
21. Common Interview Traps
22. Top Interview Questions
23. Revision Notes
24. Final Cheat Sheet

---

# 1. What is Association?

Definition:

```text id="rel001"
Association is a relationship between
two independent classes.
```

---

Simple Definition:

```text id="rel002"
One Object Uses Another Object
```

---

Example:

```text id="rel003"
Teacher ↔ Student
```

---

Both Exist Independently.

---

Teacher Can Exist Without Student.

Student Can Exist Without Teacher.

---

This is Association.

---

# 2. Why Relationships Matter in OOP

Real Applications Consist Of:

```text id="rel004"
Multiple Classes
```

---

Examples:

```text id="rel005"
User

Order

Product

Payment

Notification
```

---

These Objects Must Communicate.

---

Relationships Help:

```text id="rel006"
Model Real World Systems
```

---

# 3. HAS-A Relationship

Inheritance Represents:

```text id="rel007"
IS-A Relationship
```

---

Association Represents:

```text id="rel008"
HAS-A Relationship
```

---

Example:

```text id="rel009"
Car HAS-A Engine
```

---

```text id="rel010"
Company HAS-A Employee
```

---

```text id="rel011"
Order HAS-A Product
```

---

Interview Favorite.

---

# 4. Types of Association

Main Types:

```text id="rel012"
Association

Aggregation

Composition
```

---

Think As:

```text id="rel013"
Association

↓

General Relationship

Aggregation

↓

Weak HAS-A

Composition

↓

Strong HAS-A
```

---

# 5. One-to-One Association

Example:

```text id="rel014"
Person ↔ Passport
```

---

Code:

```java id="rel015"
class Passport {

}
```

---

```java id="rel016"
class Person {

    Passport passport;
}
```

---

Diagram:

```text id="rel017"
Person

↓

Passport
```

---

# 6. One-to-Many Association

Example:

```text id="rel018"
Department

↓

Employees
```

---

Code:

```java id="rel019"
class Employee {

}
```

---

```java id="rel020"
class Department {

    List<Employee> employees;
}
```

---

One Department.

Many Employees.

---

# 7. Many-to-Many Association

Example:

```text id="rel021"
Students

↓

Courses
```

---

One Student:

```text id="rel022"
Can Join Multiple Courses
```

---

One Course:

```text id="rel023"
Can Have Multiple Students
```

---

Common In Database Design.

---

# 8. Aggregation

Definition:

```text id="rel024"
A weak HAS-A relationship where
child object can exist independently.
```

---

Example:

```text id="rel025"
Department HAS-A Employee
```

---

If Department Removed:

```text id="rel026"
Employee Still Exists
```

---

Example:

```java id="rel027"
class Employee {

}
```

---

```java id="rel028"
class Department {

    Employee employee;
}
```

---

Weak Relationship.

---

# 9. Composition

Definition:

```text id="rel029"
A strong HAS-A relationship where
child object cannot exist independently.
```

---

Example:

```text id="rel030"
House HAS-A Room
```

---

Destroy House:

```text id="rel031"
Rooms Also Gone
```

---

Example:

```java id="rel032"
class Engine {

}
```

---

```java id="rel033"
class Car {

    private Engine engine =
        new Engine();
}
```

---

Strong Relationship.

---

# 10. Aggregation vs Composition

| Aggregation           | Composition              |
| --------------------- | ------------------------ |
| Weak Relationship     | Strong Relationship      |
| Independent Lifecycle | Dependent Lifecycle      |
| Child Can Exist Alone | Child Cannot Exist Alone |
| HAS-A                 | Strong HAS-A             |
| Less Ownership        | Full Ownership           |

---

Interview Favorite Question.

---

# 11. Strong vs Weak Relationships

Weak:

```text id="rel034"
University

↓

Professor
```

---

Professor Can Exist Elsewhere.

---

Strong:

```text id="rel035"
Human

↓

Heart
```

---

Heart Cannot Exist As Part Of Human Model.

---

Memory Perspective:

```text id="rel036"
Strong Ownership
```

---

# 12. Dependency Relationship

Definition:

```text id="rel037"
One object temporarily uses another object.
```

---

Example:

```java id="rel038"
class ReportGenerator {

    void generate(
       DatabaseConnection db){

    }
}
```

---

Relationship Exists Only During Method Call.

---

Called:

```text id="rel039"
Dependency
```

---

Weakest Relationship.

---

# 13. Dependency Injection Foundation

Very Important For Framework Interviews.

Without DI:

```java id="rel040"
class UserService {

    Database db =
      new Database();
}
```

---

Problem:

```text id="rel041"
Tightly Coupled
```

---

With DI:

```java id="rel042"
class UserService {

    Database db;

    UserService(Database db){

        this.db = db;
    }
}
```

---

Benefits:

```text id="rel043"
Loose Coupling

Testability

Flexibility
```

---

Used By:

```text id="rel044"
Spring Framework
```

---

# 14. UML Representation

Association:

```text id="rel045"
Class A -------- Class B
```

---

Aggregation:

```text id="rel046"
Class A ◇-------- Class B
```

---

Composition:

```text id="rel047"
Class A ◆-------- Class B
```

---

Interview Bonus Point.

---

# 15. Association in Selenium Frameworks

Example:

```java id="rel048"
class LoginPage {

}
```

---

```java id="rel049"
class HomePage {

}
```

---

Test Class:

```java id="rel050"
LoginPage login;

HomePage home;
```

---

Pages Associated Together.

---

# 16. Composition in Selenium POM

Real Framework Example.

Page Class:

```java id="rel051"
class LoginPage {

    private WebDriver driver;
}
```

---

Driver Is Owned By Page Object.

---

Composition Example:

```text id="rel052"
LoginPage HAS-A WebDriver
```

---

Another Example:

```java id="rel053"
class BasePage {

    protected WebDriver driver;
}
```

---

Every Page Depends On Driver.

---

# 17. Relationships in API Frameworks

Example:

```java id="rel054"
class UserAPI {

    RequestSpecification request;
}
```

---

Relationship:

```text id="rel055"
UserAPI HAS-A RequestSpecification
```

---

Composition Often Used.

---

Another Example:

```java id="rel056"
class OrderService {

    PaymentService payment;
}
```

---

Association.

---

# 18. Real Project Examples

E-Commerce System:

```text id="rel057"
User

↓

Orders

↓

Products

↓

Payments
```

---

Relationships:

```text id="rel058"
User HAS-A Orders

Order HAS-A Products

Order HAS-A Payment
```

---

Automation Framework:

```text id="rel059"
BaseTest

↓

Page Objects

↓

Utilities

↓

Reports
```

---

All Connected Through Associations.

---

# 19. Advantages of Composition

```text id="rel060"
Flexible Design

Loose Coupling

Easy Testing

Better Reusability

Maintainability
```

---

Modern Design Principle:

```text id="rel061"
Prefer Composition
Over Inheritance
```

---

Senior-Level Interview Topic.

---

# 20. Composition Over Inheritance Principle

Old Design:

```java id="rel062"
class Car
extends Engine {
}
```

---

Bad Design.

---

Better:

```java id="rel063"
class Car {

    Engine engine;
}
```

---

Reason:

```text id="rel064"
Car HAS-A Engine

Not IS-A Engine
```

---

This Principle Appears In:

```text id="rel065"
Spring

Hibernate

Selenium Frameworks

Microservices
```

---

# 21. Common Interview Traps

### Trap 1

```text id="rel066"
Difference Between Aggregation And Composition?
```

Answer:

```text id="rel067"
Aggregation = Weak Ownership

Composition = Strong Ownership
```

---

### Trap 2

```text id="rel068"
What Relationship Is Represented By Inheritance?
```

Answer:

```text id="rel069"
IS-A
```

---

### Trap 3

```text id="rel070"
What Relationship Is Represented By Composition?
```

Answer:

```text id="rel071"
HAS-A
```

---

### Trap 4

```text id="rel072"
Which Is Better:
Inheritance Or Composition?
```

Answer:

```text id="rel073"
Usually Composition
```

---

# 22. Top Interview Questions

### Q1 What Is Association?

```text id="rel074"
Relationship between independent objects.
```

---

### Q2 What Is Aggregation?

```text id="rel075"
Weak HAS-A relationship.
```

---

### Q3 What Is Composition?

```text id="rel076"
Strong HAS-A relationship.
```

---

### Q4 Difference Between Aggregation And Composition?

```text id="rel077"
Ownership and lifecycle dependency.
```

---

### Q5 What Is Dependency?

```text id="rel078"
Temporary object usage relationship.
```

---

### Q6 Why Prefer Composition Over Inheritance?

```text id="rel079"
More flexible and loosely coupled design.
```

---

# 23. Revision Notes

```text id="rel080"
Relationships

↓

Association

↓

General Relationship

Aggregation

↓

Weak HAS-A

Composition

↓

Strong HAS-A

Dependency

↓

Temporary Usage

Modern Design

↓

Composition
Over
Inheritance
```

---

# 24. Final Cheat Sheet

```text id="rel081"
Inheritance

↓

IS-A

Composition

↓

HAS-A

Aggregation

↓

Weak Ownership

Composition

↓

Strong Ownership

Dependency Injection

↓

Loose Coupling

Framework Design

↓

Composition Preferred
```

---

# Interview Takeaway

If interviewer asks:

```text id="rel082"
Why is Composition preferred over Inheritance in modern frameworks?
```

Strong Answer:

```text id="rel083"
Composition creates a HAS-A relationship
instead of an IS-A relationship.

It provides better flexibility, loose coupling,
and easier testing. Modern frameworks such as
Spring, Selenium, Hibernate, and microservices
heavily rely on composition and dependency
injection rather than deep inheritance hierarchies.

For example, a Page Object HAS-A WebDriver,
which is composition, whereas making a Page
extend WebDriver would be incorrect.
```

---

# End of OOP Part 8

## Next Part

```text id="rel084"
Part 9 → Object Class, equals(), hashCode(), toString()

Topics:

✓ Object Class

✓ equals()

✓ hashCode()

✓ toString()

✓ == vs equals()

✓ Cloneable

✓ Object Cloning

✓ Deep Copy

✓ Shallow Copy

✓ Collection Framework Impact

✓ HashMap Internals

✓ Selenium Examples

✓ Interview Questions

✓ Revision Notes
```
