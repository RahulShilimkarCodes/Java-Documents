# Java Arrays Master Guide

# Part 3 - Array Traversal Techniques

---

# Table of Contents

1. Introduction to Array Traversal
2. Why Traversal is Important
3. Traversal Using for Loop
4. Traversal Using while Loop
5. Traversal Using do-while Loop
6. Traversal Using Enhanced for Loop
7. Forward Traversal
8. Reverse Traversal
9. Traversing Primitive Arrays
10. Traversing Object Arrays
11. Traversing String Arrays
12. Array Length Property
13. Performance Considerations
14. Internal Working of Traversal
15. Common Interview Traps
16. Real Selenium Examples
17. Real API Testing Examples
18. Interview Questions & Answers
19. Short Notes
20. Revision Sheet

---

# 1. Introduction to Array Traversal

Traversal means:

```text
Visiting every element of an array one by one.
```

Example:

```java
int[] arr = {10,20,30,40,50};
```

Traversal:

```text
10
20
30
40
50
```

---

# 2. Why Traversal is Important

Almost every array operation requires traversal.

Examples:

* Searching
* Sorting
* Updating
* Validation
* Summation
* Average Calculation

Without traversal:

```text
We cannot process array elements efficiently.
```

---

# 3. Traversal Using for Loop

Most commonly used technique.

Example:

```java
int[] arr = {10,20,30,40,50};

for(int i=0;i<arr.length;i++){
    System.out.println(arr[i]);
}
```

Output:

```text
10
20
30
40
50
```

---

## Why for Loop is Popular?

Because:

```text
Index is available.
```

Useful when:

* Updating values
* Accessing neighboring elements
* Searching

---

# 4. Traversal Using while Loop

Example:

```java
int[] arr = {10,20,30,40};

int i = 0;

while(i < arr.length){
    System.out.println(arr[i]);
    i++;
}
```

Output:

```text
10
20
30
40
```

---

## When to Use while?

Use when:

```text
Number of iterations depends on condition.
```

Example:

* Retry mechanisms
* Dynamic processing

---

# 5. Traversal Using do-while Loop

Example:

```java
int[] arr = {10,20,30};

int i = 0;

do{
    System.out.println(arr[i]);
    i++;
}
while(i < arr.length);
```

---

Important:

```text
do-while executes at least once.
```

---

# 6. Traversal Using Enhanced for Loop

Also called:

```text
for-each loop
```

Example:

```java
int[] arr = {10,20,30};

for(int num : arr){
    System.out.println(num);
}
```

Output:

```text
10
20
30
```

---

## Internal Meaning

```java
for(int num : arr)
```

means:

```text
Take each element from array one by one.
```

---

# 7. Forward Traversal

Normal traversal.

Example:

```java
int[] arr = {10,20,30,40};

for(int i=0;i<arr.length;i++){
    System.out.println(arr[i]);
}
```

Order:

```text
10
20
30
40
```

---

# 8. Reverse Traversal

Frequently asked interview question.

Example:

```java
int[] arr = {10,20,30,40};

for(int i=arr.length-1;i>=0;i--){
    System.out.println(arr[i]);
}
```

Output:

```text
40
30
20
10
```

---

## Interview Insight

Many reverse-array problems start with:

```text
Reverse traversal logic.
```

---

# 9. Traversing Primitive Arrays

Example:

```java
int[] marks = {80,90,70};

for(int mark : marks){
    System.out.println(mark);
}
```

---

Supported Types:

```java
int[]
double[]
char[]
boolean[]
float[]
long[]
short[]
byte[]
```

---

# 10. Traversing Object Arrays

Example:

```java
String[] names =
{
"Rahul",
"Rohini",
"John"
};

for(String name : names){
    System.out.println(name);
}
```

Output:

```text
Rahul
Rohini
John
```

---

# 11. Traversing String Arrays

Very common in automation frameworks.

Example:

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

Output:

```text
Chrome
Firefox
Edge
```

---

# 12. Array Length Property

Length gives total elements.

Example:

```java
int[] arr = {10,20,30};

System.out.println(arr.length);
```

