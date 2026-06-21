# Java Arrays Master Guide

# Part 5 - Single Dimensional Arrays Deep Dive

---

# Table of Contents

1. Introduction
2. What is a Single Dimensional Array?
3. Internal Memory Representation
4. Array References Explained
5. Understanding Reference Variables
6. Array Object vs Array Reference
7. Passing Arrays to Methods
8. Returning Arrays from Methods
9. Array Assignment Internals
10. Shallow Copy
11. Deep Copy
12. Array Equality
13. Garbage Collection & Arrays
14. JVM Internals
15. Common Interview Traps
16. Selenium Framework Usage
17. API Testing Usage
18. Interview Questions & Answers
19. Short Notes
20. Revision Sheet

---

# 1. Introduction

Most Java developers know how to create arrays:

```java
int[] arr = {10,20,30};
```

But many interview candidates fail when asked:

```text
What exactly is stored in arr?
How does assignment work?
What happens internally?
```

This chapter focuses on:

```text
Array references, memory behavior,
copying, equality, and JVM internals.
```

These topics are frequently asked in:

* Java Interviews
* Automation Interviews
* Product-Based Companies
* Framework Design Discussions

---

# 2. What is a Single Dimensional Array?

A single dimensional array stores data in one direction.

Example:

```java
int[] marks = {80,90,70,95};
```

Visualization:

```text
Index

0 -> 80

1 -> 90

2 -> 70

3 -> 95
```

Only one index is required.

---

# 3. Internal Memory Representation

Example:

```java
int[] arr = {10,20,30};
```

Memory:

```text
Stack

arr
 |
 |
 V

Heap

+-----+
| 10  |
+-----+
| 20  |
+-----+
| 30  |
+-----+
```

Important:

```text
Array object lives in Heap.

Reference lives in Stack.
```

---

# 4. Array References Explained

Consider:

```java
int[] arr = {10,20,30};
```

Many beginners think:

```text
arr contains values
```

Wrong.

Actually:

```text
arr contains memory reference.
```

Memory:

```text
arr ---> 0x100
```

Heap:

```text
0x100

[10][20][30]
```

---

# 5. Understanding Reference Variables

Example:

```java
String str = "Java";
```

Similarly:

```java
int[] arr = {10,20,30};
```

Both store references.

---

Interview Statement:

```text
Every array variable is a reference variable.
```

Very important.

---

# 6. Array Object vs Array Reference

Most asked interview question.

Example:

```java
int[] arr = new int[5];
```

---

## Array Object

```java
new int[5]
```

Actual memory block.

---

## Reference Variable

```java
arr
```

Stores memory address.

---

Visualization:

```text
Reference Variable

arr
 |
 |
 V

Array Object

[0][0][0][0][0]
```

---

# 7. Passing Arrays to Methods

Arrays are passed using references.

---

Example

```java
public static void display(int[] arr){

    for(int num : arr){
        System.out.println(num);
    }
}
```

Call:

```java
int[] numbers = {10,20,30};

display(numbers);
```

Output:

```text
10
20
30
```

---

Important:

```text
Entire array is NOT copied.
Only reference is passed.
```

---

# 8. Returning Arrays from Methods

Arrays can be returned.

Example:

```java
public static int[] createArray(){

    int[] arr = {10,20,30};

    return arr;
}
```

Usage:

```java
int[] result = createArray();
```

---

Interview Question:

Can a method return an array?

Answer:

```text
Yes.
Arrays are objects and references can be returned.
```

---

# 9. Array Assignment Internals

Important Interview Topic.

---

Example

```java
int[] arr1 = {10,20,30};

int[] arr2 = arr1;
```

Memory:

```text
arr1 ----|
         |
         V

      [10][20][30]

         ^
         |
arr2 ----|
```

Both point to same object.

---

Now:

```java
arr2[0] = 999;
```

Output:

```java
System.out.println(arr1[0]);
```

Result:

```text
999
```

Because both references point to same array.

---

# 10. Shallow Copy

Definition:

```text
Copying reference only.
```

Example:

```java
int[] arr1 = {10,20,30};

int[] arr2 = arr1;
```

Memory:

```text
One Array Object

Two References
```

---

Changes affect both variables.

---

Example:

```java
arr2[1] = 777;
```

Output:

```java
System.out.println(arr1[1]);
```

Result:

```text
777
```

---

# 11. Deep Copy

Definition:

```text
Creating a completely new array object.
```

---

Method 1

Manual Copy

```java
int[] copy = new int[arr.length];

for(int i=0;i<arr.length;i++){
    copy[i] = arr[i];
}
```

---

Method 2

```java
int[] copy = arr.clone();
```

---

Method 3

```java
int[] copy =
Arrays.copyOf(arr, arr.length);
```

---

Memory:

```text
arr  ---> [10][20][30]

copy ---> [10][20][30]
```

