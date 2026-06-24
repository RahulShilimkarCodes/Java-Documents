````md
# Java-Exception-Handling-Guide-Part-16A.md

# Java Exception Handling Master Guide
# Part 16A – Core Java Exception Handling Interview Questions (1–25)

---

# Introduction

This section contains the first 25 interview questions on Java Exception Handling.

The answers are intentionally detailed because interviewers in product companies, banking organizations, and SDET roles often ask follow-up questions after a basic answer.

The goal is not to memorize definitions but to understand:

- Why exceptions exist
- How JVM handles exceptions
- How exception handling affects application design
- Best practices followed in enterprise projects

---

# Q1. What is an Exception in Java?

## Answer

An Exception is an abnormal event that occurs during the execution of a program and disrupts the normal flow of instructions.

When an exception occurs, Java creates an Exception Object and transfers control to an exception handler.

Example:

```java
int result = 10 / 0;
```

Output:

```text
java.lang.ArithmeticException: / by zero
```

Without exception handling, the application terminates immediately.

### Why Exceptions Are Important

Exceptions help applications:

- Detect runtime problems
- Avoid unexpected crashes
- Recover from failures
- Provide meaningful error information

### Interview Tip

An exception is not a bug itself. It is Java's mechanism for reporting runtime problems.

---

# Q2. What is Throwable?

## Answer

Throwable is the root class of Java's exception hierarchy.

Every Exception and Error ultimately inherits from Throwable.

Hierarchy:

```text
Throwable
├── Exception
└── Error
```

Important methods available in Throwable:

```java
getMessage()
printStackTrace()
getCause()
```

Example:

```java
try {
    int result = 10 / 0;
}
catch(Exception e) {

    System.out.println(
        e.getMessage()
    );

    e.printStackTrace();
}
```

### Interview Tip

Whenever an interviewer asks:

> What is the top-most class in Java Exception Handling?

Answer:

```text
Throwable
```

---

# Q3. What is the difference between Exception and Error?

## Answer

Both inherit from Throwable but represent different categories of problems.

### Exception

Represents conditions that applications can potentially recover from.

Examples:

```java
IOException
SQLException
FileNotFoundException
```

### Error

Represents serious JVM-level problems.

Examples:

```java
OutOfMemoryError
StackOverflowError
VirtualMachineError
```

### Comparison

| Exception | Error |
|------------|------------|
| Recoverable | Usually Non-Recoverable |
| Application Problem | JVM/System Problem |
| Can Be Handled | Generally Not Handled |
| Example: IOException | Example: OutOfMemoryError |

### Interview Tip

Do not say Errors can never be caught.

Technically they can be caught.

However, catching them is usually a bad design choice.

---

# Q4. What are Checked Exceptions?

## Answer

Checked Exceptions are exceptions verified by the compiler during compilation.

The compiler forces developers to either:

- Handle them using try-catch
- Declare them using throws

Example:

```java
FileReader file =
new FileReader("data.txt");
```

Compiler Error:

```text
Unhandled exception type FileNotFoundException
```

Correct:

```java
try {

    FileReader file =
    new FileReader("data.txt");

}
catch(FileNotFoundException e){

}
```

### Common Checked Exceptions

```java
IOException
SQLException
ClassNotFoundException
FileNotFoundException
```

### Interview Tip

Checked exceptions extend:

```java
Exception
```

but do not extend:

```java
RuntimeException
```

---

# Q5. What are Unchecked Exceptions?

## Answer

Unchecked Exceptions occur during runtime.

The compiler does not force developers to handle them.

Most unchecked exceptions indicate programming mistakes.

Examples:

```java
NullPointerException
ArithmeticException
ArrayIndexOutOfBoundsException
NumberFormatException
```

Example:

```java
String name = null;

System.out.println(
name.length()
);
```

Output:

```text
NullPointerException
```

### Interview Tip

Unchecked exceptions inherit from:

```java
RuntimeException
```

---

# Q6. Difference Between Checked and Unchecked Exceptions?

## Answer

| Feature | Checked | Unchecked |
|----------|----------|----------|
| Checked by Compiler | Yes | No |
| Handling Mandatory | Yes | No |
| Parent Class | Exception | RuntimeException |
| Detected | Compile Time | Runtime |
| Example | IOException | NullPointerException |

### Interview Tip

Most Selenium exceptions are unchecked exceptions.

---

# Q7. What is try-catch?

## Answer

The try-catch block allows developers to handle exceptions and continue program execution.

Syntax:

```java
try {

}
catch(Exception e){

}
```

Example:

```java
try {

    int result = 10 / 0;

}
catch(ArithmeticException e){

    System.out.println(
    "Cannot divide by zero"
    );

}
```

Output:

```text
Cannot divide by zero
```

### Benefits

- Prevents application crashes
- Improves user experience
- Allows graceful recovery

---

# Q8. What is a finally block?

## Answer

The finally block contains code that executes whether an exception occurs or not.

Common Uses:

- Closing files
- Closing database connections
- Releasing resources
- Cleaning temporary data

Example:

```java
try {

    int result = 10 / 0;

}
catch(Exception e){

}
finally{

    System.out.println(
    "Cleanup Executed"
    );

}
```

### Output

```text
Cleanup Executed
```

---

# Q9. Can finally block fail to execute?

## Answer

Under normal conditions, finally always executes.

