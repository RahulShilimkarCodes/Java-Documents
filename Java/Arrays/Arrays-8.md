# Java Arrays Master Guide

# Part 8 - Intermediate Array Coding Problems

---

# Table of Contents

1. Introduction
2. Interview Strategy for Intermediate Problems
3. Move Zeroes to End
4. Move Zeroes to Beginning
5. Remove Duplicates from Sorted Array
6. Merge Two Arrays
7. Missing Number in Array
8. Union of Two Arrays
9. Intersection of Two Arrays
10. Left Rotation by One Position
11. Left Rotation by K Positions
12. Right Rotation by K Positions
13. Leaders in Array
14. Prefix Sum Technique
15. Range Sum Query
16. Kadane's Algorithm
17. Sliding Window Technique
18. Common Interview Mistakes
19. Selenium Framework Applications
20. API Testing Applications
21. Interview Questions & Answers
22. Short Notes
23. Final Revision Sheet

---

# 1. Introduction

These problems are frequently asked in:

* TCS Digital
* Capgemini
* Cognizant
* Accenture
* Infosys
* Barclays
* Automation Testing Interviews
* Product-Based Companies

These questions test:

```text
✔ Problem Solving
✔ Array Traversal
✔ Optimization Skills
✔ Time Complexity Knowledge
✔ Algorithm Understanding
```

---

# 2. Interview Strategy for Intermediate Problems

Always follow:

```text
Step 1 → Understand Problem

Step 2 → Brute Force Solution

Step 3 → Optimize

Step 4 → Explain Complexity

Step 5 → Write Clean Code
```

Interviewers value approach more than speed.

---

# 3. Move Zeroes to End

Input:

```java
{1,0,2,0,3,0,4}
```

Output:

```java
{1,2,3,4,0,0,0}
```

---

## Brute Force

Create new array.

Complexity:

```text
O(n)
Space O(n)
```

---

## Optimized Approach

Use Two Pointers.

```java
int[] arr = {1,0,2,0,3,0,4};

int index = 0;

for(int i=0;i<arr.length;i++){

    if(arr[i] != 0){

        arr[index++] = arr[i];
    }
}

while(index < arr.length){

    arr[index++] = 0;
}
```

---

Complexity:

```text
Time  : O(n)

Space : O(1)
```

---

# 4. Move Zeroes to Beginning

Input:

```java
{1,0,2,0,3}
```

Output:

```java
{0,0,1,2,3}
```

---

Approach:

Count zeroes.

Shift non-zero values.

Fill front with zeroes.

---

Complexity:

```text
O(n)
```

---

# 5. Remove Duplicates from Sorted Array

Input:

```java
{1,1,2,2,3,4,4}
```

Output:

```java
{1,2,3,4}
```

---

## Two Pointer Solution

```java
int[] arr = {1,1,2,2,3,4,4};

int j = 0;

for(int i=1;i<arr.length;i++){

    if(arr[i] != arr[j]){

        j++;

        arr[j] = arr[i];
    }
}

System.out.println(j + 1);
```

---

Complexity:

```text
O(n)
```

---

Interview Favorite:

```text
Remove duplicates from sorted array without extra space.
```

---

# 6. Merge Two Arrays

Input:

```java
a = {1,2,3}

b = {4,5,6}
```

Output:

```java
{1,2,3,4,5,6}
```

---

Program:

```java
int[] result =
new int[a.length + b.length];

for(int i=0;i<a.length;i++){

    result[i] = a[i];
}

for(int i=0;i<b.length;i++){

    result[a.length+i] = b[i];
}
```

---

Complexity:

```text
O(n+m)
```

---

# 7. Missing Number in Array

Input:

```java
{1,2,3,5}
```

Output:

```java
4
```

---

## Formula Method

Expected Sum:

```text
n(n+1)/2
```

---

Program:

