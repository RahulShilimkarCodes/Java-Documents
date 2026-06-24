# Java Abstraction Master Guide – Part 9

## Design Patterns Using Abstraction (Interview + Framework Design)

---

# Table of Contents

1. Introduction to Design Patterns
2. Why Abstraction is Core to Design Patterns
3. Template Method Pattern
4. Strategy Pattern
5. Factory Pattern
6. Builder Pattern
7. Singleton + Abstraction Usage
8. Real Selenium Framework Architecture
9. Spring Boot Architecture Usage
10. REST API Design Patterns
11. UML Thinking for Interviews
12. Common Coding Scenarios
13. Common Mistakes
14. Advanced Interview Questions
15. Tricky Interview Questions
16. Revision Notes
17. Cheat Sheet
18. Summary
19. Practice Questions

---

# 1. Introduction to Design Patterns

Design Patterns are reusable solutions to common software design problems.

They are NOT code, but:

```text id="dp1"
blueprints for solving problems
```

---

# 2. Why Abstraction is Core to Design Patterns

Design patterns rely heavily on:

* Interfaces
* Abstract classes
* Polymorphism
* Loose coupling

---

Example:

```text id="dp2"
Strategy Pattern = Interface Abstraction
Factory Pattern = Object creation abstraction
Template Pattern = Algorithm abstraction
```

---

# 3. Template Method Pattern

Defines skeleton of algorithm.

Steps are fixed, but implementation varies.

---

## Example:

```java id="tp1"
abstract class DataParser {

    public final void parse() {

        readFile();
        processData();
        saveData();
    }

    abstract void readFile();
    abstract void processData();
    abstract void saveData();
}
```

---

## Implementation:

```java id="tp2"
class CSVParser extends DataParser {

    void readFile() {
        System.out.println("Reading CSV");
    }

    void processData() {
        System.out.println("Processing CSV");
    }

    void saveData() {
        System.out.println("Saving CSV");
    }
}
```

---

## Key Idea:

```text id="tp3"
Algorithm fixed
Steps flexible
```

---

# 4. Strategy Pattern

Encapsulates multiple algorithms.

---

## Interface:

```java id="sp1"
interface PaymentStrategy {
    void pay(int amount);
}
```

---

## Implementations:

```java id="sp2"
class UPIPayment implements PaymentStrategy {

    public void pay(int amount) {
        System.out.println("UPI: " + amount);
    }
}
```

```java id="sp3"
class CardPayment implements PaymentStrategy {

    public void pay(int amount) {
        System.out.println("Card: " + amount);
    }
}
```

---

## Usage:

```java id="sp4"
PaymentStrategy strategy =
    new UPIPayment();

strategy.pay(1000);
```

---

## Benefit:

```text id="sp5"
Runtime behavior change without modifying code
```

---

# 5. Factory Pattern

Creates objects without exposing creation logic.

---

## Interface:

```java id="fp1"
interface Vehicle {
    void drive();
}
```

---

## Implementations:

```java id="fp2"
class Car implements Vehicle {
    public void drive() {
        System.out.println("Car driving");
    }
}
```

---

## Factory:

```java id="fp3"
class VehicleFactory {

    public static Vehicle getVehicle(String type) {

        if(type.equals("car"))
            return new Car();

        return null;
    }
}
```

---

## Usage:

```java id="fp4"
Vehicle v =
    VehicleFactory.getVehicle("car");

v.drive();
```

---

# 6. Builder Pattern

Used for complex object creation.

---

## Example:

```java id="bp1"
class User {

    private String name;
    private int age;

    User(UserBuilder builder) {
        this.name = builder.name;
        this.age = builder.age;
    }
}
```

---

## Builder:

```java id="bp2"
class UserBuilder {

    String name;
    int age;

    UserBuilder setName(String name) {
        this.name = name;
        return this;
    }

    UserBuilder setAge(int age) {
        this.age = age;
        return this;
    }

    User build() {
        return new User(this);
    }
}
```

---

## Usage:

```java id="bp3"
User user =
    new UserBuilder()
    .setName("Rahul")
    .setAge(25)
    .build();
```

---

# 7. Singleton + Abstraction Usage

Singleton ensures one instance.

---

## Example:

```java id="sg1"
class DBConnection {

    private static DBConnection instance;

    private DBConnection() {}

    public static DBConnection getInstance() {

        if(instance == null) {
            instance = new DBConnection();
        }

        return instance;
    }
}
```

---