Two different objects.

---

# 12. Array Equality

Very common interview question.

---

Example

```java
int[] a = {1,2,3};

int[] b = {1,2,3};
```

---

Wrong:

```java
System.out.println(a == b);
```

Output:

```text
false
```

Reason:

```text
Reference comparison
```

---

Correct:

```java
Arrays.equals(a,b);
```

Output:

```text
true
```

---

## Why?

Because:

```text
Arrays.equals()
compares element values.
```

---

# 13. Garbage Collection & Arrays

Example:

```java
int[] arr = new int[1000];
```

Later:

```java
arr = null;
```

Now:

```text
No references exist.
```

Array becomes:

```text
Eligible for Garbage Collection.
```

---

Interview Question:

When does array become eligible for GC?

Answer:

```text
When no active reference points to it.
```

---

# 14. JVM Internals

Example:

```java
int[] arr = new int[3];
```

Execution Flow:

```text
Class Loader
      |
      V
Memory Allocation
      |
      V
Default Initialization
      |
      V
Reference Assignment
```

---

Heap:

```text
[0][0][0]
```

---

Stack:

```text
arr
```

stores reference.

---

# 15. Common Interview Traps

---

## Trap 1

```java
int[] arr1 = {1,2,3};

int[] arr2 = arr1;
```

Question:

Are there two arrays?

Answer:

```text
No.

Only one array object exists.
```

---

## Trap 2

```java
arr.clone()
```

Question:

Shallow or Deep?

Answer:

```text
Deep copy for primitive arrays.
```

---

## Trap 3

```java
a == b
```

Compares:

```text
References
```

Not values.

---

## Trap 4

```java
Arrays.equals(a,b)
```

Compares:

```text
Elements
```

---

# 16. Selenium Framework Usage

Framework Example:

```java
String[] browsers =
{
"Chrome",
"Firefox",
"Edge"
};
```

Passing browser array:

```java
executeBrowsers(browsers);
```

Only reference passed.

Efficient memory usage.

---

Environment Configuration:

```java
String[] envs =
{
"QA",
"UAT",
"PROD"
};
```

Common in automation frameworks.

---

# 17. API Testing Usage

Example:

```java
String[] endpoints =
{
"/users",
"/orders",
"/products"
};
```

Passed between:

```text
API Utility Classes
Validation Classes
Execution Classes
```

Reference sharing improves performance.

---

# 18. Interview Questions & Answers

---

## Q1 Is array a primitive?

No.

Array is an object.

---

## Q2 What does array variable store?

Reference.

---

## Q3 What is shallow copy?

Copying reference only.

---

## Q4 What is deep copy?

Creating new object and copying data.

---

## Q5 Difference between == and Arrays.equals()?

==

```text
Reference comparison
```

Arrays.equals()

```text
Value comparison
```

---

## Q6 Can array be returned from method?

Yes.

---

## Q7 Can array be passed to method?

Yes.

---

## Q8 When does array become eligible for GC?

When no reference points to it.

---

# 19. Short Notes

✔ Array variable stores reference

✔ Array object stored in heap

✔ Assignment copies reference

✔ clone() creates new object

✔ Arrays.equals() compares values

✔ == compares references

✔ Arrays can be passed to methods

✔ Arrays can be returned from methods

---

# 20. Revision Sheet

```text
Array = Object

Reference = Variable

Heap = Array Object

Stack = Reference

arr2 = arr1
→ Shallow Copy

clone()
→ New Array Object

Arrays.equals()
→ Value Comparison

==
→ Reference Comparison

No Reference
→ Eligible for GC
```

---

# Interview Takeaway

If interviewer asks:

```text
Explain shallow copy and deep copy in arrays.
```

Answer:

```text
Shallow copy occurs when only the reference is copied.

Example:

int[] arr2 = arr1;

Both references point to the same array object.

Deep copy creates a completely new array object
and copies all elements.

Examples include:

clone()
Arrays.copyOf()
Manual copying using loops

Changes made to deep copy do not affect
the original array.
```

---

# End of Part 5

## Next Part

### Part 6 – Multidimensional Arrays (2D Arrays & Jagged Arrays)

Topics:

* 2D Arrays
* Matrix Representation
* Memory Layout
* Jagged Arrays
* Row vs Column Concepts
* Matrix Traversal
* Matrix Operations
* Selenium Web Table Handling
* API Response Mapping
* Interview Questions

---

### Coming Next

**Part 6 – Multidimensional Arrays**
**Part 7 – Array Coding Problems (Basic)**
**Part 8 – Array Coding Problems (Intermediate)**
**Part 9 – Advanced Array Problems (Product Company Level)**
**Part 10 – Arrays in Selenium & API Frameworks**
**Part 11 – Performance & Optimization**
**Part 12 – Final Revision & Interview Cheat Sheet**