```java
int n = 5;

int expected =
n*(n+1)/2;

int actual = 0;

for(int num : arr){

    actual += num;
}

System.out.println(expected-actual);
```

---

Complexity:

```text
O(n)
```

---

# 8. Union of Two Arrays

Input:

```java
{1,2,3}

{3,4,5}
```

Output:

```java
{1,2,3,4,5}
```

---

Best Approach:

```java
HashSet<Integer>
```

Example:

```java
Set<Integer> set =
new HashSet<>();
```

Add all elements.

---

Complexity:

```text
O(n+m)
```

---

# 9. Intersection of Two Arrays

Input:

```java
{1,2,3,4}

{3,4,5,6}
```

Output:

```java
3 4
```

---

Program:

```java
HashSet<Integer> set =
new HashSet<>();

for(int num : arr1){

    set.add(num);
}

for(int num : arr2){

    if(set.contains(num)){

        System.out.println(num);
    }
}
```

---

Complexity:

```text
O(n+m)
```

---

# 10. Left Rotation by One Position

Input:

```java
1 2 3 4 5
```

Output:

```java
2 3 4 5 1
```

---

Program:

```java
int first = arr[0];

for(int i=0;i<arr.length-1;i++){

    arr[i] = arr[i+1];
}

arr[arr.length-1] = first;
```

---

Complexity:

```text
O(n)
```

---

# 11. Left Rotation by K Positions

Input:

```java
1 2 3 4 5
```

Rotate:

```text
K = 2
```

Output:

```java
3 4 5 1 2
```

---

Simple Approach:

Run left rotation K times.

---

Optimized:

Use temporary array.

Complexity:

```text
O(n)
```

---

# 12. Right Rotation by K Positions

Input:

```java
1 2 3 4 5
```

K:

```text
2
```

Output:

```java
4 5 1 2 3
```

---

Interview Tip:

Remember:

```text
Left Rotation

↓

Elements move left
```

```text
Right Rotation

↓

Elements move right
```

---

# 13. Leaders in Array

Definition:

```text
Element greater than all elements
to its right.
```

---

Input:

```java
{16,17,4,3,5,2}
```

Output:

```java
17

5

2
```

---

Optimized Solution

Traverse from right.

```java
int leader =
arr[arr.length-1];

System.out.println(leader);

for(int i=arr.length-2;i>=0;i--){

    if(arr[i] > leader){

        leader = arr[i];

        System.out.println(leader);
    }
}
```

---

Complexity:

```text
O(n)
```

---

# 14. Prefix Sum Technique

Very important interview topic.

---

Input:

```java
{10,20,30,40}
```

Prefix Sum:

```java
{10,30,60,100}
```

---

Program:

```java
prefix[0] = arr[0];

for(int i=1;i<arr.length;i++){

    prefix[i] =
    prefix[i-1] + arr[i];
}
```

---

Used for:

* Range Queries
* Competitive Programming
* Analytics Systems

---

# 15. Range Sum Query

Array:

```java
{10,20,30,40}
```

Find:

```text
Index 1 to 3
```

Result:

```text
90
```

Using Prefix Sum:

```java
sum =
prefix[right]
-
prefix[left-1];
```

---

Complexity:

```text
O(1)
```

after preprocessing.

---

# 16. Kadane's Algorithm

One of the most famous array questions.

---

Question:

```text
Maximum Subarray Sum
```

Input:

```java
{-2,1,-3,4,-1,2,1,-5,4}
```

Output:

```text
6
```

Subarray:

```text
4,-1,2,1
```

---

Program:

```java
int current = arr[0];

int max = arr[0];

for(int i=1;i<arr.length;i++){

    current =
    Math.max(arr[i],
             current + arr[i]);

    max =
    Math.max(max,current);
}
```

---

Complexity:

```text
O(n)
```

---

Interview Favorite:

```text
Maximum Subarray Sum Problem
```

---

# 17. Sliding Window Technique

Important Optimization Technique.

---

Problem:

