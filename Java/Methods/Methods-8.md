# Java Methods Master Guide

# Part 8 - Variable Arguments (Varargs) & Recursion

---

# Table of Contents

1. Introduction
2. What are Variable Arguments (Varargs)?
3. Why Varargs are Needed
4. Varargs Syntax
5. Varargs vs Arrays
6. Varargs Rules
7. Internal Working of Varargs
8. Method Overloading with Varargs
9. What is Recursion?
10. Recursive Method Structure
11. Base Case & Recursive Case
12. Factorial Program
13. Fibonacci Program
14. Recursion Stack Frames
15. StackOverflowError
16. Real Project Examples
17. Selenium Framework Usage
18. API Framework Usage
19. Common Interview Mistakes
20. Advanced Interview Questions
21. Quick Revision Notes
22. Final Cheat Sheet

---

# 1. Introduction

In previous parts we learned:

* Method Declaration
* Parameters
* Return Types
* Method Overloading
* Method Overriding
* Pass By Value

In this part we will learn two important topics:

```text
Varargs

Recursion
```

These topics are frequently asked in Java interviews because they test method design and JVM understanding.

---

# 2. What are Variable Arguments (Varargs)?

Definition:

```text
Varargs allow a method to accept
a variable number of arguments.
```

Before Java 5:

```java
add(10,20);

add(10,20,30);

add(10,20,30,40);
```

required multiple overloaded methods.

---

With Varargs:

```java
add(10,20);

add(10,20,30);

add(10,20,30,40);
```

all use the same method.

---

# 3. Why Varargs are Needed

Without Varargs:

```java
add(int a,int b)

add(int a,int b,int c)

add(int a,int b,int c,int d)
```

Too many overloaded methods.

---

With Varargs:

```java
add(int... numbers)
```

Single method handles everything.

---

Advantages:

```text
Cleaner Code

Flexible APIs

Reduced Overloading

Better Maintainability
```

---

# 4. Varargs Syntax

Syntax:

```java
returnType methodName(type... variableName)
```

Example:

```java
public static void printNumbers(int... nums){

}
```

---

Call:

```java
printNumbers();

printNumbers(10);

printNumbers(10,20);

printNumbers(10,20,30);
```

All valid.

---

# 5. Varargs vs Arrays

Varargs Example:

```java
public static void test(int... nums){

}
```

---

Array Example:

```java
public static void test(int[] nums){

}
```

---

Call Array Method:

```java
int[] arr =
{
10,20,30
};

test(arr);
```

---

Call Varargs Method:

```java
test(10,20,30);
```

Much easier.

---

Interview Point:

```text
Internally Varargs
is converted into an array.
```

---

# 6. Varargs Rules

Important Interview Questions.

---

## Rule 1

Only One Varargs Parameter Allowed

Valid:

```java
test(int... nums)
```

Invalid:

```java
test(int... nums,
     int... values)
```

Compilation Error.

---

## Rule 2

Varargs Must Be Last Parameter

Valid:

```java
test(String name,
     int... nums)
```

---

Invalid:

```java
test(int... nums,
     String name)
```

Compilation Error.

---

## Rule 3

Varargs Can Be Empty

Example:

```java
printNumbers();
```

Valid.

---

# 7. Internal Working of Varargs

Example:

```java
printNumbers(10,20,30);
```

Compiler Converts To:

```java
printNumbers(
new int[]{
10,
20,
30
});
```

---

Actual Method:

```java
public static void printNumbers(int[] nums){

}
```

conceptually.

---

Interview Answer:

```text
Varargs are syntactic sugar
for arrays.
```

---

# 8. Method Overloading with Varargs

Example:

```java
public static void test(int num){

    System.out.println("int");
}
```

---

```java
public static void test(int... nums){

    System.out.println("varargs");
}
```

---

Call:

```java
test(10);
```

Output:

```text
int
```

---

Reason:

```text
Exact Match Gets Priority
```

---

Priority Order:

```text
Exact Match

↓

Promotion

↓

Autoboxing

↓

Varargs
```

Important Interview Topic.

---

# 9. What is Recursion?

Definition:

```text
Recursion is a process in which
a method calls itself.
```

---

Example:

```java
public static void test(){

    test();
}
```

---

Output:

```text
StackOverflowError
```

---

Because recursion never stops.

---

# 10. Recursive Method Structure

Every recursive method requires:

```text
Base Case

+

Recursive Case
```

---

General Structure:

```java
public static void method(){

    if(baseCondition){

        return;
    }

    method();
}
```

---

Without Base Case:

```text
Infinite Recursion
```

---

# 11. Base Case & Recursive Case

Example:

```java
public static void count(int n){

    if(n==0){

        return;
    }

    System.out.println(n);

    count(n-1);
}
```

---

Execution:

```text
count(3)

↓

count(2)

↓

count(1)

↓

count(0)

↓

Stop
```

---

Output:

```text
3
2
1
```

---

# 12. Factorial Program

