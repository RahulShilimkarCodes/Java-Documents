# Java Exception Handling Master Guide

# Part 5 - throw, throws & Exception Propagation Deep Dive

---

# Table of Contents

1. Introduction
2. What is throw Keyword?
3. Why throw Exists
4. Syntax of throw
5. JVM Flow of throw
6. Built-in Exception Throwing
7. Custom Exception Throwing
8. What is throws Keyword?
9. Why throws Exists
10. Exception Propagation
11. Call Stack & Propagation Flow
12. throw vs throws
13. Real Project Examples
14. Selenium Framework Examples
15. REST Assured Examples
16. Enterprise Design Patterns
17. Common Mistakes
18. Interview Questions
19. Revision Notes
20. Final Cheat Sheet

---

# 1. Introduction

So far we have learned:

```text
try

catch

finally

try-with-resources
```

These mechanisms handle exceptions after they occur.

Now we will learn:

```text
throw

throws
```

which are responsible for:

```text
Creating Exceptions

Declaring Exceptions

Propagating Exceptions
```

---

# 2. What is throw Keyword?

The `throw` keyword is used to explicitly create and throw an exception.

Definition:

> The throw keyword is used to manually generate an exception object and transfer control to the exception handling mechanism.

---

Basic Example:

```java
public class Demo {

    public static void main(String[] args) {

        throw new RuntimeException(
            "Something Went Wrong"
        );
    }
}
```

Output:

```text
Exception in thread "main"
java.lang.RuntimeException:
Something Went Wrong
```

---

Important Observation:

```text
JVM Can Throw Exceptions

AND

Developers Can Throw Exceptions
```

---

# 3. Why throw Exists

Consider:

```java
withdraw(amount);
```

Business Rule:

```text
Amount Must Not Be Negative
```

Without throw:

```java
if(amount < 0){

    System.out.println("Invalid");
}
```

Problem:

```text
Execution Continues
```

---

Better:

```java
if(amount < 0){

    throw new IllegalArgumentException(
       "Negative Amount Not Allowed"
    );
}
```

Now:

```text
Execution Stops

Error Propagates

Can Be Handled Centrally
```

---

# 4. Syntax of throw

Syntax:

```java
throw exceptionObject;
```

Example:

```java
throw new ArithmeticException();
```

---

Another Example:

```java
throw new NullPointerException(
    "Name Cannot Be Null"
);
```

---

Flow:

```text
Create Exception Object

↓

Throw Exception

↓

Search Catch Block

↓

Handle Or Propagate
```

---

# 5. JVM Flow of throw

Example:

```java
throw new ArithmeticException(
    "Invalid Calculation"
);
```

Internally:

```text
Create Object

↓

Capture Stack Trace

↓

Transfer Control

↓

Search Catch Block

↓

Execute Handler
```

---

Important:

```text
throw Always Throws
One Exception Object
```

---

Valid:

```java
throw new IOException();
```

---

Invalid:

```java
throw "error";
```

Because:

```text
Only Throwable Objects
Can Be Thrown
```

---

# 6. Built-in Exception Throwing

Java libraries use throw extensively.

Example:

```java
String name = null;

Objects.requireNonNull(name);
```

Internally:

```java
if(name == null){

    throw new NullPointerException();
}
```

---

Array Example:

```java
int[] arr = {1,2,3};

System.out.println(arr[10]);
```

JVM automatically:

```java
throw new ArrayIndexOutOfBoundsException();
```

---

# 7. Custom Exception Throwing

Business Rule Example:

```java
public static void withdraw(
    double amount
){

    if(amount <= 0){

        throw new IllegalArgumentException(
           "Amount Must Be Positive"
        );
    }
}
```

Usage:

```java
withdraw(-100);
```

Output:

```text
IllegalArgumentException
```

---

Benefits:

```text
Clear Validation

Centralized Handling

Readable Code
```

---

# 8. What is throws Keyword?

The `throws` keyword is completely different from `throw`.

Definition:

> throws is used to declare exceptions that a method may generate.

---

Example:

```java
public void readFile()
throws IOException {

}
```

Meaning:

```text
This Method May Throw
IOException
```

---

Important:

```text
throws Does Not Throw

throws Only Declares
```

---

# 9. Why throws Exists

Consider:

```java
FileInputStream fis =
   new FileInputStream(
      "test.txt"
   );
```

Possible Exception:

```text
FileNotFoundException
```

---

Method:

```java
public void loadData()
throws FileNotFoundException {

}
```

Meaning:

```text
Caller Must Handle It
```

---

Responsibility Transfer:

```text
Method

↓

Caller

↓

Caller's Caller

↓

Eventually Handled
```

---

# 10. Exception Propagation

One of the most important Java concepts.

Example:

```java
public static void methodC(){

    int result = 10 / 0;
}
```

---

Called By:

```java
public static void methodB(){

    methodC();
}
```

---

Called By:

```java
public static void methodA(){

    methodB();
}
```

---

Called By:

```java
public static void main(String[] args){

    methodA();
}
```

---

Flow:

```text
methodC

↓

Exception

↓

methodB

↓

methodA

↓

main

↓

JVM
```

This is called:

```text
Exception Propagation
```

---

# 11. Call Stack & Propagation Flow

Visual Representation:

```text
main()

↓

login()

↓

validateUser()

↓

databaseCall()

↓

SQLException
```

---

If not handled:

```text
databaseCall

↓

validateUser

↓

login

↓

main

↓

Application Crash
```