Find maximum sum of K consecutive elements.

Input:

```java
{1,4,2,10,23,3,1,0,20}
```

K:

```text
4
```

---

Brute Force:

```text
O(n²)
```

---

Sliding Window:

```java
int windowSum = 0;

for(int i=0;i<k;i++){

    windowSum += arr[i];
}

int max = windowSum;

for(int i=k;i<arr.length;i++){

    windowSum += arr[i];

    windowSum -= arr[i-k];

    max =
    Math.max(max, windowSum);
}
```

---

Complexity:

```text
O(n)
```

---

# 18. Common Interview Mistakes

---

## Mistake 1

Using nested loops unnecessarily.

Example:

```text
O(n²)
```

instead of:

```text
O(n)
```

---

## Mistake 2

Not discussing complexity.

Always mention:

```text
Time Complexity

Space Complexity
```

---

## Mistake 3

Using Binary Search on unsorted arrays.

---

## Mistake 4

Not handling edge cases.

Example:

```java
{}
```

Empty array.

---

# 19. Selenium Framework Applications

---

## Browser Execution

```java
String[] browsers =
{
"Chrome",
"Firefox",
"Edge"
};
```

Traversal:

```java
for(String browser : browsers){

}
```

---

## Environment Rotation

```java
String[] envs =
{
"QA",
"UAT",
"PROD"
};
```

Rotate environments dynamically.

---

## Test Data Deduplication

Remove duplicate test users.

---

# 20. API Testing Applications

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

---

## Response Comparison

Use:

```text
Union

Intersection
```

for validating datasets.

---

## Analytics Responses

Prefix Sum concepts often appear in:

```text
Reports

Dashboards

Metrics APIs
```

---

# 21. Interview Questions & Answers

---

## Q1 Complexity of Kadane's Algorithm?

```text
O(n)
```

---

## Q2 Why is Sliding Window better?

Reduces:

```text
O(n²)

to

O(n)
```

---

## Q3 Prefix Sum advantage?

Range query becomes:

```text
O(1)
```

---

## Q4 Best way to remove duplicates?

```text
Two Pointers

(sorted array)
```

---

## Q5 Complexity of Union?

```text
O(n+m)
```

using HashSet.

---

# 22. Short Notes

✔ Move Zeroes → Two Pointers

✔ Remove Duplicates → Two Pointers

✔ Merge Arrays → O(n+m)

✔ Missing Number → Formula

✔ Union → HashSet

✔ Intersection → HashSet

✔ Leaders → Right Traversal

✔ Prefix Sum → O(1) Queries

✔ Kadane → Max Subarray

✔ Sliding Window → Window Optimization

---

# 23. Final Revision Sheet

```text
Move Zeroes
→ Two Pointers

Remove Duplicates
→ Sorted Array + Two Pointers

Missing Number
→ Sum Formula

Union
→ HashSet

Intersection
→ HashSet

Rotation
→ Shift Elements

Leaders
→ Traverse Right to Left

Prefix Sum
→ Range Queries

Kadane
→ Maximum Subarray Sum

Sliding Window
→ Fixed Window Optimization
```

---

# Interview Takeaway

If interviewer asks:

```text
Name important intermediate array algorithms.
```

Answer:

```text
1. Two Pointer Technique
2. Prefix Sum
3. Sliding Window
4. Kadane's Algorithm
5. Union & Intersection
6. Array Rotation
7. Missing Number
8. Leaders in Array

These algorithms appear frequently in Java,
Selenium Automation,
and Product-Based Company Interviews.
```

---

# End of Part 8

## Next Part

### Part 9 – Advanced Array Problems (Product Company Level)

Topics:

* Two Sum
* Three Sum
* Majority Element
* Dutch National Flag Algorithm
* Trapping Rain Water
* Stock Buy & Sell
* Longest Consecutive Sequence
* Maximum Product Subarray
* Merge Intervals
* Advanced Interview Questions
