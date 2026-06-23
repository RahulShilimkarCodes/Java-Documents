# Java Methods Master Guide

# Part 1 - Method Fundamentals & JVM Execution

---

# Table of Contents

1. Introduction to Methods
2. Why Methods Are Important
3. Real World Analogy
4. Method Definition
5. Method Syntax
6. Components of a Method
7. How Method Calls Work
8. JVM Execution Flow
9. Stack Memory and Methods
10. Method Lifecycle
11. Types of Methods
12. Benefits of Methods
13. Real Project Examples
14. Common Beginner Mistakes
15. Interview Questions
16. Quick Revision Notes
17. Final Cheat Sheet

---

# 1. Introduction to Methods

Methods are one of the most important building blocks in Java.

Every Java application is primarily composed of:

* Classes
* Objects
* Methods

A method contains a set of instructions that perform a specific task.

Example:

```java
System.out.println("Login");

System.out.println("Search");

System.out.println("Checkout");
```

Without methods, the same logic may need to be repeated many times.

Methods help organize and reuse code.

---

# 2. Why Methods Are Important

Methods solve several software development problems.

Without Methods:

```java
System.out.println("Welcome");

System.out.println("Welcome");

System.out.println("Welcome");

System.out.println("Welcome");
```

With Methods:

```java
public static void displayWelcome(){

    System.out.println("Welcome");
}

displayWelcome();

displayWelcome();

displayWelcome();
```

Advantages:

```text
Code Reusability

Improved Readability

Easy Maintenance

Reduced Duplication

Better Design
```

---

# 3. Real World Analogy

Think of a TV Remote.

When you press:

```text
Power Button
```

a predefined task executes.

Similarly:

```java
login();
```

executes a predefined block of code.

Method = Action Button

---

# 4. Method Definition

Definition:

```text
A method is a reusable block of code
that performs a specific task and can be
executed whenever required.
```

Example:

```java
public static void greet(){

    System.out.println("Hello");
}
```

---

# 5. Method Syntax

General Syntax:

```java
accessModifier returnType methodName(){

}
```

Example:

```java
public static void login(){

}
```

---

# 6. Components of a Method

Example:

```java
public static int add(int a,int b){

    return a+b;
}
```

Breakdown:

```text
public
→ Access Modifier

static
→ Belongs to Class

int
→ Return Type

add
→ Method Name

(int a,int b)
→ Parameters

return
→ Returned Value
```

---

# 7. How Method Calls Work

Example:

```java
public static void greet(){

    System.out.println("Hello");
}

public static void main(String[] args){

    greet();
}
```

Execution Flow:

```text
main()

↓

greet()

↓

Print Hello

↓

Return to main()
```

Output:

```text
Hello
```

---

# 8. JVM Execution Flow

Consider:

```java
public static void login(){

    search();
}

public static void search(){

    checkout();
}

public static void checkout(){

    System.out.println("Order Placed");
}
```

Execution:

```text
main()

↓

login()

↓

search()

↓

checkout()

↓

Return

↓

Return

↓

Return
```

JVM executes methods using Stack Memory.

---

# 9. Stack Memory and Methods

Most Important Interview Topic.

Example:

```java
public static void test(){

}
```

When method executes:

```text
STACK

+-------+
| test()|
+-------+
```

When execution completes:

```text
STACK

(empty)
```

The JVM creates and removes stack frames automatically.

---

# 10. Method Lifecycle

Step 1

Method Defined

```java
public static void hello(){

}
```

---

Step 2

Method Called

```java
hello();
```

---

Step 3

Stack Frame Created

---

Step 4

Method Executes

---

Step 5

Control Returns

---

Step 6

Stack Frame Removed

---

# 11. Types of Methods

---

## Predefined Methods

Methods already provided by Java.

Examples:

```java
Math.sqrt(25);

String.valueOf(100);

Arrays.sort(arr);
```

---

## User Defined Methods

Methods created by developers.

Example:

```java
public static void login(){

}
```

---

## Static Methods

Can be called without object creation.

Example:

```java
public static void test(){

}
```

Call:

```java
test();
```

---

## Non-Static Methods

Require object creation.

Example:

```java
public void test(){

}
```

Call:

```java
Demo d = new Demo();

d.test();
```

---

# 12. Benefits of Methods

Advantages:

```text
Code Reusability

Modularity

Easy Maintenance

Improved Readability

Reduced Redundancy

Easy Debugging

Better Testing
```

---

# 13. Real Project Examples

---

## Selenium Framework

```java
login();

logout();

searchProduct();

addToCart();

captureScreenshot();
```

---

## API Testing

```java
createUser();

updateUser();

deleteUser();

getUser();
```

---

## Framework Utilities

```java
readProperty();

generateReport();

takeScreenshot();

launchBrowser();
```

---

# 14. Common Beginner Mistakes

---

## Mistake 1

Method Defined But Never Called

```java
public static void hello(){

}
```

Output:

```text
No Output
```

---

## Mistake 2

Wrong Return Type

```java
public static int test(){

}
```

Compilation Error.

Reason:

```text
Missing Return Statement
```

---

## Mistake 3

Calling Non-Static Method From Static Context

Example:

```java
public void test(){

}

public static void main(String[] args){

    test();
}
```

Error:

```text
Cannot Make Static Reference
To Non-Static Method
```

---

## Mistake 4

Infinite Method Calls

```java
public static void test(){

    test();
}
```

Result:

```text
StackOverflowError
```

---

# 15. Interview Questions

---

## Q1 What is a Method?

Answer:

```text
A reusable block of code used
to perform a specific task.
```

---

## Q2 Why Use Methods?

Answer:

```text
To improve reusability,
maintainability,
and readability.
```

---

## Q3 What Happens During a Method Call?

Answer:

```text
JVM creates a stack frame,
executes the method,
returns control,
and removes the frame.
```

---

## Q4 Where Are Methods Stored?

Answer:

```text
Methods belong to classes.

During execution,
their stack frames are stored
inside Stack Memory.
```

---

## Q5 What Memory Is Used During Method Execution?

Answer:

```text
Stack Memory
```

---

## Q6 What Is a Stack Frame?

Answer:

```text
A memory block created
for every method call.
```

---

# 16. Quick Revision Notes

```text
Method = Reusable Code Block

Method Call Creates Stack Frame

Methods Improve Reusability

Methods Improve Readability

Methods Reduce Duplication

Methods Improve Maintainability

Methods Execute Through JVM Stack

Method Completion Removes Frame
```

---

# 17. Final Cheat Sheet

```text
Method

Definition:
Reusable Block Of Code

Purpose:
Perform Specific Task

Benefits:
Reuse
Readability
Maintenance

Execution:

Method Call

↓

Stack Frame Created

↓

Execution

↓

Return

↓

Stack Frame Removed

Memory:
Stack Memory

Examples:
login()

logout()

searchProduct()

captureScreenshot()

generateReport()
```

---

# Interview Takeaway

If interviewer asks:

```text
What happens internally when a method is called?
```

Strong Answer:

```text
When a method is called,
the JVM creates a stack frame in Stack Memory.

The method executes inside that frame.

After execution completes,
control returns to the calling method
and the stack frame is removed.

This push-pop mechanism continues
for every method call during execution.
```

---

# End of Part 1

## Next Part

Part 2 → Method Declaration & Calling

Topics:

* Method Declaration
* Method Calling
* Void Methods
* Methods Returning Values
* Static Methods
* Non-Static Methods
* Calling Methods Across Classes
* Execution Flow Diagrams
* Selenium Framework Examples
* Interview Questions
* Project Scenarios
