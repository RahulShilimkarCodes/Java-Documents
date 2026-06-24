# Java Exception Handling Master Guide

# Part 6 - Custom Exceptions, Business Exceptions & Enterprise Exception Design

---

# Table of Contents

1. Introduction to Custom Exceptions
2. Why Custom Exceptions Are Needed
3. Problems with Generic Exceptions
4. What is a Custom Exception?
5. Creating a Custom Checked Exception
6. Creating a Custom Unchecked Exception
7. Checked vs Unchecked Custom Exceptions
8. Business Exceptions
9. Exception Design Principles
10. Exception Chaining
11. Enterprise Exception Architecture
12. Banking Application Examples
13. E-Commerce Examples
14. Selenium Framework Examples
15. REST Assured Framework Examples
16. Common Mistakes
17. Interview Questions
18. Revision Notes
19. Final Cheat Sheet

---

# 1. Introduction to Custom Exceptions

Java provides hundreds of built-in exceptions.

Examples:

```text
NullPointerException

IOException

SQLException

ArithmeticException

NumberFormatException
```

However, enterprise applications often encounter business-specific problems that cannot be represented clearly using standard Java exceptions.

Examples:

```text
Insufficient Balance

Invalid Account

Employee Not Found

Order Not Found

Coupon Expired

User Already Exists
```

Using generic exceptions for these situations makes code difficult to understand.

This is where Custom Exceptions become useful.

---

## Definition

> A Custom Exception is a user-defined exception class created to represent specific business or application-level problems.

---

# 2. Why Custom Exceptions Are Needed

Consider:

```java
throw new Exception(
    "Something Went Wrong"
);
```

Problem:

```text
What Went Wrong?

Database Failure?

Validation Failure?

Business Rule Failure?

Network Failure?
```

The exception message is too generic.

---

Better:

```java
throw new InsufficientBalanceException(
    "Balance Too Low"
);
```

Now the problem becomes immediately clear.

---

Benefits:

```text
Readable Code

Better Debugging

Business Clarity

Better Logging

Better Error Handling
```

---

# 3. Problems with Generic Exceptions

Bad Example:

```java
public void withdraw(
    double amount
) throws Exception {

    if(amount > balance){

        throw new Exception(
           "Error"
        );
    }
}
```

---

Problems:

```text
Unclear Meaning

Hard To Debug

Poor Design

Poor API Contract
```

---

Enterprise systems avoid this pattern.

---

Preferred:

```java
throw new InsufficientBalanceException(
    "Insufficient Balance"
);
```

---

# 4. What is a Custom Exception?

A custom exception is simply a class extending:

```text
Exception

OR

RuntimeException
```

---

Hierarchy:

```text
Throwable

↓

Exception

↓

Custom Exception
```

or

```text
Throwable

↓

RuntimeException

↓

Custom Runtime Exception
```

---

Example:

```java
public class EmployeeNotFoundException
extends Exception {

}
```

---

# 5. Creating a Custom Checked Exception

Checked Exception:

```java
public class EmployeeNotFoundException
extends Exception {

    public EmployeeNotFoundException(
        String message
    ){
        super(message);
    }
}
```

---

Usage:

```java
public void findEmployee(
    int id
)
throws EmployeeNotFoundException {

    throw new EmployeeNotFoundException(
       "Employee Not Found"
    );
}
```

---

Compiler Forces Handling.

---

Example:

```java
try {

    findEmployee(100);

}
catch(EmployeeNotFoundException e){

    System.out.println(
        e.getMessage()
    );
}
```

---

# 6. Creating a Custom Unchecked Exception

Runtime Exception:

```java
public class InvalidAgeException
extends RuntimeException {

    public InvalidAgeException(
        String message
    ){
        super(message);
    }
}
```

---

Usage:

```java
if(age < 18){

    throw new InvalidAgeException(
       "Age Must Be 18+"
    );
}
```

---

No compiler enforcement.

---

# 7. Checked vs Unchecked Custom Exceptions

| Checked           | Unchecked                  |
| ----------------- | -------------------------- |
| Extends Exception | Extends RuntimeException   |
| Compiler Enforced | Not Enforced               |
| Recoverable       | Programming/Business Error |
| Must Handle       | Optional Handling          |

---

Checked Example:

```java
EmployeeNotFoundException
```

---

Unchecked Example:

```java
InvalidAgeException
```

---

Interview Rule:

```text
Business Recoverable

↓

Checked Exception
```

```text
Programming Error

↓

Runtime Exception
```

---

# 8. Business Exceptions

Enterprise applications usually create business exceptions.

Examples:

```text
InsufficientBalanceException

OrderNotFoundException

InvalidCouponException

PaymentFailedException

UserAlreadyExistsException
```

---

Banking Example:

```java
if(balance < amount){

    throw new InsufficientBalanceException(
       "Insufficient Funds"
    );
}
```

---

E-Commerce Example:

```java
if(product == null){

    throw new ProductNotFoundException(
       "Product Not Found"
    );
}
```

---

Benefits:

```text
Business Meaning

Easy Troubleshooting

Cleaner APIs
```

---

# 9. Exception Design Principles

Senior developers follow exception design guidelines.

---

## Principle 1

Use Meaningful Names

Bad:

```java
CustomException
```

Good:

```java
PaymentFailedException
```

---

## Principle 2

Add Useful Messages

Bad:

```java
throw new RuntimeException(
   "Error"
);
```

Good:

```java
throw new PaymentFailedException(
   "Card Authorization Failed"
);
```

---

## Principle 3

Keep Exception Hierarchy Organized

Example:

```text
BusinessException

├── PaymentException

├── OrderException

├── UserException
```

