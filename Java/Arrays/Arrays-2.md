# Java Arrays Master Guide

# Part 2 - Array Creation & Initialization Techniques

---

# Table of Contents

1. Introduction
2. Array Creation Process
3. Array Declaration
4. Array Instantiation
5. Array Initialization
6. Default Values in Arrays
7. Primitive Type Arrays
8. Object Type Arrays
9. String Arrays
10. Anonymous Arrays
11. Dynamic Initialization
12. Array Memory Allocation Process
13. JVM Internals During Array Creation
14. Common Interview Traps
15. Real-Time Project Usage
16. Selenium Framework Examples
17. API Testing Examples
18. Interview Questions & Answers
19. Short Notes
20. Revision Sheet

---

# 1. Introduction

In Part 1, we learned:

* What arrays are
* Memory model
* Heap vs Stack
* Array internals

In this part we will focus on:

```text
How arrays are actually created inside JVM
```

This is one of the most frequently asked Java interview topics.

---

# 2. Array Creation Process

When we write:

```java
int[] arr = new int[5];
```

Java performs 3 steps:

---

## Step 1: Declaration

```java
int[] arr;
```

Compiler creates a reference variable.

---

## Step 2: Object Creation

```java
new int[5];
```

JVM allocates memory in heap.

---

## Step 3: Reference Assignment

```java
arr = new int[5];
```

Reference variable points to array object.

---

Visualization:

```text
Stack Memory

arr
 |
 |
 V

Heap Memory

[0][0][0][0][0]
```

---

# 3. Array Declaration

Declaration means:

```text
Informing compiler about array type
```

---

## Syntax 1 (Recommended)

```java
int[] arr;
```

Recommended because:

```text
Type belongs to variable clearly
```

---

## Syntax 2

```java
int arr[];
```

Allowed but not preferred.

---

## Multiple Declarations

```java
int[] a, b, c;
```

All are arrays.

---

Interview Tip:

```text
Prefer int[] arr;
```

because it improves readability.

---

# 4. Array Instantiation

Instantiation means:

```text
Creating actual array object
```

Example:

```java
int[] arr = new int[5];
```

---

What happens internally?

JVM creates:

```text
Index

0
1
2
3
4
```

All initialized with default values.

---

# 5. Array Initialization

Initialization means:

```text
Assigning values to array elements
```

---

## Method 1

```java
int[] arr = {10,20,30};
```

---

## Method 2

```java
int[] arr = new int[3];

arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
```

---

Memory:

```text
Index    Value

0 ------> 10

1 ------> 20

2 ------> 30
```

---

# 6. Default Values in Arrays

One of the most important Java interview topics.

When array is created:

```java
int[] arr = new int[5];
```

JVM automatically initializes values.

---

## int

```java
int[] arr = new int[3];
```

Output:

```text
0
0
0
```

---

## double

```java
double[] arr = new double[3];
```

Output:

```text
0.0
0.0
0.0
```

---

## boolean

```java
boolean[] arr = new boolean[3];
```

Output:

```text
false
false
false
```

---

## char

```java
char[] arr = new char[3];
```

Output:

```text
'\u0000'
```

Null character.

---

## String

```java
String[] arr = new String[3];
```

Output:

```text
null
null
null
```

---

Interview Question

### Why are arrays automatically initialized?

Answer:

```text
To prevent garbage values and ensure predictable behavior.
```

---

# 7. Primitive Type Arrays

Stores primitive values directly.

Example:

```java
int[] numbers = {10,20,30};
```

Memory:

```text
[10][20][30]
```

---

Types:

```java
byte[]
short[]
int[]
long[]
float[]
double[]
char[]
boolean[]
```

---

# 8. Object Type Arrays

Stores references.

Example:

```java
String[] names =
{
"Rahul",
"Rohini",
"John"
};
```

Memory:

```text
Array Object

[Ref][Ref][Ref]

       |
       |
       V

String Objects
```

Important:

```text
Object arrays store references, not actual objects.
```

---

# 9. String Arrays

Most used in Selenium and Framework Design.

Example:

```java
String[] browsers =
{
"Chrome",
"Firefox",
"Edge"
};
```

Usage:

```java
for(String browser : browsers){
    System.out.println(browser);
}
```

---

Framework Example:

```java
String[] envs =
{
"QA",
"UAT",
"PROD"
};
```

---

# 10. Anonymous Arrays

Created without reference variable.

Example:

```java
new int[]{10,20,30};
```

---

Usage:

```java
display(new int[]{10,20,30});
```

Method:

```java
public static void display(int[] arr){
    for(int num : arr){
        System.out.println(num);
    }
}
```