## With Abstraction:

```java id="sg2"
DBConnection conn =
    DBConnection.getInstance();
```

---

# 8. Real Selenium Framework Architecture

---

## Core Design:

```text id="sf1"
WebDriver (Interface)
    |
ChromeDriver / FirefoxDriver
```

---

## Page Object Model:

```java id="sf2"
class LoginPage {

    WebDriver driver;

    public LoginPage(WebDriver driver) {
        this.driver = driver;
    }
}
```

---

## Why Abstraction?

* Switch browsers easily
* Reusable test logic
* Maintainable framework

---

# 9. Spring Boot Architecture Usage

---

## Service Layer:

```java id="sb1"
interface UserService {
    void createUser();
}
```

---

## Implementation:

```java id="sb2"
@Service
class UserServiceImpl
implements UserService {

    public void createUser() {
        System.out.println("User created");
    }
}
```

---

## Controller:

```java id="sb3"
@Autowired
UserService service;
```

---

## Benefit:

```text id="sb4"
Loose coupling + dependency injection
```

---

# 10. REST API Design Patterns

---

## Controller → Service → Repository

```text id="api1"
Controller → Interface → Implementation → DB
```

---

## Example:

```java id="api2"
interface UserRepository {
    User findUser();
}
```

---

## Implementation hidden using abstraction

---

# 11. UML Thinking for Interviews

---

## Class Diagram Concept:

```text id="uml1"
Interface → Class → Object
```

---

## Relationship Types:

```text id="uml2"
Inheritance (extends)
Implementation (implements)
Association (uses)
```

---

# 12. Common Coding Scenarios

---

## Scenario 1: Switch Payment Methods

```java id="cs1"
PaymentStrategy p =
    new CardPayment();
```

---

## Scenario 2: Browser Switching

```java id="cs2"
WebDriver driver =
    new ChromeDriver();
```

---

# 13. Common Mistakes

---

## Mistake 1

Hardcoding implementations

---

## Mistake 2

Not using interfaces

---

## Mistake 3

Tight coupling in frameworks

---

# 14. Advanced Interview Questions

---

## Q1

Why use design patterns?

Answer:

To solve recurring design problems in a reusable way.

---

## Q2

Why is Strategy Pattern used?

Answer:

To change behavior at runtime.

---

## Q3

What is Factory Pattern?

Answer:

Encapsulates object creation logic.

---

## Q4

What is Template Pattern?

Answer:

Defines fixed algorithm structure.

---

## Q5

Why abstraction is important in frameworks?

Answer:

To decouple implementation from usage.

---

# 15. Tricky Interview Questions

---

## Q1

Can Strategy Pattern work without interface?

Answer:

No, interface is core.

---

## Q2

Is Factory Pattern abstraction?

Answer:

Yes, it hides object creation.

---

## Q3

Can Builder Pattern exist without abstraction?

Answer:

No, it relies on encapsulation and fluent interfaces.

---

## Q4

Is WebDriver a design pattern?

Answer:

It uses Factory + Strategy + Abstraction concepts.

---

## Q5

Can we combine multiple design patterns?

Answer:

Yes, in real frameworks.

---

# 16. Revision Notes

```text id="rn1"
Design Patterns + Abstraction
-----------------------------

Strategy → Behavior change
Factory → Object creation
Template → Algorithm structure
Builder → Complex object creation
Singleton → Single instance

Core Idea:
----------
Loose coupling + reusability
```

---

# 17. Cheat Sheet

```text id="cs1"
Strategy → interface + runtime swap
Factory → hides object creation
Template → fixed steps + override hooks
Builder → step-by-step object creation
Singleton → single instance
```

---

# 18. Summary

Design patterns are the backbone of scalable applications.

They heavily depend on abstraction:

* Interfaces
* Abstract classes
* Polymorphism

Used in:

* Selenium frameworks
* Spring Boot architecture
* Microservices
* Enterprise systems

---

# 19. Practice Questions

1. What is Strategy Pattern?
2. What is Factory Pattern?
3. What is Template Method Pattern?
4. Why use design patterns?
5. How does Selenium use design patterns?
6. How does Spring use abstraction?
7. Difference between Factory and Builder?
8. Can patterns be combined?
9. Why is WebDriver abstraction important?
10. What is loose coupling?
11. Explain real framework design.
12. What is dependency injection?
13. Why use interfaces in design patterns?
14. What is runtime polymorphism?
15. Explain architecture of automation framework.