Output:

```text
3
```

---

Important:

```text
length is a property
NOT a method
```

Correct:

```java
arr.length
```

Wrong:

```java
arr.length()
```

---

# 13. Performance Considerations

---

## Array Access Complexity

```java
arr[i]
```

Complexity:

```text
O(1)
```

---

## Complete Traversal

```java
for(int i=0;i<arr.length;i++)
```

Complexity:

```text
O(n)
```

---

## Nested Traversal

```java
for(...)
{
    for(...)
    {
    }
}
```

Complexity:

```text
O(n²)
```

---

## Interview Rule

```text
Single traversal = O(n)

Nested traversal = O(n²)
```

---

# 14. Internal Working of Traversal

Example:

```java
int[] arr = {10,20,30};
```

Memory:

```text
Index   Value

0 ----> 10

1 ----> 20

2 ----> 30
```

Traversal:

```text
Read index 0

Read index 1

Read index 2
```

Sequential memory access is very fast.

---

# 15. Common Interview Traps

---

## Trap 1

```java
for(int i=0;i<=arr.length;i++)
```

Output:

```text
ArrayIndexOutOfBoundsException
```

Correct:

```java
i < arr.length
```

---

## Trap 2

```java
arr.length()
```

Wrong.

Correct:

```java
arr.length
```

---

## Trap 3

```java
for(int i=1;i<arr.length;i++)
```

First element skipped.

---

## Trap 4

```java
for(int i=arr.length;i>=0;i--)
```

Invalid starting index.

Correct:

```java
arr.length - 1
```

---

# 16. Real Selenium Examples

---

## Multiple Browser Execution

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

## Environment Testing

```java
String[] envs =
{
"QA",
"UAT",
"PROD"
};

for(String env : envs){
    System.out.println(env);
}
```

---

## Data-Driven Execution

```java
String[] users =
{
"user1",
"user2",
"user3"
};

for(String user : users){
    System.out.println(user);
}
```

---

# 17. Real API Testing Examples

---

## Endpoint Traversal

```java
String[] endpoints =
{
"/users",
"/orders",
"/products"
};

for(String endpoint : endpoints){
    System.out.println(endpoint);
}
```

---

## Header Validation

```java
String[] headers =
{
"Authorization",
"Content-Type",
"Accept"
};

for(String header : headers){
    System.out.println(header);
}
```

---

# 18. Interview Questions & Answers

---

## Q1 What is array traversal?

Visiting each element one by one.

---

## Q2 Complexity of traversal?

```text
O(n)
```

---

## Q3 Which loop is best?

Depends on requirement.

Usually:

```text
for loop
```

---

## Q4 Difference between for and for-each?

for:

```text
Index available
```

for-each:

```text
Cleaner syntax
No index access
```

---

## Q5 Why use arr.length?

To avoid hardcoded size.

---

## Q6 Can we modify elements in for-each?

Not directly through loop variable.

---

# 19. Short Notes

✔ Traversal = visiting elements

✔ for loop most common

✔ while useful for dynamic conditions

✔ do-while executes once

✔ for-each simplifies code

✔ length is property

✔ Traversal complexity = O(n)

---

# 20. Revision Sheet

```text
Traversal = visit every element

for → index available

while → condition based

do-while → executes once

for-each → cleaner traversal

arr.length → total elements

Traversal Complexity → O(n)

Nested Traversal → O(n²)

Reverse Traversal →
arr.length-1 to 0
```

---

# Interview Takeaway

If interviewer asks:

"How do you traverse an array in Java?"

Answer:

```text
Arrays can be traversed using
for loop,
while loop,
do-while loop,
and enhanced for loop.

The most common approach is the for loop because it provides index access.
Traversal complexity is O(n) because each element is visited exactly once.
```

---

# End of Part 3

## Next Part

### Part 4 – Array Operations

Topics:

* Insert Element
* Update Element
* Delete Element
* Search Element
* Copy Arrays
* Clone Arrays
* Compare Arrays
* Reverse Arrays
* Rotate Arrays
* Real Interview Questions
* Practical Coding Examples
