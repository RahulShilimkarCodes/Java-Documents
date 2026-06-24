# Java Exception Handling Master Guide

# Part 8 - Checked Exceptions, Unchecked Exceptions & Enterprise Exception Strategies

---

# Table of Contents

1. Introduction
2. What Are Checked Exceptions?
3. Why Checked Exceptions Exist
4. Common Checked Exceptions
5. Checked Exception Flow
6. What Are Unchecked Exceptions?
7. Why Runtime Exceptions Exist
8. Common Runtime Exceptions
9. Checked vs Unchecked Exceptions
10. Compile-Time vs Runtime Validation
11. Exception Translation Pattern
12. Global Exception Handling Strategy
13. Enterprise Framework Design
14. Spring Boot Exception Architecture
15. Selenium Framework Exception Design
16. REST Assured Framework Exception Design
17. Exception Handling Best Practices
18. Common Mistakes
19. Interview Questions
20. Revision Notes
21. Final Cheat Sheet

---

# 1. Introduction

Java exceptions are broadly divided into two categories:

```text
Checked Exceptions

Unchecked Exceptions
```

Understanding the difference is critical because it affects:

* Application Design
* Framework Architecture
* API Design
* Error Handling Strategy
* Interview Performance

Most enterprise applications follow different handling approaches for checked and unchecked exceptions.

---

# 2. What Are Checked Exceptions?

Checked Exceptions are exceptions that the compiler forces developers to handle.

Example:

```java
FileInputStream fis =
    new FileInputStream("data.txt");
```

Compiler Error:

```text
Unhandled Exception:
FileNotFoundException
```

Java forces you to either:

```java
try {

}
catch(FileNotFoundException e){

}
```

or

```java
throws FileNotFoundException
```

---

Definition:

> Checked exceptions are validated during compilation.

---

# 3. Why Checked Exceptions Exist

Java designers introduced checked exceptions because some failures are outside developer control.

Examples:

```text
File Missing

Database Down

Network Failure

Server Unreachable

Printer Offline
```

These are external failures.

The compiler forces developers to think about recovery.

---

Example:

```java
public void loadFile()
throws IOException {

}
```

Meaning:

```text
This Operation May Fail

Caller Must Decide
How To Handle It
```

---

# 4. Common Checked Exceptions

Frequently Used Checked Exceptions:

```text
IOException

SQLException

FileNotFoundException

ClassNotFoundException

InterruptedException

ParseException

MalformedURLException
```

---

Example:

```java
try {

    Thread.sleep(5000);

}
catch(InterruptedException e){

}
```

---

Interview Question:

### Why Is InterruptedException Checked?

Answer:

```text
Thread Interruption
Is Recoverable
```

---

# 5. Checked Exception Flow

Example:

```java
public void methodA()
throws IOException {

    methodB();
}
```

```java
public void methodB()
throws IOException {

}
```

Flow:

```text
methodB

↓

IOException

↓

methodA

↓

Caller

↓

Handle Exception
```

---

Compiler ensures exception handling exists somewhere.

---

# 6. What Are Unchecked Exceptions?

Unchecked Exceptions are exceptions that are NOT validated by the compiler.

Example:

```java
String name = null;

name.length();
```

Compiles successfully.

Fails during execution:

```text
NullPointerException
```

---

Definition:

> Unchecked exceptions occur at runtime and are not enforced by the compiler.

---

# 7. Why Runtime Exceptions Exist

Runtime Exceptions represent:

```text
Programming Mistakes

Invalid Logic

Invalid State

Incorrect Assumptions
```

---

Examples:

```java
String name = null;

name.length();
```

Developer mistake.

---

Example:

```java
int result = 10 / 0;
```

Developer mistake.

---

Compiler cannot always predict these situations.

---

# 8. Common Runtime Exceptions

Frequently Used Runtime Exceptions:

```text
NullPointerException

ArithmeticException

IllegalArgumentException

NumberFormatException

IndexOutOfBoundsException

ArrayIndexOutOfBoundsException

IllegalStateException

ClassCastException
```

---

Example:

```java
Integer.parseInt("ABC");
```

Produces:

```text
NumberFormatException
```

---

# 9. Checked vs Unchecked Exceptions

| Checked Exception   | Unchecked Exception      |
| ------------------- | ------------------------ |
| Compiler Validated  | Runtime Only             |
| Must Handle         | Optional Handling        |
| Recoverable Failure | Programming Error        |
| Extends Exception   | Extends RuntimeException |
| External Failure    | Internal Failure         |

---

Examples:

Checked:

```java
IOException
SQLException
```

Unchecked:

```java
NullPointerException
ArithmeticException
```

---

Interview Rule:

```text
Recoverable

↓

Checked
```

```text
Programming Error

↓

Runtime Exception
```

---

# 10. Compile-Time vs Runtime Validation

Compile-Time Validation:

```java
FileInputStream fis =
new FileInputStream("data.txt");
```

Compiler forces handling.

---

Runtime Validation:

```java
String name = null;

name.length();
```

Compiler allows execution.

Failure occurs later.

---

Comparison:

```text
Checked

↓

Compiler Protection
```

```text
Unchecked

↓

Runtime Detection
```

---

# 11. Exception Translation Pattern

Very Important Enterprise Concept.

DAO Layer:

```java
throw new SQLException(
   "Database Error"
);
```

---

Service Layer:

```java
catch(SQLException e){

    throw new EmployeeServiceException(
       "Unable To Load Employee",
       e
    );
}
```

---

Called:

```text
Exception Translation
```

---

Benefits:

```text
Hide Technical Details

Add Business Meaning

Improve Maintainability
```

---

