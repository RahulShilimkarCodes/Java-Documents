# Java OOP Master Guide

# Part 3 - Encapsulation Deep Dive

---

# Table of Contents

1. What is Encapsulation?
2. Why Encapsulation is Needed
3. Data Hiding vs Encapsulation
4. Private Variables
5. Getters and Setters
6. Validation Through Encapsulation
7. Read-Only Classes
8. Write-Only Classes
9. Immutable Classes
10. POJO Classes
11. JavaBeans
12. DTO (Data Transfer Objects)
13. Builder Pattern
14. Encapsulation in Selenium Frameworks
15. Encapsulation in API Frameworks
16. Advantages of Encapsulation
17. Disadvantages of Encapsulation
18. Common Interview Traps
19. Top Interview Questions
20. Revision Notes
21. Final Cheat Sheet

---

# 1. What is Encapsulation?

Encapsulation is one of the four pillars of OOP.

Definition:

```text id="enc001"
Encapsulation is the process of binding
data and methods together into a single unit
while restricting direct access to data.
```

---

Simple Definition:

```text id="enc002"
Data Hiding + Controlled Access
```

---

Example:

```java id="enc003"
class Employee {

    private String name;

    public void setName(String name){

        this.name = name;
    }

    public String getName(){

        return name;
    }
}
```

---

Interview Definition:

```text id="enc004"
Encapsulation protects object data
by restricting direct access and exposing
controlled methods.
```

---

# 2. Why Encapsulation is Needed

Without Encapsulation:

```java id="enc005"
class Employee {

    public int age;
}
```

---

Usage:

```java id="enc006"
emp.age = -100;
```

---

Problem:

```text id="enc007"
Invalid Data Allowed
```

---

With Encapsulation:

```java id="enc008"
private int age;
```

---

Setter Validation:

```java id="enc009"
public void setAge(int age){

    if(age > 0){

        this.age = age;
    }
}
```

---

Benefits:

```text id="enc010"
Data Protection

Validation

Security

Maintainability
```

---

# 3. Data Hiding vs Encapsulation

Many candidates confuse these terms.

---

Data Hiding:

```text id="enc011"
Restrict Direct Access To Data
```

Example:

```java id="enc012"
private String password;
```

---

Encapsulation:

```text id="enc013"
Data + Methods Wrapped Together
```

Example:

```java id="enc014"
private String password;

public String getPassword(){

    return password;
}
```

---

Interview Answer:

```text id="enc015"
Data hiding is achieved using access modifiers,
while encapsulation is the broader concept of
combining data and methods into one unit.
```

---

# 4. Private Variables

Encapsulation starts with:

```java id="enc016"
private
```

---

Example:

```java id="enc017"
class Employee {

    private String name;

    private int age;
}
```

---

Why Private?

```text id="enc018"
Prevent Direct Modification

Force Controlled Access
```

---

Invalid:

```java id="enc019"
emp.name = "Rahul";
```

---

Compilation Error.

---

# 5. Getters and Setters

Getter:

```java id="enc020"
public String getName(){

    return name;
}
```

---

Setter:

```java id="enc021"
public void setName(String name){

    this.name = name;
}
```

---

Usage:

```java id="enc022"
emp.setName("Rahul");

System.out.println(
    emp.getName()
);
```

---

Naming Convention:

```text id="enc023"
getVariable()

setVariable()
```

---

Examples:

```java id="enc024"
getSalary()

setSalary()

getEmail()

setEmail()
```

---

# 6. Validation Through Encapsulation

Real Advantage.

Example:

```java id="enc025"
private int age;
```

---

Setter:

```java id="enc026"
public void setAge(int age){

    if(age >= 18){

        this.age = age;
    }
}
```

---

Invalid Data:

```java id="enc027"
emp.setAge(10);
```

Rejected.

---

Interview Point:

```text id="enc028"
Encapsulation allows validation before data assignment.
```

---

# 7. Read-Only Classes

Getter Available.

Setter Missing.

Example:

```java id="enc029"
class Employee {

    private String company =
        "Google";

    public String getCompany(){

        return company;
    }
}
```

---

Usage:

```java id="enc030"
emp.getCompany();
```

---

Cannot Modify:

```java id="enc031"
emp.setCompany();
```

Not Available.

---

Called:

```text id="enc032"
Read Only Class
```

---

# 8. Write-Only Classes

Setter Available.

Getter Missing.

Example:

```java id="enc033"
class Password {

    private String password;

    public void setPassword(
        String password){

        this.password = password;
    }
}
```

---

Common Usage:

```text id="enc034"
Security Sensitive Data
```

---

# 9. Immutable Classes

Very Important Interview Topic.

Definition:

```text id="enc035"
An immutable object cannot be modified
after creation.
```

---

Example:

```java id="enc036"
final class Employee {

    private final String name;

    public Employee(String name){

        this.name = name;
    }

    public String getName(){

        return name;
    }
}
```

---

Characteristics:

```text id="enc037"
final class

private final variables

No setters
```

---

Benefits:

```text id="enc038"
Thread Safety

Security

Predictability
```

---

Interview Question:

```text id="enc039"
Is String immutable?
```

Answer:

```text id="enc040"
Yes
```

---

# 10. POJO Classes

POJO:

```text id="enc041"
Plain Old Java Object
```

---

Simple Example:

```java id="enc042"
class Employee {

    private String name;

    public String getName(){

        return name;
    }

    public void setName(String name){

        this.name = name;
    }
}
```

---

Characteristics:

```text id="enc043"
Simple Class

No Framework Dependency

Private Fields

Public Getters/Setters
```

---

Widely Used In:

```text id="enc044"
REST Assured

Spring Boot

Hibernate

Jackson
```

---

# 11. JavaBeans

JavaBean is a specialized POJO.

