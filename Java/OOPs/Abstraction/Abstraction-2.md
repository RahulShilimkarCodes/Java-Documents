# Java Abstraction Master Guide – Part 2

## Abstract Classes Deep Dive (Interview Preparation)

---

# Table of Contents

1. Introduction to Abstract Classes
2. Why Abstract Classes Were Introduced
3. Syntax of Abstract Class
4. Rules of Abstract Classes
5. Abstract Class Memory Structure
6. Abstract Methods
7. Concrete Methods
8. Constructors in Abstract Classes
9. Variables in Abstract Classes
10. Static Members
11. Final Members
12. Access Modifiers
13. Object Creation Rules
14. Abstract Class vs Normal Class
15. Abstract Class vs Interface
16. Real Project Examples
17. Selenium Framework Examples
18. Spring Framework Examples
19. Design Pattern Usage
20. Common Mistakes
21. JVM Internals
22. Interview Questions
23. Tricky Questions
24. Revision Notes
25. Cheat Sheet
26. Summary

---

# 1. Introduction to Abstract Classes

An abstract class is a class that cannot be instantiated directly and is designed to act as a base class for other classes.

It provides:

* Common behavior
* Common properties
* Partial implementation
* Shared business logic

---

## Definition

An abstract class is declared using the `abstract` keyword.

Example:

```java
abstract class Vehicle {

}
```

---

# 2. Why Abstract Classes Were Introduced

Imagine multiple classes share common functionality.

Example:

```java
Car
Bike
Truck
Bus
```

All vehicles may have:

```java
fuelType
engineNumber
start()
stop()
```

Instead of duplicating code:

```java
abstract class Vehicle {
    String fuelType;
    String engineNumber;

    void stop() {
        System.out.println("Vehicle Stopped");
    }
}
```

Inheritance promotes reuse.

---

# 3. Syntax of Abstract Class

Basic Syntax:

```java
abstract class Animal {

    abstract void sound();
}
```

Implementation:

```java
class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

---

# 4. Rules of Abstract Classes

## Rule 1

Must use `abstract` keyword.

```java
abstract class Employee {

}
```

---

## Rule 2

Cannot create object directly.

Invalid:

```java
Employee emp = new Employee();
```

Compiler Error.

---

## Rule 3

Can contain abstract methods.

```java
abstract void work();
```

---

## Rule 4

Can contain normal methods.

```java
void login() {

}
```

---

## Rule 5

Can contain constructors.

```java
Employee() {

}
```

---

## Rule 6

Can contain static methods.

```java
static void companyPolicy() {

}
```

---

## Rule 7

Can contain final methods.

```java
final void generateId() {

}
```

---

# 5. Abstract Class Memory Structure

Consider:

```java
abstract class Animal {

}
```

Child:

```java
class Dog extends Animal {

}
```

Object Creation:

```java
Animal animal = new Dog();
```

Memory:

```text
Stack
-----
animal
  |
  V

Heap
-----
Dog Object
```

Reference Type:

```java
Animal
```

Actual Object:

```java
Dog
```

---

# 6. Abstract Methods

An abstract method has:

* Declaration
* No implementation

Example:

```java
abstract class Shape {

    abstract void draw();
}
```

Invalid:

```java
abstract void draw() {

}
```

Abstract methods cannot have body.

---

# 7. Concrete Methods

Abstract classes may contain fully implemented methods.

Example:

```java
abstract class Vehicle {

    void stop() {
        System.out.println("Vehicle Stopped");
    }
}
```

Child classes inherit this method.

---

Example:

```java
class Car extends Vehicle {

}
```

Usage:

```java
Car car = new Car();
car.stop();
```

Output:

```text
Vehicle Stopped
```

---

# 8. Constructors in Abstract Classes

Most asked interview question.

---

## Can Abstract Class Have Constructor?

Answer:

Yes.

Example:

```java
abstract class Employee {

