# Java Methods Master Guide

# Part 6 - Method Overriding

---

# Table of Contents

1. Introduction
2. What is Method Overriding?
3. Why Method Overriding is Needed
4. Overloading vs Overriding
5. Rules of Method Overriding
6. Inheritance and Overriding
7. @Override Annotation
8. Runtime Polymorphism
9. Dynamic Method Dispatch
10. Upcasting and Overriding
11. Covariant Return Types
12. Access Modifiers and Overriding
13. Final, Static and Private Methods
14. Real Project Examples
15. Selenium Framework Usage
16. API Framework Usage
17. Common Beginner Mistakes
18. Advanced Interview Questions
19. Quick Revision Notes
20. Final Cheat Sheet

---

# 1. Introduction

In Part 5 we learned:

* Method Overloading
* Compile Time Polymorphism
* Method Signatures
* Type Promotion

In this part we will learn:

```text id="or1"
Method Overriding

Runtime Polymorphism

Dynamic Method Dispatch

Inheritance

Real Framework Usage
```

Method Overriding is one of the most important OOP concepts and is frequently asked in Java, Selenium, and SDET interviews.

---

# 2. What is Method Overriding?

Definition:

```text id="or2"
Method Overriding occurs when a child class
provides its own implementation of a method
already defined in the parent class.
```

---

Example:

Parent Class:

```java id="or3"
class Animal{

    public void sound(){

        System.out.println("Animal Sound");
    }
}
```

Child Class:

```java id="or4"
class Dog extends Animal{

    public void sound(){

        System.out.println("Dog Barks");
    }
}
```

---

Call:

```java id="or5"
Dog dog = new Dog();

dog.sound();
```

Output:

```text id="or6"
Dog Barks
```

---

# 3. Why Method Overriding is Needed

Suppose every animal has a different sound.

Without Overriding:

```java id="or7"
animalSound();

dogSound();

catSound();

lionSound();
```

Poor design.

---

With Overriding:

```java id="or8"
sound();
```

Each child provides its own implementation.

Advantages:

```text id="or9"
Flexibility

Code Reusability

Runtime Decision Making

Better OOP Design
```

---

# 4. Overloading vs Overriding

Most Asked Interview Question.

| Feature      | Overloading  | Overriding         |
| ------------ | ------------ | ------------------ |
| Class        | Same Class   | Parent & Child     |
| Parameters   | Different    | Same               |
| Return Type  | Can Differ   | Must Be Compatible |
| Polymorphism | Compile Time | Runtime            |
| Inheritance  | Not Required | Required           |

---

Example Overloading:

```java id="or10"
add(int a,int b)

add(int a,int b,int c)
```

---

Example Overriding:

```java id="or11"
Parent → sound()

Child → sound()
```

---

# 5. Rules of Method Overriding

For valid overriding:

---

## Rule 1

Method Name Must Be Same

Parent:

```java id="or12"
sound()
```

Child:

```java id="or13"
sound()
```

---

## Rule 2

Parameter List Must Be Same

Parent:

```java id="or14"
display(String name)
```

Child:

```java id="or15"
display(String name)
```

---

## Rule 3

Inheritance Must Exist

Example:

```java id="or16"
class Dog extends Animal
```

---

## Rule 4

Return Type Must Be Compatible

Will be discussed later.

---

# 6. Inheritance and Overriding

Overriding is impossible without inheritance.

Parent:

```java id="or17"
class Vehicle{

    public void start(){

        System.out.println("Vehicle Started");
    }
}
```

---

Child:

```java id="or18"
class Car extends Vehicle{

    public void start(){

        System.out.println("Car Started");
    }
}
```

---

Output:

```text id="or19"
Car Started
```

---

# 7. @Override Annotation

Best Practice.

Example:

```java id="or20"
@Override
public void start(){

    System.out.println("Car Started");
}
```

---

Benefits:

```text id="or21"
Compile Time Validation

Improved Readability

Detects Mistakes Early
```

---

Example Error:

```java id="or22"
@Override
public void starts(){

}
```

Compiler detects issue immediately.

---

# 8. Runtime Polymorphism

Method Overriding is also called:

```text id="or23"
Runtime Polymorphism
```

Reason:

Actual method is selected during runtime.

---

Example:

```java id="or24"
Animal animal =
new Dog();

animal.sound();
```

Output:

```text id="or25"
Dog Barks
```

Compiler sees:

```text id="or26"
Animal
```

Runtime executes:

```text id="or27"
Dog
```

method.

---

# 9. Dynamic Method Dispatch

Extremely Important Interview Topic.

Definition:

```text id="or28"
The process through which
an overridden method call
is resolved at runtime.
```

---

Example:

```java id="or29"
Animal animal =
new Dog();

animal.sound();
```

Execution:

```text id="or30"
Reference Type
Animal

↓

Object Type
Dog

↓

Dog's Method Executes
```

---

This mechanism is called:

```text id="or31"
Dynamic Method Dispatch
```

---

# 10. Upcasting and Overriding

Common Interview Question.

Example:

```java id="or32"
Animal animal =
new Dog();
```

Called:

```text id="or33"
Upcasting
```

---

Why Used?

```text id="or34"
Supports Runtime Polymorphism
```

---

Method Call:

```java id="or35"
animal.sound();
```

