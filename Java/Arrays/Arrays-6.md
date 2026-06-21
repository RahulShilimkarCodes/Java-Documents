# Java Arrays Master Guide

# Part 6 - Multidimensional Arrays (2D Arrays & Jagged Arrays)

---

# Table of Contents

1. Introduction to Multidimensional Arrays
2. What is a 2D Array?
3. Why 2D Arrays Are Needed
4. Declaration of 2D Arrays
5. Creation & Initialization
6. Memory Representation of 2D Arrays
7. Row and Column Concept
8. Traversing 2D Arrays
9. Enhanced for-each Traversal
10. Matrix Representation
11. Matrix Operations
12. Jagged Arrays
13. Internal JVM Memory Model
14. Common Interview Traps
15. Selenium Web Table Handling
16. API Testing Use Cases
17. Interview Questions & Answers
18. Short Notes
19. Revision Sheet

---

# 1. Introduction to Multidimensional Arrays

So far we have worked with:

```java
int[] arr = {10,20,30};
```

This is called:

```text
Single Dimensional Array
```

Sometimes data is naturally arranged in:

* Rows
* Columns

Examples:

* Excel Sheets
* Database Tables
* Web Tables
* Matrices
* Student Marks Sheets

For such scenarios Java provides:

```text
Multidimensional Arrays
```

---

# 2. What is a 2D Array?

Definition:

```text
A 2D array is an array of arrays.
```

Example:

```java
int[][] marks =
{
    {80,90,70},
    {75,85,95},
    {88,92,81}
};
```

Visualization:

```text
      Col0 Col1 Col2

Row0   80   90   70

Row1   75   85   95

Row2   88   92   81
```

---

# 3. Why 2D Arrays Are Needed

Without 2D arrays:

```java
int[] student1 = {80,90,70};
int[] student2 = {75,85,95};
int[] student3 = {88,92,81};
```

Managing becomes difficult.

Using 2D arrays:

```java
int[][] marks =
{
    {80,90,70},
    {75,85,95},
    {88,92,81}
};
```

Everything is stored in one structure.

---

# 4. Declaration of 2D Arrays

## Syntax 1

```java
int[][] arr;
```

Preferred.

---

## Syntax 2

```java
int arr[][];
```

Allowed.

---

## Syntax 3

```java
int[] arr[];
```

Also valid.

---

Interview Tip:

```text
Prefer int[][] arr;
```

---

# 5. Creation & Initialization

---

## Method 1

Create First

```java
int[][] arr = new int[3][4];
```

Meaning:

```text
3 Rows
4 Columns
```

Memory:

```text
[ ][ ][ ][ ]

[ ][ ][ ][ ]

[ ][ ][ ][ ]
```

---

## Method 2

Direct Initialization

```java
int[][] arr =
{
    {1,2,3},
    {4,5,6},
    {7,8,9}
};
```

---

# 6. Memory Representation of 2D Arrays

Most Important Interview Topic.

Example:

```java
int[][] arr =
{
    {10,20},
    {30,40}
};
```

Many beginners think:

```text
One giant memory block
```

Wrong.

Internally:

```text
Main Array

      |
      |
      V

+---------+
| Ref Row0|
+---------+
| Ref Row1|
+---------+

      |            |
      V            V

 [10][20]      [30][40]
```

---

# 7. Row and Column Concept

Example:

```java
int[][] arr =
{
    {10,20,30},
    {40,50,60}
};
```

Rows:

```text
2
```

Columns:

```text
3
```

---

## Length

Rows:

```java
arr.length
```

Output:

```text
2
```

---

Columns:

```java
arr[0].length
```

Output:

```text
3
```

---

Interview Question:

Difference between:

```java
arr.length
```

and

```java
arr[0].length
```

Answer:

```text
arr.length → rows

arr[0].length → columns
```

---

# 8. Traversing 2D Arrays

Most Common Approach.

---

## Nested Loop Traversal

```java
int[][] arr =
{
    {10,20,30},
    {40,50,60}
};

for(int i=0;i<arr.length;i++){

    for(int j=0;j<arr[i].length;j++){

        System.out.print(arr[i][j] + " ");
    }

    System.out.println();
}
```

Output:

```text
10 20 30

40 50 60
```

---

Why nested loops?

```text
Outer Loop → Rows

Inner Loop → Columns
```

---

# 9. Enhanced for-each Traversal

Example:

```java
for(int[] row : arr){

    for(int value : row){

        System.out.print(value + " ");
    }

    System.out.println();
}
```

Output:

```text
10 20 30

40 50 60
```

---

Interview Insight:

```text
for-each improves readability.
```

---

# 10. Matrix Representation

2D arrays are often called matrices.

Example:

```java
int[][] matrix =
{
    {1,2},
    {3,4}
};
```

Visualization:

```text
|1 2|

|3 4|
```

---

Applications:

* Mathematics
* Machine Learning
* Graphics
* Data Processing

---

# 11. Matrix Operations