Most Common Interview Question.

Formula:

```text
5! = 5×4×3×2×1
```

---

Recursive Solution:

```java
public static int factorial(int n){

    if(n==1){

        return 1;
    }

    return n *
           factorial(n-1);
}
```

---

Call:

```java
factorial(5);
```

---

Execution:

```text
5 * factorial(4)

4 * factorial(3)

3 * factorial(2)

2 * factorial(1)

1
```

---

Output:

```text
120
```

---

# 13. Fibonacci Program

Very Popular Interview Question.

Sequence:

```text
0 1 1 2 3 5 8 13
```

---

Program:

```java
public static int fibonacci(int n){

    if(n<=1){

        return n;
    }

    return fibonacci(n-1)
         + fibonacci(n-2);
}
```

---

Example:

```java
fibonacci(5)
```

Output:

```text
5
```

---

Interview Note:

Recursive Fibonacci is slow.

---

# 14. Recursion Stack Frames

Example:

```java
factorial(3);
```

Stack:

```text
+----------------+
| factorial(1)   |
+----------------+
| factorial(2)   |
+----------------+
| factorial(3)   |
+----------------+
| main()         |
+----------------+
```

---

Return Flow:

```text
factorial(1)

↓

factorial(2)

↓

factorial(3)

↓

main()
```

---

Each recursive call creates a new stack frame.

---

# 15. StackOverflowError

Important Interview Question.

Example:

```java
public static void test(){

    test();
}
```

---

Result:

```text
StackOverflowError
```

---

Reason:

```text
Infinite Stack Frame Creation
```

---

Common Causes:

```text
Missing Base Case

Wrong Exit Condition

Infinite Recursion
```

---

# 16. Real Project Examples

Recursion is used in:

```text
Tree Traversal

Folder Traversal

JSON Parsing

XML Processing

Graph Algorithms
```

---

Example:

```java
readFolder(folder);
```

calls itself for subfolders.

---

# 17. Selenium Framework Usage

Rarely used directly.

Possible uses:

```text
Nested Menu Traversal

Tree Structures

Folder Screenshot Processing
```

---

Example:

```java
clickMenu(menu);
```

may recursively traverse child menus.

---

# 18. API Framework Usage

Examples:

```text
JSON Traversal

Nested Response Validation

Tree-Based Structures
```

---

Example:

```java
findNode(jsonNode);
```

may recursively inspect child nodes.

---

# 19. Common Interview Mistakes

---

## Mistake 1

No Base Case

```java
test(){

   test();
}
```

---

## Mistake 2

Wrong Base Condition

```java
if(n==100)
```

when value never reaches 100.

---

## Mistake 3

Thinking Varargs Create Multiple Methods

Wrong.

Compiler converts them into arrays.

---

## Mistake 4

Ignoring Stack Memory Usage

Every recursive call creates:

```text
New Stack Frame
```

---

# 20. Advanced Interview Questions

---

## Q1 What are Varargs?

Answer:

```text
Methods accepting variable
number of arguments.
```

---

## Q2 How are Varargs Implemented Internally?

Answer:

```text
Compiler converts them
into arrays.
```

---

## Q3 Can Multiple Varargs Exist?

Answer:

```text
No
```

---

## Q4 What is Recursion?

Answer:

```text
Method calling itself.
```

---

## Q5 What is Base Case?

Answer:

```text
Condition that stops recursion.
```

---

## Q6 What Happens Without Base Case?

Answer:

```text
StackOverflowError
```

---

## Q7 Why is Recursive Fibonacci Slow?

Answer:

```text
Repeated Calculations
```

---

# 21. Quick Revision Notes

```text
Varargs

Variable Arguments

Internally Arrays

One Varargs Allowed

Must Be Last Parameter

Recursion

Method Calls Itself

Needs Base Case

Needs Recursive Case

Creates Stack Frames

Infinite Recursion

↓

StackOverflowError
```

---

# 22. Final Cheat Sheet

```text
Varargs

int... nums

Example

test(10)

test(10,20)

test(10,20,30)

Compiler Converts

↓

Array

Recursion

Method Calls Itself

Requires

Base Case

+

Recursive Case

Common Problems

Factorial

Fibonacci

Tree Traversal

Interview Favorite

StackOverflowError
```

---

# Interview Takeaway

If interviewer asks:

```text
Why does recursion cause StackOverflowError?
```

Strong Answer:

```text
Every recursive method call creates
a new stack frame in JVM Stack Memory.

If recursion continues indefinitely
or lacks a proper base condition,
stack frames keep accumulating until
the stack memory limit is exceeded.

At that point JVM throws
StackOverflowError.
```

---

# End of Part 8

## Next Part

Part 9 → Static Methods vs Instance Methods Deep Dive

Topics:

* Static Methods
* Instance Methods
* Static Context
* Non-Static Context
* this Keyword
* Memory Allocation
* Utility Classes
* Singleton Usage
* Framework Design Examples
* Advanced Interview Questions