Output:

```text id="or36"
Dog Barks
```

---

# 11. Covariant Return Types

Advanced Interview Topic.

Parent:

```java id="or37"
class Animal{

    Animal getAnimal(){

        return new Animal();
    }
}
```

---

Child:

```java id="or38"
class Dog extends Animal{

    Dog getAnimal(){

        return new Dog();
    }
}
```

Valid.

---

Reason:

```text id="or39"
Child return type
is more specific.
```

This is called:

```text id="or40"
Covariant Return Type
```

---

# 12. Access Modifiers and Overriding

Important Rule.

Parent:

```java id="or41"
public void test(){

}
```

Child:

```java id="or42"
public void test(){

}
```

Valid.

---

Cannot Reduce Visibility.

Invalid:

```java id="or43"
protected void test(){

}
```

if parent method is public.

---

Rule:

```text id="or44"
Visibility Can Increase

Visibility Cannot Decrease
```

---

# 13. Final, Static and Private Methods

Frequently Asked.

---

## Final Methods

Cannot Override.

Example:

```java id="or45"
final void display(){

}
```

---

Attempt:

```java id="or46"
@Override
void display(){

}
```

Compilation Error.

---

## Static Methods

Not Overridden.

They are:

```text id="or47"
Method Hidden
```

---

## Private Methods

Cannot Override.

Reason:

```text id="or48"
Not Visible In Child Class
```

---

# 14. Real Project Examples

---

## Report Generation

Parent:

```java id="or49"
generateReport()
```

---

Child:

```java id="or50"
generateReport()
```

Different implementation.

---

## Browser Launch

Parent:

```java id="or51"
launchBrowser()
```

---

Chrome:

```java id="or52"
launchBrowser()
```

---

Firefox:

```java id="or53"
launchBrowser()
```

---

# 15. Selenium Framework Usage

Example:

Base Page:

```java id="or54"
click()
```

---

Custom Page:

```java id="or55"
click()
```

Enhanced implementation.

---

Driver Example:

```java id="or56"
WebDriver driver;
```

Runtime:

```java id="or57"
ChromeDriver

FirefoxDriver

EdgeDriver
```

Different implementations execute.

---

This is Runtime Polymorphism.

---

# 16. API Framework Usage

Base Service:

```java id="or58"
sendRequest()
```

---

Child Services:

```java id="or59"
sendRequest()
```

Custom implementation.

---

Authentication Service:

```java id="or60"
authenticate()
```

Can be overridden.

---

# 17. Common Beginner Mistakes

---

## Mistake 1

Different Parameters

Parent:

```java id="or61"
test(int a)
```

Child:

```java id="or62"
test()
```

Not overriding.

Overloading instead.

---

## Mistake 2

Missing Inheritance

No inheritance means:

```text id="or63"
No Overriding
```

---

## Mistake 3

Trying To Override Static Method

Not allowed.

---

## Mistake 4

Trying To Override Final Method

Compilation Error.

---

# 18. Advanced Interview Questions

---

## Q1 What is Method Overriding?

Answer:

```text id="or64"
Child class provides its own
implementation of parent method.
```

---

## Q2 What is Runtime Polymorphism?

Answer:

```text id="or65"
Method execution decided at runtime.
```

---

## Q3 What is Dynamic Method Dispatch?

Answer:

```text id="or66"
Runtime mechanism used to determine
which overridden method executes.
```

---

## Q4 Can Static Methods Be Overridden?

Answer:

```text id="or67"
No

Only Method Hiding Occurs
```

---

## Q5 Can Final Methods Be Overridden?

Answer:

```text id="or68"
No
```

---

## Q6 Can Private Methods Be Overridden?

Answer:

```text id="or69"
No
```

---

## Q7 What is Covariant Return Type?

Answer:

```text id="or70"
Child method returns
more specific return type.
```

---

# 19. Quick Revision Notes

```text id="or71"
Method Overriding

Parent + Child Classes

Same Method Name

Same Parameters

Runtime Polymorphism

Dynamic Method Dispatch

@Override Recommended

Static Methods Not Overridden

Final Methods Not Overridden

Private Methods Not Overridden

Covariant Return Types Supported
```

---

# 20. Final Cheat Sheet

```text id="or72"
Method Overriding

Inheritance Required

Same Name

Same Parameters

Runtime Polymorphism

Dynamic Method Dispatch

Example

Animal animal =
new Dog();

animal.sound();

Output

Dog Sound

Annotation

@Override

Cannot Override

final methods

private methods

static methods
```

---

# Interview Takeaway

If interviewer asks:

```text id="or73"
Explain Method Overriding with Runtime Polymorphism.
```

Strong Answer:

```text id="or74"
Method Overriding occurs when a child class
provides its own implementation of a method
defined in the parent class.

Overriding enables Runtime Polymorphism,
where the JVM decides at runtime which
implementation should execute based on
the actual object type.

This mechanism is called Dynamic Method Dispatch
and is one of the core principles of Object-Oriented Programming.
```

---

# End of Part 6

## Next Part

Part 7 → Pass By Value Deep Dive

Topics:

* Java Pass By Value
* Primitive Variables
* Object References
* String Parameters
* Array Parameters
* Memory Diagrams
* JVM Internals
* Interview Traps
* Real Project Examples