---

Interview Question:

### Why use anonymous arrays?

Answer:

```text
Temporary array object used only once.
```

---

# 11. Dynamic Initialization

Values assigned at runtime.

Example:

```java
Scanner sc = new Scanner(System.in);

int[] arr = new int[3];

for(int i=0;i<arr.length;i++){
    arr[i] = sc.nextInt();
}
```

User input decides values.

---

Real-world Example:

```text
Reading test data
Reading API data
Reading file contents
```

---

# 12. Array Memory Allocation Process

Example:

```java
int[] arr = new int[4];
```

JVM performs:

---

Step 1

```text
Creates reference variable
```

---

Step 2

```text
Allocates heap memory
```

---

Step 3

```text
Stores default values
```

---

Step 4

```text
Returns memory reference
```

---

Visualization:

```text
Stack

arr
 |
 |
 V

Heap

+----+
| 0  |
+----+
| 0  |
+----+
| 0  |
+----+
| 0  |
+----+
```

---

# 13. JVM Internals During Array Creation

Example:

```java
int[] arr = new int[5];
```

Internally:

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
Reference Returned
```

---

Important Interview Point:

```text
Array length becomes immutable after creation.
```

Cannot do:

```java
arr.length = 10;
```

---

# 14. Common Interview Traps

---

## Trap 1

```java
int[] arr;

System.out.println(arr[0]);
```

Output:

```text
Compile Error
```

Reason:

```text
Array not initialized
```

---

## Trap 2

```java
int[] arr = new int[3];

arr[3] = 100;
```

Output:

```text
ArrayIndexOutOfBoundsException
```

---

## Trap 3

```java
String[] names = new String[3];

System.out.println(names[0].length());
```

Output:

```text
NullPointerException
```

---

# 15. Real-Time Project Usage

Configuration Handling:

```java
String[] environments =
{
"QA",
"UAT",
"PROD"
};
```

---

Country Codes:

```java
String[] countries =
{
"IN",
"US",
"UK"
};
```

---

Test Data Storage:

```java
String[] usernames =
{
"user1",
"user2",
"user3"
};
```

---

# 16. Selenium Framework Examples

Browser execution:

```java
String[] browsers =
{
"Chrome",
"Firefox",
"Edge"
};

for(String browser : browsers){
    System.out.println(browser);
}
```

---

Cross Environment Testing:

```java
String[] urls =
{
"qa.site.com",
"uat.site.com",
"prod.site.com"
};
```

---

# 17. API Testing Examples

Endpoints:

```java
String[] endpoints =
{
"/users",
"/orders",
"/products"
};
```

Execution:

```java
for(String endpoint : endpoints){
    System.out.println(endpoint);
}
```

---

Headers:

```java
String[] headers =
{
"Authorization",
"Content-Type",
"Accept"
};
```

---

# 18. Interview Questions & Answers

---

## Q1 Difference between declaration and initialization?

Declaration:

```java
int[] arr;
```

Initialization:

```java
arr = new int[5];
```

---

## Q2 Default value of String array?

```text
null
```

---

## Q3 Default value of boolean array?

```text
false
```

---

## Q4 Are object arrays storing objects?

No.

They store references.

---

## Q5 Can arrays be created dynamically?

Yes.

```java
new int[size];
```

---

## Q6 What is anonymous array?

Array without reference variable.

---

# 19. Short Notes

✔ Arrays get default values

✔ Primitive arrays store values

✔ Object arrays store references

✔ String arrays store String references

✔ Anonymous arrays are temporary

✔ Length is fixed

✔ Array object resides in heap

---

# 20. Revision Sheet

```text
Declaration → int[] arr

Instantiation → new int[5]

Initialization → assign values

Default int → 0

Default double → 0.0

Default boolean → false

Default String → null

Object Array → references

Anonymous Array → one-time use

Length → fixed forever
```

---

# Interview Takeaway

If interviewer asks:

"Explain array creation process in Java."

Answer:

```text
Array creation involves declaration,
instantiation, and initialization.

The array object is created in heap memory,
default values are assigned automatically,
and a reference is returned to the stack variable.

Primitive arrays store values directly,
while object arrays store references.
```

---

# End of Part 2

## Next Part (Will Continue Automatically)

### Part 3 – Array Traversal Techniques

Topics:

* for loop traversal
* while loop traversal
* do-while traversal
* for-each traversal
* Forward traversal
* Reverse traversal
* Traversing object arrays
* Traversing String arrays
* Performance considerations
* Real Selenium & API examples
* Interview traps and questions
