# Java-Exception-Handling-Guide-Part-16A.md

# Java Exception Handling Master Guide

## Part 16A – Core Java Exception Handling Interview Questions (1–25)

---

# Q1. What is an Exception in Java?

## Answer

An Exception is an abnormal event that occurs during program execution and disrupts the normal flow of a program.

Example:

```java
int result = 10 / 0;
```

Output:

```text
java.lang.ArithmeticException: / by zero
```

Exceptions help applications:

* Detect runtime problems
* Prevent unexpected crashes
* Improve reliability
* Provide meaningful error information

---

# Q2. What is Throwable?

## Answer

Throwable is the root class of Java's exception hierarchy.

Hierarchy:

```text
Throwable
├── Exception
└── Error
```

Common methods:

```java
getMessage()
printStackTrace()
getCause()
```

All exceptions and errors inherit from Throwable.

---

# Q3. What is the Difference Between Exception and Error?

## Answer

| Exception            | Error                     |
| -------------------- | ------------------------- |
| Recoverable          | Usually Non-Recoverable   |
| Application Issue    | JVM/System Issue          |
| Can Be Handled       | Usually Not Handled       |
| Example: IOException | Example: OutOfMemoryError |

Examples:

```java
IOException
SQLException
```

Errors:

```java
OutOfMemoryError
StackOverflowError
```

---

# Q4. What are Checked Exceptions?

## Answer

Checked Exceptions are verified by the compiler during compilation.

The compiler forces developers to:

* Handle the exception
* Declare it using throws

Example:

```java
FileReader file =
new FileReader("data.txt");
```

Compiler Error:

```text
Unhandled exception type FileNotFoundException
```

Examples:

```java
IOException
SQLException
FileNotFoundException
ClassNotFoundException
```

---

# Q5. What are Unchecked Exceptions?

## Answer

Unchecked Exceptions occur during runtime.

Compiler does not force handling.

Examples:

```java
NullPointerException
ArithmeticException
NumberFormatException
ArrayIndexOutOfBoundsException
```

Example:

```java
String name = null;
name.length();
```

Output:

```text
NullPointerException
```

---

# Q6. Difference Between Checked and Unchecked Exceptions?

## Answer

| Feature             | Checked      | Unchecked        |
| ------------------- | ------------ | ---------------- |
| Checked by Compiler | Yes          | No               |
| Mandatory Handling  | Yes          | No               |
| Parent              | Exception    | RuntimeException |
| Detection           | Compile Time | Runtime          |

Examples:

Checked:

```java
IOException
```

Unchecked:

```java
NullPointerException
```

---

# Q7. What is try-catch?

## Answer

Used to handle exceptions gracefully.

Example:

```java
try {
    int result = 10 / 0;
}
catch(ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

Output:

```text
Cannot divide by zero
```

Benefits:

* Prevents crashes
* Improves stability
* Allows recovery

---

# Q8. What is finally Block?

## Answer

finally executes whether exception occurs or not.

Example:

```java
try {
    int result = 10 / 0;
}
catch(Exception e) {
}
finally {
    System.out.println("Cleanup");
}
```

Output:

```text
Cleanup
```

Used for:

* Closing files
* Closing DB connections
* Resource cleanup

---

# Q9. Can finally Block Fail to Execute?

## Answer

Normally finally always executes.

Exceptions:

```java
System.exit(0);
```

or

```text
JVM Crash
Power Failure
OutOfMemoryError
```

---

# Q10. Difference Between throw and throws?

## Answer

### throw

Used to throw an exception.

```java
throw new IllegalArgumentException(
"Invalid Age"
);
```

### throws

Used in method declaration.

```java
public void readFile()
throws IOException {
}
```

| throw            | throws             |
| ---------------- | ------------------ |
| Throws Exception | Declares Exception |
| Inside Method    | Method Signature   |

---

# Q11. What is Exception Propagation?

## Answer

When an exception moves from called method to caller method until handled.

Example:

```java
methodA()
→ methodB()
→ Exception
```

Flow:

```text
methodB
↓
methodA
↓
main
↓
JVM
```

---

# Q12. What is Stack Unwinding?

## Answer

When JVM searches backward through method calls looking for a matching catch block.

Example:

```text
A()
↓
B()
↓
C()
↓
Exception
```

JVM checks:

```text
C
↓
B
↓
A
↓
main
```

---

# Q13. What is Exception Handling?

## Answer

Exception Handling is the process of detecting and managing runtime failures.

Benefits:

* Reliability
* Stability
* Better User Experience
* Easier Debugging

---

# Q14. What is a Custom Exception?

## Answer

User-defined exception created for business-specific failures.

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
"Payment Failed"
);
```

---

# Q15. Why Create Custom Exceptions?

## Answer

Custom exceptions improve readability.

Bad:

```java
throw new Exception("Error");
```

Good:

```java
throw new PaymentFailedException(
"Payment Failed"
);
```

Benefits:

* Business Meaning
* Better Debugging
* Cleaner Architecture

---

# Q16. What is NullPointerException?

## Answer

Occurs when null reference is accessed.

Example:

```java
String name = null;
name.length();
```

Output:

```text
NullPointerException
```

Prevention:

```java
if(name != null) {
}
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

Occurs when invalid text is converted to number.

Example:

```java
Integer.parseInt("ABC");
```

Output:

```text
NumberFormatException
```

---

# Q19. What is IllegalArgumentException?

## Answer

Occurs when invalid arguments are passed to methods.

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

Occurs when accessing invalid array index.

Example:

```java
int[] arr = {1,2,3};

System.out.println(arr[5]);
```

Output:

```text
ArrayIndexOutOfBoundsException
```

---

# Q21. What is ClassCastException?

## Answer

Occurs when incompatible casting is attempted.

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

Occurs when call stack exceeds JVM limit.

Most common cause:

```text
Infinite Recursion
```

Example:

```java
public void test() {
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

while(true) {
    list.add("Java");
}
```

Output:

```text
OutOfMemoryError
```

Common Causes:

* Memory Leaks
* Huge Collections
* Insufficient Heap Size

---

# Q24. Should We Catch Errors?

## Answer

Generally No.

Examples:

```java
OutOfMemoryError
StackOverflowError
```

Reason:

Errors usually indicate JVM-level problems.

Fix root cause instead of catching them.

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

Traditional Approach:

```java
FileInputStream fis = null;

try {

}
finally {

    if(fis != null) {
        fis.close();
    }
}
```

Benefits:

* Cleaner Code
* Automatic Cleanup
* Reduced Memory Leaks
* Better Resource Management

---

# Part 16A Revision Sheet

```text
Exception
↓
Runtime Problem

Throwable
↓
Root Class

Checked Exception
↓
Compile Time

Unchecked Exception
↓
Runtime

try-catch
↓
Handle Exception

finally
↓
Cleanup

throw
↓
Throw Exception

throws
↓
Declare Exception

Custom Exception
↓
Business Meaning

Stack Unwinding
↓
Search Catch Block

Try-With-Resources
↓
Automatic Resource Cleanup
```

---

# End of Part 16A