Exceptions:

### JVM Shutdown

```java
System.exit(0);
```

### JVM Crash

Examples:

```text
Power Failure

OS Crash

JVM Crash
```

### Interview Tip

The correct answer is:

```text
Normally Yes

But JVM termination can prevent execution
```

---

# Q10. Difference Between throw and throws?

## Answer

### throw

Used to explicitly throw an exception object.

Example:

```java
throw new IllegalArgumentException(
"Invalid Age"
);
```

### throws

Used to declare exceptions in a method signature.

Example:

```java
public void readFile()
throws IOException {

}
```

### Comparison

| throw | throws |
|---------|---------|
| Throws Exception | Declares Exception |
| Inside Method | Method Signature |
| Single Object | Multiple Exceptions |

---

# Q11. What is Exception Propagation?

## Answer

Exception propagation means an exception moves from the called method to the caller method until it is handled.

Example:

```java
public void methodA(){

    methodB();

}

public void methodB(){

    int result = 10 / 0;

}
```

Flow:

```text
methodB()

↓

methodA()

↓

Main Method

↓

JVM
```

### Interview Tip

Propagation happens automatically if no catch block is found.

---

# Q12. What is Stack Unwinding?

## Answer

When an exception occurs, JVM starts moving backward through method calls searching for a matching catch block.

Example:

```java
A()

↓

B()

↓

C()

↓

Exception
```

JVM searches:

```text
C

↓

B

↓

A

↓

Main
```

This process is called Stack Unwinding.

---

# Q13. What is Exception Handling?

## Answer

Exception Handling is the mechanism used to detect, process, and recover from runtime failures.

Benefits:

- Stability
- Reliability
- Better user experience
- Easier debugging

---

# Q14. What is a Custom Exception?

## Answer

A user-defined exception created for business-specific failures.

Example:

```java
public class PaymentFailedException
extends Exception {

    public PaymentFailedException(
    String message){

        super(message);

    }

}
```

Usage:

```java
throw new PaymentFailedException(
"Payment Declined"
);
```

---

# Q15. Why create Custom Exceptions?

## Answer

Custom exceptions provide business meaning.

Bad:

```java
throw new Exception(
"Error"
);
```

Good:

```java
throw new PaymentFailedException(
"Payment Declined"
);
```

Benefits:

- Better readability
- Better debugging
- Domain-specific error handling

---

# Q16. What is NullPointerException?

## Answer

Occurs when a null reference is accessed.

Example:

```java
String name = null;

name.length();
```

Output:

```text
NullPointerException
```

### Prevention

```java
if(name != null){

}
```

or

```java
Optional<String>
```

---

# Q17. What is ArithmeticException?

## Answer

Occurs during illegal arithmetic operations.

Example:

```java
int result = 10 / 0;
```

Output:

```text
ArithmeticException
```

---

# Q18. What is NumberFormatException?

## Answer

Occurs when converting invalid text to a numeric value.

Example:

```java
Integer.parseInt(
"ABC"
);
```

Output:

```text
NumberFormatException
```

---

# Q19. What is IllegalArgumentException?

## Answer

Occurs when a method receives an inappropriate argument.

Example:

```java
Thread.sleep(-100);
```

Output:

```text
IllegalArgumentException
```

---

# Q20. What is ArrayIndexOutOfBoundsException?

## Answer

Occurs when accessing an invalid array index.

Example:

```java
int[] arr = {1,2,3};

System.out.println(
arr[5]
);
```

Output:

```text
ArrayIndexOutOfBoundsException
```

---

# Q21. What is ClassCastException?

## Answer

Occurs when an object is cast to an incompatible type.

Example:

```java
Object obj = "Java";

Integer num =
(Integer) obj;
```

Output:

```text
ClassCastException
```

---

# Q22. What is StackOverflowError?

## Answer

Occurs when the call stack exceeds its capacity.

Common Cause:

Infinite recursion.

Example:

```java
public void test(){

    test();

}
```

Output:

```text
StackOverflowError
```

---

# Q23. What is OutOfMemoryError?

## Answer

Occurs when JVM cannot allocate additional memory.

Example:

```java
List<String> list =
new ArrayList<>();

while(true){

    list.add("Java");

}
```

Output:

```text
OutOfMemoryError
```

---

# Q24. Should We Catch Error?

## Answer

Generally No.

Reason:

Errors usually indicate JVM-level problems.

Examples:

```java
OutOfMemoryError
StackOverflowError
```

Fix the root cause instead of catching them.

---

# Q25. What is Try-With-Resources?

## Answer

Introduced in Java 7.

Automatically closes resources.

Example:

```java
try(
FileInputStream fis =
new FileInputStream(
"data.txt"
)
){

}
```

Equivalent Traditional Code:

```java
FileInputStream fis = null;

try{

}
finally{

    if(fis != null){

        fis.close();

    }

}
```

### Benefits

- Cleaner Code
- Automatic Resource Cleanup
- Reduced Memory Leaks
- Fewer Bugs

---

# End of Part 16A

## Next File

```text
Java-Exception-Handling-Guide-Part-16B.md

Questions 26–50

Topics:

- Exception Chaining
- Suppressed Exceptions
- Multi-Catch
- RuntimeException Internals
- JVM Exception Processing
- Defensive Programming
- Production Scenarios
- Best Practices
- Advanced Interview Questions
```
````