---

Benefits:

```text
Centralized Error Handling

Cleaner Code

Reduced Duplication
```

---

# 12. throw vs throws

One of the most asked interview questions.

| throw                | throws                      |
| -------------------- | --------------------------- |
| Keyword              | Keyword                     |
| Used Inside Method   | Used In Method Signature    |
| Creates Exception    | Declares Exception          |
| One Exception Object | Multiple Exceptions Allowed |
| Runtime Action       | Compile-Time Declaration    |

---

Example:

```java
throw new IOException();
```

---

Example:

```java
public void test()
throws IOException {

}
```

---

Interview Tip:

```text
throw = Action

throws = Declaration
```

---

# 13. Real Project Examples

## Banking Application

```java
if(balance < amount){

    throw new RuntimeException(
       "Insufficient Balance"
    );
}
```

---

## Employee Management

```java
if(employee == null){

    throw new IllegalArgumentException(
       "Employee Not Found"
    );
}
```

---

## Inventory System

```java
if(stock == 0){

    throw new RuntimeException(
       "Out Of Stock"
    );
}
```

---

# 14. Selenium Framework Examples

Example:

```java
WebElement element =
    driver.findElement(
       By.id("login")
    );
```

Internally Selenium may throw:

```text
NoSuchElementException
```

---

Custom Framework Example:

```java
if(element == null){

    throw new RuntimeException(
       "Element Missing"
    );
}
```

---

Framework Flow:

```text
Element Missing

↓

Throw Exception

↓

Capture Screenshot

↓

Fail Test
```

---

# 15. REST Assured Examples

Example:

```java
if(response.statusCode() != 200){

    throw new RuntimeException(
        "Invalid Response"
    );
}
```

---

API Validation Frameworks frequently use:

```text
throw

IllegalStateException

AssertionError

RuntimeException
```

---

# 16. Enterprise Design Patterns

Modern applications rarely handle exceptions immediately.

Pattern:

```text
DAO Layer

↓

Service Layer

↓

Controller Layer

↓

Global Handler
```

---

DAO:

```java
throws SQLException
```

---

Service:

```java
throws BusinessException
```

---

Controller:

```java
handles exception
```

---

Benefits:

```text
Separation Of Concerns

Cleaner Architecture

Centralized Logging
```

---

# 17. Common Mistakes

## Mistake 1

Using throws Instead Of throw

Wrong:

```java
throws new RuntimeException();
```

Invalid.

---

Correct:

```java
throw new RuntimeException();
```

---

## Mistake 2

Throwing Generic Exception

Bad:

```java
throw new Exception();
```

---

Better:

```java
throw new IllegalArgumentException();
```

---

## Mistake 3

Using Exceptions For Normal Flow

Bad:

```java
try {

}
catch(Exception e){

}
```

for regular logic.

---

Reason:

```text
Exceptions Are Expensive
```

---

# 18. Interview Questions

## Q1 What Is throw?

Answer:

```text
Used To Explicitly Throw Exception Object.
```

---

## Q2 What Is throws?

Answer:

```text
Used To Declare Exceptions.
```

---

## Q3 Difference Between throw And throws?

Answer:

```text
throw -> Action

throws -> Declaration
```

---

## Q4 Can We Throw Checked Exception?

Answer:

```text
Yes
```

Example:

```java
throw new IOException();
```

---

## Q5 Can We Throw Multiple Exceptions Using throw?

Answer:

```text
No
```

Only one object at a time.

---

## Q6 Can Method Declare Multiple Exceptions?

Answer:

```java
public void test()
throws IOException,
       SQLException {

}
```

Yes.

---

## Q7 What Is Exception Propagation?

Answer:

```text
Movement Of Exception Through Call Stack Until Handled.
```

---

## Q8 Which Class Can Be Thrown?

Answer:

```text
Any Child Of Throwable.
```

---

# 19. Revision Notes

```text
throw
↓
Create Exception

throws
↓
Declare Exception

Exception
↓
Propagates Upward

Call Stack
↓
Method Chain

Throwable
↓
Root Type
```

---

Propagation Flow:

```text
Method C

↓

Method B

↓

Method A

↓

Main

↓

JVM
```

---

# 20. Final Cheat Sheet

```text
throw
↓
Action

throws
↓
Declaration

throw
↓
Inside Method

throws
↓
Method Signature

throw
↓
One Exception

throws
↓
Multiple Exceptions

Propagation
↓
Moves Up Call Stack

Throwable
↓
Parent Of All Exceptions
```

---

# Key Takeaway

A professional Java developer must understand that:

```text
throw
=
Create Exception

throws
=
Declare Exception

Propagation
=
Move Exception Through Call Stack
```

These concepts form the foundation for:

* Custom Exceptions
* Enterprise Framework Design
* Global Exception Handling
* Spring Boot Exception Architecture
* Selenium Framework Error Handling
* REST API Error Management

Understanding these topics is essential before moving to custom exception creation and advanced enterprise exception design.

---

# End of Part 5

## Next File

```text
Java-Exception-Handling-Guide-Part-6.md

Topics:

✓ Custom Exceptions

✓ User Defined Exceptions

✓ Checked Custom Exceptions

✓ Unchecked Custom Exceptions

✓ Business Exceptions

✓ Exception Design Best Practices

✓ Banking Project Examples

✓ Selenium Framework Examples

✓ Enterprise Architecture

✓ Interview Questions
```
