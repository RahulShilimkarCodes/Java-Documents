# Java Arrays Master Guide

# Part 4 - Array Operations (Insert, Update, Delete, Search, Copy, Clone, Reverse)

---

# Table of Contents

1. Introduction to Array Operations
2. Why Array Operations Matter
3. Insert Operation
4. Update Operation
5. Delete Operation
6. Search Operation
7. Linear Search
8. Binary Search
9. Copying Arrays
10. Cloning Arrays
11. Comparing Arrays
12. Reversing Arrays
13. Rotating Arrays
14. Swapping Elements
15. Internal Working & Complexity
16. Common Interview Traps
17. Selenium Framework Examples
18. API Testing Examples
19. Interview Questions & Answers
20. Short Notes
21. Revision Sheet

---

# 1. Introduction to Array Operations

After creating and traversing arrays, the next important topic is:

```text
How to perform operations on array elements.
```

Every real-world application performs:

* Insert
* Update
* Delete
* Search
* Copy
* Compare
* Reverse

operations on data.

---

# 2. Why Array Operations Matter

Interviewers ask these questions because they test:

```text
✔ Loop Knowledge
✔ Index Understanding
✔ Problem Solving Ability
✔ Time Complexity Understanding
```

Many coding rounds start with these operations.

---

# 3. Insert Operation

Arrays have fixed size.

Java does NOT provide direct insertion.

We must manually shift elements.

---

## Example

Current Array:

```text
10 20 30 40
```

Insert:

```text
25 at index 2
```

Result:

```text
10 20 25 30 40
```

---

## Program

```java
int[] arr = new int[5];

arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
arr[3] = 40;

int position = 2;
int value = 25;

for(int i = 3; i >= position; i--){
    arr[i+1] = arr[i];
}

arr[position] = value;
```

---

## Complexity

```text
O(n)
```

Because shifting is required.

---

# 4. Update Operation

Updating is easy.

Simply replace the value.

Example:

```java
int[] arr = {10,20,30};

arr[1] = 99;
```

Result:

```text
10 99 30
```

---

## Complexity

```text
O(1)
```

Direct index access.

---

# 5. Delete Operation

Deletion requires shifting.

---

Example

Before:

```text
10 20 30 40 50
```

Delete:

```text
Index 2
```

After:

```text
10 20 40 50
```

---

## Program

```java
int[] arr = {10,20,30,40,50};

int position = 2;

for(int i = position; i < arr.length - 1; i++){
    arr[i] = arr[i+1];
}
```

---

## Complexity

```text
O(n)
```

---

# 6. Search Operation

Searching means finding a value.

Example:

```text
Find 40
```

Array:

```text
10 20 30 40 50
```

Output:

```text
Found at index 3
```

---

# 7. Linear Search

Most basic search technique.

---

## Program

```java
int[] arr = {10,20,30,40,50};

int target = 40;

for(int i = 0; i < arr.length; i++){

    if(arr[i] == target){
        System.out.println(i);
        break;
    }
}
```

---

## Complexity

```text
Best Case  : O(1)

Worst Case : O(n)
```

---

## Real Interview Question

When should we use Linear Search?

Answer:

```text
When array is unsorted.
```

---

# 8. Binary Search

One of the most asked interview questions.

---

Requirement:

```text
Array MUST be sorted.
```

Example:

```text
10 20 30 40 50
```

Find:

```text
40
```

---

## Logic

Find middle.

Compare.

Move left or right.

---

## Program

```java
int[] arr = {10,20,30,40,50};

int target = 40;

int low = 0;
int high = arr.length - 1;

while(low <= high){

    int mid = (low + high)/2;

    if(arr[mid] == target){
        System.out.println(mid);
        break;
    }

    if(target > arr[mid]){
        low = mid + 1;
    }
    else{
        high = mid - 1;
    }
}
```

---

## Complexity

```text
O(log n)
```

---

## Interview Tip

Always mention:

```text
Binary Search requires sorted array.
```

---

# 9. Copying Arrays

---

## Method 1

Manual Copy

```java
int[] source = {10,20,30};

int[] target = new int[source.length];

for(int i=0;i<source.length;i++){
    target[i] = source[i];
}
```

---

## Method 2

System.arraycopy()

```java
System.arraycopy(source,0,target,0,source.length);
```

---

## Method 3

Arrays.copyOf()

```java
int[] copy =
Arrays.copyOf(source, source.length);
```

---

# 10. Cloning Arrays

Interview Favorite.

---

Example

```java
int[] arr = {10,20,30};

int[] clone = arr.clone();
```

---

## Internal Working

Creates new array object.

Copies elements.

---

Memory:

```text
arr     ---> [10 20 30]

clone   ---> [10 20 30]
```

Different objects.

---

# 11. Comparing Arrays

Wrong Approach:

```java
arr1 == arr2
```

Checks:

```text
Reference comparison
```

---

Correct:

```java
Arrays.equals(arr1, arr2);
```

---

Example

```java
int[] a = {1,2,3};
int[] b = {1,2,3};

System.out.println(Arrays.equals(a,b));
```

Output:

```text
true
```

---

# 12. Reversing Arrays

Most asked coding question.

---

Example

Before:

```text
10 20 30 40
```

After:

```text
40 30 20 10
```

---

## Program

```java
int[] arr = {10,20,30,40};

for(int i = arr.length-1; i >= 0; i--){
    System.out.println(arr[i]);
}
```

---

## Two Pointer Approach

```java
int left = 0;
int right = arr.length - 1;

while(left < right){

    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;

    left++;
    right--;
}
```

---

## Complexity

```text
O(n)
```

---

# 13. Rotating Arrays

Frequently asked.

---

Example

Left Rotation

Before:

```text
1 2 3 4 5
```

After:

```text
2 3 4 5 1
```

---

## Program

```java
int first = arr[0];

for(int i=0;i<arr.length-1;i++){
    arr[i] = arr[i+1];
}

arr[arr.length-1] = first;
```

---

# 14. Swapping Elements

Basic but extremely important.

---

Program

```java
int temp = arr[i];

arr[i] = arr[j];

arr[j] = temp;
```

Used in:

* Sorting
* Reverse
* Rotation

---

# 15. Internal Working & Complexity

| Operation     | Complexity |
| ------------- | ---------- |
| Access        | O(1)       |
| Update        | O(1)       |
| Search        | O(n)       |
| Binary Search | O(log n)   |
| Insert        | O(n)       |
| Delete        | O(n)       |
| Copy          | O(n)       |
| Reverse       | O(n)       |

---

# 16. Common Interview Traps

---

## Trap 1

```java
arr[arr.length]
```

Invalid.

Last index:

```java
arr.length - 1
```

---

## Trap 2

```java
arr1 == arr2
```

Reference comparison only.

---

## Trap 3

Using Binary Search on unsorted array.

Wrong result.

---

## Trap 4

Forgetting boundary conditions.

Example:

```java
i <= arr.length
```

Wrong.

---

# 17. Selenium Framework Examples

---

## Multiple Browser Execution

```java
String[] browsers =
{
"Chrome",
"Firefox",
"Edge"
};
```

Search browser:

```java
for(String browser : browsers){

    if(browser.equals("Chrome")){
        System.out.println("Found");
        break;
    }
}
```

---

## Environment Selection

```java
String[] envs =
{
"QA",
"UAT",
"PROD"
};
```

Used for execution configuration.

---

# 18. API Testing Examples

---

## Endpoint Validation

```java
String[] endpoints =
{
"/users",
"/orders",
"/products"
};
```

Search endpoint:

```java
for(String endpoint : endpoints){

    if(endpoint.equals("/users")){
        System.out.println("Available");
    }
}
```

---

## Response Validation

Arrays are frequently used while validating:

```text
JSON Arrays
Response Lists
Headers
```

---

# 19. Interview Questions & Answers

---

## Q1 Difference between search and access?

Access:

```java
arr[2]
```

O(1)

Search:

```text
Find location first
```

O(n)

---

## Q2 Why insertion is costly?

Because shifting is required.

---

## Q3 Why deletion is costly?

Because elements must move left.

---

## Q4 Difference between clone() and assignment?

Assignment:

```java
int[] b = a;
```

Same object.

Clone:

```java
int[] b = a.clone();
```

New object.

---

## Q5 Why Binary Search is faster?

Because search space reduces by half every iteration.

---

## Q6 Complexity of Binary Search?

```text
O(log n)
```

---

# 20. Short Notes

✔ Insert → Shift Right

✔ Delete → Shift Left

✔ Search → Linear or Binary

✔ Binary Search → Sorted Array

✔ Clone → New Object

✔ Copy → Duplicate Elements

✔ Reverse → Two Pointer Technique

---

# 21. Revision Sheet

```text
Access      → O(1)

Update      → O(1)

Search      → O(n)

Binary      → O(log n)

Insert      → O(n)

Delete      → O(n)

Clone       → clone()

Compare     → Arrays.equals()

Copy        → Arrays.copyOf()

Reverse     → Two Pointers
```

---

# Interview Takeaway

If interviewer asks:

"Which array operations are expensive and why?"

Answer:

```text
Insertion and deletion are expensive because arrays
store elements in contiguous memory locations.

To insert or delete an element,
existing elements must be shifted,
which results in O(n) complexity.

Access and update are very fast because arrays
support direct index-based access with O(1) complexity.
```

---

# End of Part 4

## Next Part

### Part 5 – Single Dimensional Arrays Deep Dive

Topics:

* Array References
* Memory Diagrams
* Shallow Copy
* Deep Copy
* Reference Variables
* Array Equality
* Pass Array to Methods
* Return Arrays from Methods
* JVM Internals
* Real Interview Scenarios
