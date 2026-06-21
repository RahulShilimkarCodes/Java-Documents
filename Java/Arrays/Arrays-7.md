# Java Arrays Master Guide

# Part 7 - Basic Array Coding Problems (Interview Preparation)

---

# Table of Contents

1. Introduction
2. How Interviewers Evaluate Array Problems
3. Find Largest Element
4. Find Smallest Element
5. Sum of Array Elements
6. Average of Array Elements
7. Count Even and Odd Numbers
8. Count Positive and Negative Numbers
9. Reverse an Array
10. Copy an Array
11. Linear Search
12. Find Frequency of an Element
13. Count Duplicate Elements
14. Find Second Largest Element
15. Find Second Smallest Element
16. Common Interview Mistakes
17. Selenium & Automation Use Cases
18. API Testing Use Cases
19. Interview Questions & Answers
20. Short Notes
21. Final Revision Sheet

---

# 1. Introduction

These are the most frequently asked array coding questions in:

* Java Interviews
* Selenium Interviews
* Automation Testing Interviews
* Product-Based Company Interviews

Before solving advanced problems, every developer should master these basics.

---

# 2. How Interviewers Evaluate Array Problems

Interviewers usually check:

```text
✔ Loop Knowledge

✔ Array Traversal

✔ Index Handling

✔ Logic Building

✔ Time Complexity Understanding
```

Important Rule:

```text
Most basic array problems are solved using a single traversal.
```

Complexity:

```text
O(n)
```

---

# 3. Find Largest Element

Question:

```text
Find the largest number in an array.
```

Input:

```java
int[] arr = {10,50,20,90,30};
```

Output:

```text
90
```

---

## Logic

Assume first element is largest.

Compare with remaining elements.

---

## Program

```java
int[] arr = {10,50,20,90,30};

int max = arr[0];

for(int i=1;i<arr.length;i++){

    if(arr[i] > max){

        max = arr[i];
    }
}

System.out.println(max);
```

---

## Complexity

```text
O(n)
```

---

## Interview Tip

Always initialize:

```java
int max = arr[0];
```

Avoid:

```java
int max = 0;
```

because array may contain negative numbers.

---

# 4. Find Smallest Element

Input:

```java
int[] arr = {10,50,20,90,30};
```

Output:

```text
10
```

---

## Program

```java
int min = arr[0];

for(int i=1;i<arr.length;i++){

    if(arr[i] < min){

        min = arr[i];
    }
}

System.out.println(min);
```

---

## Complexity

```text
O(n)
```

---

# 5. Sum of Array Elements

Question:

```text
Find sum of all elements.
```

Input:

```java
{10,20,30,40}
```

Output:

```text
100
```

---

## Program

```java
int sum = 0;

for(int num : arr){

    sum += num;
}

System.out.println(sum);
```

---

## Complexity

```text
O(n)
```

---

# 6. Average of Array Elements

Formula:

```text
Average = Sum / Number of Elements
```

---

## Program

```java
int sum = 0;

for(int num : arr){

    sum += num;
}

double avg =
(double)sum / arr.length;

System.out.println(avg);
```

---

Output:

```text
25.0
```

---

Interview Tip:

Always use:

```java
(double)
```

to avoid integer division.

---

# 7. Count Even and Odd Numbers

Input:

```java
{10,15,20,25,30}
```

Output:

```text
Even = 3

Odd = 2
```

---

## Program

```java
int even = 0;
int odd = 0;

for(int num : arr){

    if(num % 2 == 0){

        even++;
    }
    else{

        odd++;
    }
}

System.out.println(even);
System.out.println(odd);
```

---

## Complexity

```text
O(n)
```

---

# 8. Count Positive and Negative Numbers

Input:

```java
{-10,20,-30,40,50}
```

Output:

```text
Positive = 3

Negative = 2
```

---

## Program

```java
int positive = 0;
int negative = 0;

for(int num : arr){

    if(num >= 0){

        positive++;
    }
    else{

        negative++;
    }
}
```

---

Interview Question:

What about zero?

Answer:

```text
Depends on business requirement.
```

Most programs treat:

```text
0 as positive.
```

---

# 9. Reverse an Array

Input:

```text
10 20 30 40
```

Output:

```text
40 30 20 10
```

---

## Method 1

Reverse Traversal

```java
for(int i=arr.length-1;i>=0;i--){

    System.out.print(arr[i]+" ");
}
```

---

## Method 2

Actual Reversal

```java
int left = 0;

int right = arr.length-1;

while(left < right){

    int temp = arr[left];

    arr[left] = arr[right];

    arr[right] = temp;

    left++;
    right--;
}
```

---

Complexity:

```text
O(n)
```

---

# 10. Copy an Array

Question:

Create duplicate array.

---

## Program

```java
int[] copy =
new int[arr.length];

for(int i=0;i<arr.length;i++){

    copy[i] = arr[i];
}
```

---

Output:

```text
Copy Created
```

---

Alternative:

```java
int[] copy = arr.clone();
```

---

# 11. Linear Search

Question:

Find element position.

Input:

```java
{10,20,30,40,50}
```

Find:

```text
40
```

Output:

```text
Index = 3
```

---

## Program

```java
int target = 40;

for(int i=0;i<arr.length;i++){

    if(arr[i] == target){

        System.out.println(i);

        break;
    }
}
```

---

Complexity:

```text
O(n)
```

---

# 12. Find Frequency of an Element

Input:

```java
{10,20,10,30,10}
```

Find frequency of:

```text
10
```

Output:

```text
3
```

---

## Program

```java
int count = 0;

for(int num : arr){

    if(num == 10){

        count++;
    }
}

System.out.println(count);
```

---

# 13. Count Duplicate Elements

Input:

```java
{10,20,10,30,20}
```

Duplicates:

```text
10

20
```

---

Basic Approach:

Nested Loop

```java
for(int i=0;i<arr.length;i++){

    for(int j=i+1;j<arr.length;j++){

        if(arr[i] == arr[j]){

            System.out.println(arr[i]);
        }
    }
}
```

---

Complexity:

```text
O(n²)
```

---

# 14. Find Second Largest Element

Very Common Interview Question.

Input:

```java
{10,90,20,70}
```

Output:

```text
70
```

---

## Program

```java
int largest = Integer.MIN_VALUE;

int second = Integer.MIN_VALUE;

for(int num : arr){

    if(num > largest){

        second = largest;

        largest = num;
    }

    else if(num > second &&
            num != largest){

        second = num;
    }
}

System.out.println(second);
```

---

Complexity:

```text
O(n)
```

---

# 15. Find Second Smallest Element

Input:

```java
{10,90,20,70}
```

Output:

```text
20
```

---

## Program

```java
int smallest =
Integer.MAX_VALUE;

int second =
Integer.MAX_VALUE;

for(int num : arr){

    if(num < smallest){

        second = smallest;

        smallest = num;
    }

    else if(num < second &&
            num != smallest){

        second = num;
    }
}
```

---

Complexity:

```text
O(n)
```

---

# 16. Common Interview Mistakes

---

## Mistake 1

```java
int max = 0;
```

Fails for:

```java
{-10,-20,-5}
```

---

Correct:

```java
int max = arr[0];
```

---

## Mistake 2

Forgetting:

```java
break;
```

after search result found.

---

## Mistake 3

Using:

```java
i <= arr.length
```

instead of:

```java
i < arr.length
```

---

## Mistake 4

Not handling empty arrays.

---

# 17. Selenium & Automation Use Cases

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

Find specific browser:

```java
for(String browser : browsers){

    if(browser.equals("Chrome")){

        System.out.println("Found");
    }
}
```

---

## Test Data Validation

```java
String[] users =
{
"user1",
"user2",
"user3"
};
```

Search user:

```java
for(String user : users){

    if(user.equals("user2")){

        System.out.println("Exists");
    }
}
```

---

# 18. API Testing Use Cases

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

Search endpoint.

---

## Response Data Verification

```java
int[] ids =
{
101,
102,
103
};
```

Verify:

```text
Expected ID exists
```

---

# 19. Interview Questions & Answers

---

## Q1 Largest element complexity?

```text
O(n)
```

---

## Q2 Smallest element complexity?

```text
O(n)
```

---

## Q3 Search complexity?

Linear Search:

```text
O(n)
```

---

## Q4 Reverse complexity?

```text
O(n)
```

---

## Q5 Why use Integer.MIN_VALUE?

For safe comparison.

---

## Q6 Difference between reverse traversal and reverse array?

Reverse Traversal:

```text
Print in reverse order
```

Reverse Array:

```text
Modify actual array
```

---

# 20. Short Notes

✔ Largest Element → O(n)

✔ Smallest Element → O(n)

✔ Sum → O(n)

✔ Average → O(n)

✔ Search → O(n)

✔ Reverse → O(n)

✔ Frequency Count → O(n)

✔ Duplicate Detection → O(n²)

---

# 21. Final Revision Sheet

```text
Largest Element
→ max

Smallest Element
→ min

Sum
→ accumulator

Average
→ sum / length

Even
→ num % 2 == 0

Odd
→ num % 2 != 0

Reverse
→ Two Pointers

Search
→ Linear Search

Frequency
→ Counter

Second Largest
→ largest + second

Second Smallest
→ smallest + second
```

---

# Interview Takeaway

If interviewer asks:

```text
What are the most important beginner array problems?
```

Answer:

```text
The most important beginner array problems are:

1. Largest Element
2. Smallest Element
3. Sum
4. Average
5. Search
6. Reverse Array
7. Frequency Count
8. Duplicate Detection
9. Second Largest
10. Second Smallest

These problems test traversal,
conditions,
loops,
and complexity analysis.
```

---

# End of Part 7

## Next Part

### Part 8 – Intermediate Array Coding Problems

Topics:

* Move Zeroes to End
* Remove Duplicates
* Merge Arrays
* Missing Number
* Union & Intersection
* Array Rotation
* Leaders in Array
* Kadane's Algorithm
* Prefix Sum
* Sliding Window Basics