---

## Sum of Elements

```java
int sum = 0;

for(int i=0;i<arr.length;i++){

    for(int j=0;j<arr[i].length;j++){

        sum += arr[i][j];
    }
}
```

---

## Find Largest Element

```java
int max = arr[0][0];

for(int i=0;i<arr.length;i++){

    for(int j=0;j<arr[i].length;j++){

        if(arr[i][j] > max){

            max = arr[i][j];
        }
    }
}
```

---

## Row Sum

```java
for(int i=0;i<arr.length;i++){

    int sum = 0;

    for(int j=0;j<arr[i].length;j++){

        sum += arr[i][j];
    }

    System.out.println(sum);
}
```

---

# 12. Jagged Arrays

Very Frequently Asked Interview Topic.

---

Definition:

```text
Rows having different column sizes.
```

Example:

```java
int[][] arr =
{
    {10,20},
    {30,40,50},
    {60}
};
```

Visualization:

```text
10 20

30 40 50

60
```

---

Why possible?

Because:

```text
2D array is actually array of arrays.
```

Each row can have different size.

---

## Dynamic Jagged Array

```java
int[][] arr = new int[3][];

arr[0] = new int[2];

arr[1] = new int[5];

arr[2] = new int[1];
```

---

Interview Favorite Question:

```text
Is Java 2D array truly multidimensional?
```

Answer:

```text
No.

It is an array of array references.
```

---

# 13. Internal JVM Memory Model

Example:

```java
int[][] arr = new int[2][3];
```

Memory:

```text
Stack

arr
 |
 |
 V

Heap

Main Array

+------+
| Ref1 |
+------+
| Ref2 |
+------+

   |          |
   V          V

[0][0][0]

[0][0][0]
```

---

Interview Insight:

```text
Java multidimensional arrays
are arrays of references.
```

---

# 14. Common Interview Traps

---

## Trap 1

```java
arr.length
```

Returns:

```text
Rows
```

Not total elements.

---

## Trap 2

```java
arr[0].length
```

Returns:

```text
Columns of first row
```

---

## Trap 3

Assuming all rows have same size.

Wrong for:

```text
Jagged Arrays
```

---

## Trap 4

Using:

```java
for(int j=0;j<arr[0].length;j++)
```

for jagged arrays.

Can cause:

```text
ArrayIndexOutOfBoundsException
```

Use:

```java
arr[i].length
```

---

# 15. Selenium Web Table Handling

One of the best practical examples.

Suppose:

```text
Employee Table

Name   Age

John   25

David  30
```

Extracting data conceptually becomes:

```java
String[][] tableData =
{
    {"John","25"},
    {"David","30"}
};
```

Traversal:

```java
for(String[] row : tableData){

    for(String value : row){

        System.out.print(value + " ");
    }
}
```

---

Real Selenium frameworks use similar row-column processing.

---

# 16. API Testing Use Cases

Example JSON:

```json
{
  "users":[
      {"id":1,"name":"John"},
      {"id":2,"name":"David"}
  ]
}
```

Conceptually:

```text
Rows = Users

Columns = Fields
```

Processing follows similar nested traversal logic.

---

# 17. Interview Questions & Answers

---

## Q1 What is a 2D array?

Array of arrays.

---

## Q2 How many loops required?

Usually:

```text
2 Nested Loops
```

---

## Q3 Difference between rows and columns?

Rows:

```java
arr.length
```

Columns:

```java
arr[i].length
```

---

## Q4 What is Jagged Array?

Rows with different column sizes.

---

## Q5 Is Java 2D array contiguous memory?

No.

It stores references to row arrays.

---

## Q6 Complexity of traversing matrix?

```text
O(rows × columns)
```

---

# 18. Short Notes

✔ 2D Array = Array of Arrays

✔ Rows = arr.length

✔ Columns = arr[i].length

✔ Nested loops required

✔ Jagged arrays supported

✔ Java stores row references

✔ Web tables often map to 2D structures

---

# 19. Revision Sheet

```text
2D Array
=
Array of Arrays

Rows
=
arr.length

Columns
=
arr[i].length

Traversal
=
Nested Loops

Matrix
=
2D Array

Jagged Array
=
Unequal Column Sizes

Complexity
=
O(rows × columns)

Java
=
Array of References
```

---

# Interview Takeaway

If interviewer asks:

```text
Explain how 2D arrays work internally in Java.
```

Answer:

```text
A Java 2D array is not a single contiguous block of memory.

It is an array whose elements are references to other arrays.

The main array stores references to row arrays.
Each row array stores actual values.

This design allows Java to support jagged arrays,
where different rows can have different lengths.
```

---

# End of Part 6

## Next Part

### Part 7 – Array Coding Problems (Basic)

Topics:

* Largest Element
* Smallest Element
* Sum of Elements
* Average
* Count Even/Odd
* Count Positive/Negative
* Reverse Array
* Copy Array
* Linear Search
* Most Asked Interview Coding Problems