    Employee() {
        System.out.println("Employee Constructor");
    }
}
```

---

Child:

```java
class Developer extends Employee {

}
```

Execution:

```java
Developer developer =
        new Developer();
```

Output:

```text
Employee Constructor
```

---

Why Constructor?

To initialize common properties.

Example:

```java
abstract class Employee {

    String companyName;

    Employee() {
        companyName = "ABC Corp";
    }
}
```

---

# 9. Variables in Abstract Classes

Abstract classes can contain:

* Instance Variables
* Static Variables
* Final Variables

---

## Instance Variable

```java
abstract class Employee {

    String name;
}
```

---

## Static Variable

```java
abstract class Employee {

    static String companyName;
}
```

Shared among all objects.

---

## Final Variable

```java
abstract class Employee {

    final int id = 101;
}
```

Cannot be modified.

---

# 10. Static Members

Allowed inside abstract class.

Example:

```java
abstract class Utility {

    static void printMessage() {
        System.out.println("Welcome");
    }
}
```

Usage:

```java
Utility.printMessage();
```

Output:

```text
Welcome
```

---

# 11. Final Members

Example:

```java
abstract class Employee {

    final void companyRules() {

    }
}
```

Cannot be overridden.

---

Invalid:

```java
class Developer extends Employee {

    void companyRules() {

    }
}
```

Compilation Error.

---

# 12. Access Modifiers

Abstract methods can use:

```java
public
protected
default
```

Example:

```java
public abstract void login();
```

---

Invalid:

```java
private abstract void login();
```

Reason:

Private methods cannot be overridden.

Abstract methods require overriding.

---

# 13. Object Creation Rules

Invalid:

```java
abstract class Vehicle {

}

Vehicle vehicle =
    new Vehicle();
```

Compiler Error.

---

Valid:

```java
Vehicle vehicle =
    new Car();
```

Reason:

Object belongs to child class.

---

# 14. Abstract Class vs Normal Class

| Feature         | Abstract Class | Normal Class |
| --------------- | -------------- | ------------ |
| Object Creation | No             | Yes          |
| Abstract Method | Yes            | No           |
| Constructors    | Yes            | Yes          |
| Variables       | Yes            | Yes          |
| Static Methods  | Yes            | Yes          |
| Inheritance     | Yes            | Yes          |

---

# 15. Abstract Class vs Interface

| Feature              | Abstract Class | Interface |
| -------------------- | -------------- | --------- |
| Constructor          | Yes            | No        |
| Instance Variables   | Yes            | No        |
| Multiple Inheritance | No             | Yes       |
| Partial Abstraction  | Yes            | Yes       |
| Full Abstraction     | No             | Yes       |

---

# 16. Real Project Example

## Banking Application

```java
abstract class Account {

    String accountNumber;

    abstract void calculateInterest();

    void printAccountInfo() {
        System.out.println(accountNumber);
    }
}
```

---

Savings Account:

```java
class SavingsAccount extends Account {

    @Override
    void calculateInterest() {

    }
}
```

---

Current Account:

```java
class CurrentAccount extends Account {

    @Override
    void calculateInterest() {

    }
}
```

---

# 17. Selenium Framework Example

Framework Base Page:

```java
abstract class BasePage {

    protected WebDriver driver;

    BasePage(WebDriver driver) {
        this.driver = driver;
    }

    void click(By locator) {
        driver.findElement(locator).click();
    }
}
```

---

Login Page:

```java
class LoginPage extends BasePage {

    LoginPage(WebDriver driver) {
        super(driver);
    }
}
```

Common reusable logic lives in abstract class.

---

# 18. Spring Framework Example

Service Layer:

```java
public abstract class BaseService {

    public void audit() {

    }
}
```

Child Services:

```java
UserService
OrderService
ProductService
```

Reuse common logic.

---

# 19. Design Pattern Usage

## Template Method Pattern

One of the strongest uses of abstract classes.

Example:

```java
abstract class ReportGenerator {

    public final void generateReport() {

        fetchData();
        formatData();
        exportReport();
    }

