# Java Abstraction Master Guide – Part 5

## Java 8 Interface Enhancements, Functional Interfaces & Lambda Expressions

---

# Table of Contents

1. Why Java 8 Changed Interfaces
2. Problems Before Java 8
3. Default Methods
4. Static Methods in Interfaces
5. Functional Interfaces
6. @FunctionalInterface Annotation
7. Lambda Expressions
8. Method References
9. Built-in Functional Interfaces
10. Predicate
11. Function
12. Consumer
13. Supplier
14. Real Project Examples
15. Selenium Framework Usage
16. Spring Boot Usage
17. Stream API Relation
18. Common Mistakes
19. Advanced Interview Questions
20. Tricky Interview Questions
21. Revision Notes
22. Cheat Sheet
23. Summary
24. Practice Questions

---

# 1. Why Java 8 Changed Interfaces

Before Java 8:

Interfaces could contain only:

```java
public abstract methods
public static final variables
```

Example:

```java
interface Vehicle {
    void start();
}
```

---

Problem:

Suppose thousands of projects implement:

```java
interface Vehicle {
    void start();
}
```

Now company wants:

```java
void stop();
```

Added to interface:

```java
interface Vehicle {
    void start();
    void stop();
}
```

Result:

```text
Thousands of implementing classes break.
Compilation fails.
```

Java 8 introduced:

```text
Default Methods
Static Methods
```

to solve this issue.

---

# 2. Problems Before Java 8

Example:

```java
interface Notification {

    void send();
}
```

100 classes implement it.

Adding:

```java
void log();
```

requires updating all 100 classes.

Huge maintenance problem.

---

Solution:

```java
default void log() {

}
```

Existing implementations continue working.

---

# 3. Default Methods

Definition:

A default method is a method with implementation inside an interface.

---

Syntax:

```java
interface Vehicle {

    default void stop() {

        System.out.println("Vehicle Stopped");
    }
}
```

---

Usage:

```java
class Car implements Vehicle {

}
```

---

Execution:

```java
Car car = new Car();
car.stop();
```

Output:

```text
Vehicle Stopped
```

---

# Why Default Methods?

To add new functionality without breaking existing implementations.

---

# Default Method Example

```java
interface Payment {

    void pay();

    default void printReceipt() {

        System.out.println("Receipt Generated");
    }
}
```

---

Implementation:

```java
class UPIPayment
implements Payment {

    public void pay() {

        System.out.println("UPI Payment");
    }
}
```

---

Execution:

```java
Payment payment =
        new UPIPayment();

payment.printReceipt();
```

Output:

```text
Receipt Generated
```

---

# 4. Overriding Default Methods

Default methods can be overridden.

---

Interface:

```java
interface Vehicle {

    default void start() {

        System.out.println("Vehicle Started");
    }
}
```

---

Class:

```java
class Car
implements Vehicle {

    @Override
    public void start() {

        System.out.println("Car Started");
    }
}
```

Output:

```text
Car Started
```

---

# 5. Static Methods in Interfaces

Java 8 introduced static methods inside interfaces.

---

Syntax:

```java
interface Utility {

    static void print() {

        System.out.println("Utility Method");
    }
}
```

---

Usage:

```java
Utility.print();
```

Output:

```text
Utility Method
```

---

# Why Static Methods?

Common utility logic.

Example:

```java
interface ValidationUtil {

    static boolean isValidEmail(
            String email) {

        return email.contains("@");
    }
}
```

Usage:

```java
ValidationUtil.isValidEmail(
        "test@gmail.com");
```

---

# Important Rule

Cannot be overridden.

---

Invalid:

```java
class Test
implements ValidationUtil {

}
```

No overriding possible.

---

# 6. Functional Interfaces

One of the most important Java 8 interview topics.

---

Definition:

A Functional Interface contains exactly one abstract method.

---

Example:

```java
interface Calculator {

    int add(int a, int b);
}
```

Valid Functional Interface.

---

Example:

```java
interface Employee {

    void login();

    void logout();
}
```

Not Functional Interface.

Contains 2 abstract methods.

---

# Why Functional Interfaces?

Designed for:

```text
Lambda Expressions
Method References
Streams
```

---

# 7. @FunctionalInterface Annotation

Used to indicate functional interface.

---

Example:

```java
@FunctionalInterface
interface Calculator {

    int add(int a, int b);
}
```

---

Compiler Validation:

If second abstract method added:

```java
@FunctionalInterface
interface Calculator {

    int add(int a, int b);

    int subtract(int a, int b);
}
```

Compilation Error.

---

# Benefits

```text
Readability
Validation
Best Practice
```

---

# 8. Lambda Expressions

Before Java 8:

```java
interface Calculator {

    int add(int a, int b);
}
```

Implementation:

```java
class CalculatorImpl
implements Calculator {

    public int add(
        int a,
        int b) {

        return a + b;
    }
}
```

---

Java 8 Lambda:

```java
Calculator calculator =
    (a,b) -> a + b;
```

---

Execution:

```java
System.out.println(
    calculator.add(10,20));
```

Output:

```text
30
```

---

# Lambda Syntax

General Form:

```java
(parameters) -> expression
```

---

Example:

```java
name -> System.out.println(name)
```

---

Example:

```java
(a,b) -> a+b
```

---

Example:

```java
() -> System.out.println("Hello")
```

---

# 9. Method References

Used to simplify lambdas.

---

Lambda:

```java
list.forEach(
    name ->
    System.out.println(name));
```

---

Method Reference:

```java
list.forEach(
    System.out::println);
```

Cleaner.

Readable.

---

# Types of Method References

---

## Static Method Reference

```java
ClassName::methodName
```

Example:

```java
Math::max
```

---

## Instance Method Reference

```java
object::methodName
```

Example:

```java
employee::getName
```

---

## Constructor Reference

```java
ClassName::new
```

Example:

```java
ArrayList::new
```

---

# 10. Built-In Functional Interfaces

Java provides ready-made interfaces.

Located in:

```java
java.util.function
```

Package.

---

Most Important:

```text
Predicate
Function
Consumer
Supplier
```

---

# 11. Predicate

Represents:

```text
Condition Check
```

Method:

```java
boolean test(T t)
```

---

Example:

```java
Predicate<Integer> even =
        num -> num % 2 == 0;
```

Usage:

```java
System.out.println(
        even.test(10));
```

Output:

```text
true
```

---

Real Use:

```text
Filtering Data
Validation
Search Conditions
```

---

# 12. Function

Represents:

```text
Input → Output
```

Method:

```java
R apply(T t)
```

---

Example:

```java
Function<String,Integer>
length =
    str -> str.length();
```

Execution:

```java
length.apply("Java");
```

Output:

```text
4
```

---

# 13. Consumer

Consumes input.

Returns nothing.

---

Method:

```java
accept(T t)
```

---

Example:

```java
Consumer<String> printer =
    name ->
        System.out.println(name);
```

Execution:

```java
printer.accept("Rahul");
```

Output:

```text
Rahul
```

---

# 14. Supplier

Provides data.

No input.

Returns value.

---

Method:

```java
get()
```

---

Example:

```java
Supplier<String> supplier =
    () -> "Hello";
```

Execution:

```java
supplier.get();
```

Output:

```text
Hello
```

---

# 15. Real Project Example

Notification Service

---

Functional Interface:

```java
@FunctionalInterface
interface Notification {

    void send(String message);
}
```

---

Lambda:

```java
Notification email =
    msg ->
    System.out.println(
            "Email: " + msg);
```

---

Usage:

```java
email.send("Welcome");
```

Output:

```text
Email: Welcome
```

---

# 16. Selenium Framework Usage

Common Usage:

```java
WebDriverWait wait =
    new WebDriverWait(
        driver,
        Duration.ofSeconds(10));
```

---

Lambda:

```java
wait.until(
    driver ->
        driver.findElement(
            By.id("login"))
            .isDisplayed());
```

---

Functional Interface used internally.

---

# 17. Spring Boot Usage

Dependency Injection often uses:

```java
Supplier
Function
Predicate
```

Internally.

---

Spring Security:

```java
Authentication ->
    Authorization
```

Uses functional programming concepts heavily.

---

# 18. Stream API Relation

Stream API relies heavily on:

```text
Predicate
Function
Consumer
```

---

Filtering:

```java
list.stream()
    .filter(
        num -> num > 10)
    .forEach(
        System.out::println);
```

---

Components:

```text
Lambda
Method Reference
Functional Interface
```

work together.

---

# 19. Common Mistakes

---

## Mistake 1

Creating multiple abstract methods.

```java
@FunctionalInterface
interface Test {

    void a();

    void b();
}
```

Compilation Error.

---

## Mistake 2

Trying to override interface static method.

Not allowed.

---

## Mistake 3

Using lambda with non-functional interface.

Compilation Error.

---

# 20. Advanced Interview Questions

---

## Q1

What is a Default Method?

Answer:

A method with implementation inside interface introduced in Java 8.

---

## Q2

Why Default Methods were introduced?

Answer:

To avoid breaking existing implementations.

---

## Q3

What is Functional Interface?

Answer:

An interface with exactly one abstract method.

---

## Q4

Can Functional Interface contain default methods?

Answer:

Yes.

---

## Q5

Can Functional Interface contain static methods?

Answer:

Yes.

---

## Q6

What is Lambda Expression?

Answer:

A concise way to implement functional interfaces.

---

## Q7

What is Method Reference?

Answer:

Short-hand syntax for lambda expressions.

---

## Q8

Difference between Function and Predicate?

Answer:

| Function      | Predicate       |
| ------------- | --------------- |
| Returns Value | Returns Boolean |
| apply()       | test()          |

---

# 21. Tricky Interview Questions

---

## Q1

Can interface have implemented methods?

Answer:

Yes.

Using default methods.

---

## Q2

Can functional interface extend another interface?

Answer:

Yes.

Provided only one abstract method remains.

---

## Q3

Can lambda access local variables?

Answer:

Yes.

If effectively final.

---

## Q4

Can default methods be overridden?

Answer:

Yes.

---

## Q5

Can static methods be inherited?

Answer:

No.

Called using interface name.

---

# 22. Revision Notes

```text
Java 8 Interface Features
-------------------------

Default Methods

Static Methods

Functional Interfaces

Lambda Expressions

Method References

Built-in Functional Interfaces

Predicate
Function
Consumer
Supplier
```

---

# 23. Cheat Sheet

```text
Default Method
---------------
default keyword

Static Method
---------------
InterfaceName.method()

Functional Interface
---------------
One Abstract Method

Lambda
---------------
() -> {}

Method Reference
---------------
System.out::println

Built-in Interfaces
---------------
Predicate
Function
Consumer
Supplier
```

---

# 24. Summary

Java 8 completely transformed interfaces by introducing:

* Default Methods
* Static Methods
* Functional Interfaces
* Lambda Expressions
* Method References

These features enabled:

* Functional Programming
* Stream API
* Cleaner Code
* Better Framework Design

Today they are heavily used in:

* Selenium
* Spring Boot
* REST Assured
* Microservices
* Enterprise Applications

---

# 25. Practice Questions

1. Why were default methods introduced?
2. What is a functional interface?
3. What is @FunctionalInterface?
4. Explain lambda expressions.
5. Explain method references.
6. Difference between Predicate and Function?
7. Difference between Consumer and Supplier?
8. Can functional interfaces have default methods?
9. Can static methods be overridden?
10. Explain lambda usage in Selenium.
11. Explain lambda usage in Stream API.
12. What are built-in functional interfaces?
13. Explain constructor references.
14. Explain instance method references.
15. Explain Java 8 interface enhancements in detail.