# 12. Global Exception Handling Strategy

Enterprise applications avoid:

```java
try {
}
catch(Exception e){
}
```

everywhere.

---

Instead:

```text
Controller

↓

Service

↓

Repository

↓

Global Exception Handler
```

---

Benefits:

```text
Centralized Handling

Consistent Responses

Cleaner Code
```

---

# 13. Enterprise Framework Design

Typical Architecture:

```text
Controller

↓

Service

↓

DAO

↓

Database
```

---

DAO:

```java
throws SQLException
```

---

Service:

```java
throw new BusinessException()
```

---

Controller:

```java
Global Handler
```

---

Benefits:

```text
Layer Separation

Reusable Logic

Consistent Error Handling
```

---

# 14. Spring Boot Exception Architecture

Spring Boot commonly uses:

```java
@RestControllerAdvice
```

---

Example:

```java
@RestControllerAdvice
public class GlobalHandler {

    @ExceptionHandler(
        Exception.class
    )
    public ResponseEntity<?> handle(
        Exception ex
    ){

        return ResponseEntity
            .badRequest()
            .body(ex.getMessage());
    }
}
```

---

Flow:

```text
Controller

↓

Exception

↓

Global Handler

↓

Response
```

---

Benefits:

```text
No Duplicate Catch Blocks

Centralized Logging

Consistent API Response
```

---

# 15. Selenium Framework Exception Design

Bad Practice:

```java
catch(Exception e){
}
```

---

Better:

```java
catch(NoSuchElementException e){
}
```

---

Framework Strategy:

```text
Exception

↓

Screenshot

↓

Logging

↓

Report

↓

Fail Test
```

---

Custom Framework Example:

```java
throw new ElementNotFoundException(
   "Login Button Missing"
);
```

---

# 16. REST Assured Framework Exception Design

Example:

```java
if(response.statusCode() != 200){

    throw new ApiValidationException(
       "Invalid Status Code"
    );
}
```

---

Framework Flow:

```text
API Call

↓

Validation Failure

↓

Custom Exception

↓

Reporting Layer

↓

Test Failure
```

---

Benefits:

```text
Readable Tests

Reusable Validation

Centralized Reporting
```

---

# 17. Exception Handling Best Practices

## Use Specific Exceptions

Bad:

```java
catch(Exception e)
```

Good:

```java
catch(IOException e)
```

---

## Preserve Root Cause

Bad:

```java
throw new ServiceException(
   "Failed"
);
```

Good:

```java
throw new ServiceException(
   "Failed",
   e
);
```

---

## Use Custom Exceptions

Bad:

```java
throw new Exception();
```

Good:

```java
throw new PaymentFailedException();
```

---

## Log Meaningful Details

Include:

```text
Timestamp

Request ID

User ID

Stack Trace
```

---

# 18. Common Mistakes

## Mistake 1

Catching Generic Exception Everywhere

---

## Mistake 2

Ignoring Stack Trace

---

## Mistake 3

Swallowing Exceptions

Bad:

```java
catch(Exception e){

}
```

---

## Mistake 4

Using RuntimeException For Everything

---

## Mistake 5

Not Preserving Root Cause

---

# 19. Interview Questions

## Q1 What Is A Checked Exception?

Answer:

```text
Compiler Forces Handling
```

---

## Q2 What Is An Unchecked Exception?

Answer:

```text
Runtime Exception
Not Compiler Enforced
```

---

## Q3 Which Is Better?

Answer:

```text
Depends On Use Case
```

---

## Q4 Why Does Java Have Checked Exceptions?

Answer:

```text
To Force Developers
To Handle Recoverable Failures
```

---

## Q5 What Is Exception Translation?

Answer:

```text
Converting Technical Exceptions
Into Business Exceptions
```

---

## Q6 What Is Global Exception Handling?

Answer:

```text
Centralized Error Handling
Across Entire Application
```

---

## Q7 Should We Catch Exception Everywhere?

Answer:

```text
No
```

---

## Q8 Why Preserve Root Cause?

Answer:

```text
Better Debugging
```

---

# 20. Revision Notes

```text
Checked Exception

↓

Compiler Validation

↓

Recoverable Failure
```

---

```text
Unchecked Exception

↓

Runtime Validation

↓

Programming Error
```

---

```text
SQLException

↓

ServiceException

↓

Global Handler
```

---

# 21. Final Cheat Sheet

```text
Checked Exception
↓
Compiler Enforced

Unchecked Exception
↓
Runtime Only

Checked
↓
Recoverable

Unchecked
↓
Programming Mistake

Exception Translation
↓
Technical → Business

Global Handler
↓
Centralized Handling

Spring Boot
↓
@RestControllerAdvice

Best Practice
↓
Specific Exceptions

Avoid
↓
catch(Exception)
```

---

# Key Takeaway

A senior Java developer should understand not only how exceptions work, but also how exceptions are designed across large enterprise systems.

Master these concepts:

* Checked Exceptions
* Runtime Exceptions
* Exception Translation
* Global Exception Handling
* Spring Boot Architecture
* Selenium Framework Design
* REST Assured Framework Design

These topics are among the most frequently asked exception-handling concepts in product-company and banking interviews.

---

# End of Part 8

## Next File

```text
Java-Exception-Handling-Guide-Part-9.md

Topics:

✓ Advanced Exception Handling

✓ Multi-Catch Internals

✓ Rethrowing Exceptions

✓ Exception Wrapping

✓ Suppressed Exceptions Deep Dive

✓ Stack Unwinding

✓ JVM Internals

✓ Enterprise Logging Strategies

✓ Framework-Level Exception Design

✓ Advanced Interview Questions
```