    abstract void fetchData();

    abstract void formatData();

    abstract void exportReport();
}
```

Common flow fixed.

Implementation customizable.

---

# 20. Common Mistakes

### Mistake 1

Trying to instantiate abstract class.

```java
new Vehicle();
```

---

### Mistake 2

Not implementing abstract methods.

```java
class Car extends Vehicle {

}
```

Compilation Error.

---

### Mistake 3

Using interface when shared implementation is needed.

---

### Mistake 4

Overusing abstract classes.

---

# 21. JVM Internals

Code:

```java
Animal animal =
        new Dog();
```

Runtime:

```text
Reference Type = Animal

Object Type = Dog
```

Method Call:

```java
animal.sound();
```

JVM:

1. Looks at actual object.
2. Finds Dog implementation.
3. Executes Dog method.

Dynamic Method Dispatch.

---

# 22. Interview Questions

## Q1

What is an abstract class?

Answer:

A class declared using abstract keyword which cannot be instantiated and may contain abstract and concrete methods.

---

## Q2

Can abstract class have constructors?

Answer:

Yes.

Used for initialization.

---

## Q3

Can abstract class contain implemented methods?

Answer:

Yes.

---

## Q4

Can abstract class have static methods?

Answer:

Yes.

---

## Q5

Can abstract class have final methods?

Answer:

Yes.

---

## Q6

Can abstract class contain variables?

Answer:

Yes.

Instance, Static and Final variables.

---

## Q7

Why can't abstract classes be instantiated?

Answer:

Because they may contain incomplete methods.

---

## Q8

Can abstract class contain no abstract methods?

Answer:

Yes.

Example:

```java
abstract class Employee {

}
```

Valid.

---

# 23. Tricky Interview Questions

## Q1

Can constructor be abstract?

Answer:

No.

Constructors must have implementation.

---

## Q2

Can abstract method be static?

Answer:

No.

Static methods cannot be overridden.

---

## Q3

Can abstract method be final?

Answer:

No.

Final prevents overriding.

Abstract requires overriding.

---

## Q4

Can abstract class be final?

Answer:

No.

Final prevents inheritance.

Abstract requires inheritance.

---

## Q5

Can abstract class implement interface?

Answer:

Yes.

Example:

```java
abstract class Employee
        implements Serializable {

}
```

---

# 24. Revision Notes

```text
Abstract Class
=
Partial Abstraction

Cannot Instantiate

Can Have:
-------------
Constructor
Variables
Static Methods
Final Methods
Abstract Methods
Concrete Methods

Supports Inheritance

Used for Common Logic Sharing
```

---

# 25. Cheat Sheet

```text
Abstract Class
-------------------
abstract keyword

Cannot Create Object

Can Have Constructor

Can Have Variables

Can Have Abstract Methods

Can Have Concrete Methods

Used For Partial Abstraction

Parent Class Design
```

---

# 26. Summary

Abstract classes provide:

* Code Reuse
* Partial Abstraction
* Shared Implementation
* Common State Management
* Better Framework Design

Used heavily in:

* Selenium Frameworks
* Spring Boot Applications
* Enterprise Banking Systems
* Reporting Systems
* Template Method Pattern

Mastering abstract classes is essential before learning:

* Abstract Methods
* Runtime Polymorphism
* Interfaces
* Dependency Injection
* Design Patterns

---

# Practice Questions

1. What is an abstract class?
2. Why are abstract classes used?
3. Can abstract classes have constructors?
4. Can abstract classes have static methods?
5. Can abstract classes have final methods?
6. Can abstract classes contain variables?
7. Difference between abstract class and interface?
8. Explain abstract classes with Selenium framework.
9. Explain abstract classes with Spring Boot.
10. Why can't abstract classes be instantiated?
11. Can an abstract class contain no abstract methods?
12. Can abstract methods be static?
13. Can abstract methods be final?
14. Explain Template Method Pattern.
15. Explain abstract class from JVM perspective.