Requirements:

```text id="enc045"
Private Variables

Public Getter/Setter

No-Arg Constructor

Serializable
```

---

Example:

```java id="enc046"
public class UserBean {

    private String name;

    public UserBean(){

    }

    public String getName(){

        return name;
    }

    public void setName(String name){

        this.name = name;
    }
}
```

---

Interview Question:

```text id="enc047"
Difference Between POJO And JavaBean?
```

Answer:

```text id="enc048"
Every JavaBean is a POJO.

Not every POJO is a JavaBean.
```

---

# 12. DTO (Data Transfer Object)

DTO:

```text id="enc049"
Data Transfer Object
```

---

Purpose:

```text id="enc050"
Transfer Data Between Layers
```

---

Example:

```java id="enc051"
class UserDTO {

    private String username;

    private String email;

}
```

---

Common Usage:

```text id="enc052"
API Requests

API Responses

Microservices
```

---

# 13. Builder Pattern

Advanced Encapsulation Technique.

Without Builder:

```java id="enc053"
Employee emp =
new Employee(
"Rahul",
30,
50000,
"Mumbai",
"QA"
);
```

---

Difficult To Read.

---

Builder:

```java id="enc054"
Employee emp =
new EmployeeBuilder()
.setName("Rahul")
.setAge(30)
.build();
```

---

Benefits:

```text id="enc055"
Readable

Flexible

Maintainable
```

---

Frequently Used In:

```text id="enc056"
Lombok

Selenium Frameworks

REST Clients
```

---

# 14. Encapsulation in Selenium Frameworks

Page Object Example:

```java id="enc057"
public class LoginPage {

    private WebDriver driver;

}
```

---

Why Private?

```text id="enc058"
Prevent Direct Driver Manipulation
```

---

Methods Exposed:

```java id="enc059"
login()

logout()

clickLogin()
```

---

Encapsulation Protects:

```text id="enc060"
Locators

Driver

Internal Logic
```

---

# 15. Encapsulation in API Frameworks

Example:

```java id="enc061"
public class UserService {

    private RequestSpecification request;
}
```

---

Methods:

```java id="enc062"
createUser()

updateUser()

deleteUser()
```

---

Advantages:

```text id="enc063"
Hide Implementation Details

Expose Only Service Methods
```

---

# 16. Advantages of Encapsulation

```text id="enc064"
Security

Validation

Flexibility

Maintainability

Reusability

Loose Coupling
```

---

Framework Benefits:

```text id="enc065"
Cleaner Architecture

Easier Refactoring

Protected Internal Logic
```

---

# 17. Disadvantages of Encapsulation

Generally minimal.

Possible Issues:

```text id="enc066"
More Code

Additional Methods

Slight Complexity
```

---

Trade-off Worth It.

---

# 18. Common Interview Traps

### Trap 1

```text id="enc067"
Is Data Hiding Same As Encapsulation?
```

Answer:

```text id="enc068"
No
```

---

### Trap 2

```text id="enc069"
Can Encapsulation Exist Without Getters?
```

Answer:

```text id="enc070"
Yes
```

---

### Trap 3

```text id="enc071"
Can Immutable Class Be Encapsulated?
```

Answer:

```text id="enc072"
Yes
```

---

### Trap 4

```text id="enc073"
Is String Encapsulated?
```

Answer:

```text id="enc074"
Yes
```

---

# 19. Top Interview Questions

### Q1 What Is Encapsulation?

```text id="enc075"
Binding data and methods together
while restricting direct access.
```

---

### Q2 Why Use Private Variables?

```text id="enc076"
To protect data from direct modification.
```

---

### Q3 What Is Data Hiding?

```text id="enc077"
Restricting access using access modifiers.
```

---

### Q4 What Is Immutable Class?

```text id="enc078"
Class whose objects cannot be modified after creation.
```

---

### Q5 Difference Between POJO And JavaBean?

```text id="enc079"
JavaBean follows additional conventions
like no-arg constructor and serialization.
```

---

### Q6 Why Is Encapsulation Important In Frameworks?

```text id="enc080"
Protects internal implementation and improves maintainability.
```

---

# 20. Revision Notes

```text id="enc081"
Encapsulation

↓

Data Hiding

↓

Private Variables

↓

Getters/Setters

↓

Validation

↓

Security

Special Concepts

POJO

JavaBean

DTO

Immutable Class

Builder Pattern
```

---

# 21. Final Cheat Sheet

```text id="enc082"
private Variables

↓

Data Hidden

public Methods

↓

Controlled Access

Getter

↓

Read Data

Setter

↓

Write Data

Immutable Class

↓

No Modification

POJO

↓

Simple Object

JavaBean

↓

POJO + Rules

DTO

↓

Data Transfer

Builder

↓

Flexible Object Creation
```

---

# Interview Takeaway

If interviewer asks:

```text id="enc083"
Explain Encapsulation with a real project example.
```

Strong Answer:

```text id="enc084"
Encapsulation is the process of hiding internal
data and exposing controlled access through methods.

In Selenium frameworks, page locators and WebDriver
instances are usually private, while public methods
such as login() and searchProduct() expose business
actions. This prevents direct manipulation of internal
framework components and improves maintainability,
security and scalability.
```

---

# End of OOP Part 3

## Next Part

```text id="enc085"
Part 4 → Inheritance Deep Dive

Topics:

✓ Types Of Inheritance

✓ extends Keyword

✓ IS-A Relationship

✓ Method Inheritance

✓ Constructor Inheritance Rules

✓ super Keyword

✓ Method Overriding Basics

✓ Runtime Polymorphism Foundation

✓ Selenium Framework Examples

✓ API Framework Examples

✓ Real Project Scenarios

✓ Interview Questions

✓ Revision Notes
```