---

# 10. Exception Chaining

Important Product Company Topic.

Suppose:

```java
SQLException
```

occurs inside DAO layer.

---

Instead of exposing it:

```java
throw sqlException;
```

---

Wrap it:

```java
throw new EmployeeServiceException(
    "Unable To Load Employee",
    sqlException
);
```

---

Constructor:

```java
public EmployeeServiceException(
    String message,
    Throwable cause
){

    super(message, cause);
}
```

---

Benefits:

```text
Preserve Original Exception

Add Business Context

Better Logging
```

---

# 11. Enterprise Exception Architecture

Large applications rarely throw raw exceptions.

Architecture:

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

DAO Layer:

```java
throw new SQLException();
```

---

Service Layer:

```java
throw new EmployeeServiceException(
    "Employee Fetch Failed",
    ex
);
```

---

Controller Layer:

```java
Global Exception Handler
```

---

Benefits:

```text
Layer Separation

Clean Design

Centralized Handling
```

---

# 12. Banking Application Examples

## Example 1

Insufficient Balance

```java
public class
InsufficientBalanceException
extends Exception {

    public
    InsufficientBalanceException(
        String message
    ){
        super(message);
    }
}
```

---

Usage:

```java
if(balance < withdrawal){

    throw new
    InsufficientBalanceException(
       "Balance Too Low"
    );
}
```

---

## Example 2

Invalid Account

```java
throw new InvalidAccountException(
   "Account Does Not Exist"
);
```

---

# 13. E-Commerce Examples

Example:

```java
throw new ProductNotFoundException(
   "Product Missing"
);
```

---

Example:

```java
throw new CouponExpiredException(
   "Coupon Expired"
);
```

---

Typical Exception Hierarchy:

```text
EcommerceException

├── ProductException

├── PaymentException

├── CouponException

├── ShippingException
```

---

# 14. Selenium Framework Examples

Custom Selenium Framework Exception:

```java
public class ElementNotFoundException
extends RuntimeException {

    public ElementNotFoundException(
        String message
    ){
        super(message);
    }
}
```

---

Usage:

```java
if(element == null){

    throw new ElementNotFoundException(
       "Login Button Missing"
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

Log Failure

↓

Fail Test
```

---

# 15. REST Assured Framework Examples

Custom API Exception:

```java
public class ApiValidationException
extends RuntimeException {

    public ApiValidationException(
        String message
    ){
        super(message);
    }
}
```

---

Usage:

```java
if(response.statusCode() != 200){

    throw new ApiValidationException(
       "Unexpected Status Code"
    );
}
```

---

Benefits:

```text
Reusable Validation

Centralized Reporting

Cleaner Test Code
```

---

# 16. Common Mistakes

## Mistake 1

Creating Too Many Exceptions

Bad:

```text
NameMissingException

NameBlankException

NameEmptyException
```

---

Over-Engineering.

---

## Mistake 2

Using Generic Names

Bad:

```java
CustomException
```

---

Good:

```java
PaymentFailedException
```

---

## Mistake 3

Ignoring Root Cause

Bad:

```java
throw new ServiceException(
   "Error"
);
```

---

Better:

```java
throw new ServiceException(
   "Error",
   ex
);
```

---

# 17. Interview Questions

## Q1 What Is Custom Exception?

Answer:

```text
User-defined exception created to represent application-specific failures.
```

---

## Q2 How To Create Custom Exception?

Answer:

```text
Extend Exception

OR

Extend RuntimeException
```

---

## Q3 Difference Between Checked And Unchecked Custom Exception?

Answer:

```text
Checked → Compiler Enforced

Unchecked → Runtime Only
```

---

## Q4 What Is Exception Chaining?

Answer:

```text
Wrapping one exception inside another exception.
```

---

## Q5 Why Use Custom Exceptions?

Answer:

```text
Better Readability

Business Clarity

Better Error Handling
```

---

## Q6 Which Is Better?

```java
throw new Exception();
```

or

```java
throw new PaymentFailedException();
```

Answer:

```text
PaymentFailedException
```

because it clearly describes the problem.

---

# 18. Revision Notes

```text
Custom Exception

↓

User Defined

↓

Extends Exception

OR

RuntimeException

↓

Business Meaning

↓

Better Design
```

---

Exception Chaining:

```text
SQLException

↓

ServiceException

↓

Controller
```

---

Enterprise Flow:

```text
DAO

↓

Service

↓

Controller

↓

Global Handler
```

---

# 19. Final Cheat Sheet

```text
Custom Exception
↓
User Defined

Checked
↓
Exception

Unchecked
↓
RuntimeException

Business Exception
↓
Domain Specific

Exception Chaining
↓
Preserve Root Cause

Enterprise Design
↓
Layered Handling

Best Practice
↓
Meaningful Names
```

---

# Key Takeaway

Custom Exceptions are one of the most important concepts in enterprise Java development.

A senior Java developer should:

* Create meaningful exception classes
* Design business-specific exceptions
* Use exception chaining correctly
* Preserve root causes
* Build layered exception architectures
* Integrate exceptions with Selenium and API frameworks

These concepts are heavily used in Spring Boot, Microservices, Banking Applications, E-Commerce Platforms, and Automation Frameworks.

---

# End of Part 6

## Next File

```text
Java-Exception-Handling-Guide-Part-7.md

Topics:

✓ Exception Hierarchy Deep Dive

✓ Throwable Class

✓ Error Class

✓ RuntimeException Internals

✓ Checked Exception Internals

✓ JVM Exception Creation

✓ Stack Trace Internals

✓ Memory Impact Of Exceptions

✓ Performance Considerations

✓ Product Company Interview Questions
```
