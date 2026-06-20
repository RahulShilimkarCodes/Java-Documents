# Java String Master Guide

# Part 2 - String Creation Internals & JVM Memory Deep Dive

---

# Table of Contents

1. String Object Creation Process
2. Literal vs new String()
3. JVM Memory Architecture
4. Heap Memory Internals
5. String Constant Pool Internals
6. Object Creation Walkthrough
7. Duplicate String Handling
8. String Interning Deep Dive
9. Java 6 vs Java 7 vs Java 8+
10. Garbage Collection and Strings
11. Memory Diagrams
12. Real Project Examples
13. Interview Questions
14. Short Notes
15. Revision Sheet

---

# 1. String Object Creation Process

Whenever Java encounters:

```java
String s = "Java";
```

it performs several checks before creating the object.

Steps:

1. Check SCP (String Constant Pool)
2. If String exists:

   * Reuse existing object
3. If String doesn't exist:

   * Create object in SCP
4. Reference variable points to SCP object

Example:

```java
String s1 = "Java";
String s2 = "Java";
```

Memory:

```text
SCP

+------+
| Java |
+------+

s1 -----+
         |
s2 -----+
```

Only one object created.

---

# 2. Literal vs new String()

## Using Literal

```java
String s = "Java";
```

Advantages:

* Memory efficient
* Faster lookup
* Reuses existing object

---

## Using new

```java
String s = new String("Java");
```

Creates:

1. SCP object (if absent)
2. Heap object

Memory:

```text
SCP

Java

Heap

Java
```

Two objects may exist.

---

# 3. Detailed Object Creation

Code:

```java
String s = new String("Java");
```

Step 1

Check SCP.

```text
Java present?
```

If absent:

```text
Create in SCP
```

Step 2

Create new Heap object.

Step 3

Reference variable points to Heap object.

Memory:

```text
SCP

+------+
| Java |
+------+

Heap

+------+
| Java |
+------+
   ^
   |
   s
```

---

# 4. JVM Memory Architecture

Important areas:

```text
JVM Memory

├── Heap
├── Stack
├── Method Area
├── Metaspace
└── String Pool
```

For Strings, focus on:

```text
Heap
String Pool
Stack
```

---

# 5. Stack vs Heap

Example:

```java
String s = "Java";
```

Stack:

```text
s
```

contains reference.

Heap/SCP:

```text
Java object
```

Actual object stored here.

Diagram:

```text
Stack

s
|
v

SCP

Java
```

---

# 6. Multiple Literal Example

```java
String a = "Java";
String b = "Java";
String c = "Java";
```

Memory:

```text
SCP

+------+
| Java |
+------+

a -----+
b -----+
c -----+
```

Only one object.

---

# 7. Multiple new Example

```java
String a = new String("Java");
String b = new String("Java");
```

Memory:

```text
SCP

Java

Heap

Java  (a)

Java  (b)
```

Three total objects.

---

# 8. String Pool Optimization

Without SCP:

```java
1000 users
```

Each having:

```java
"India"
```

would create:

```text
1000 objects
```

With SCP:

```text
1 object
```

Huge memory savings.

---

# 9. Why SCP Exists

Main goals:

### Reduce Memory

Duplicate literals avoided.

### Improve Performance

Fast object reuse.

### Faster Equality Checks

Reference comparison possible.

---

# 10. String Interning

Method:

```java
intern()
```

Purpose:

Move/reference String inside SCP.

Example:

```java
String s1 = new String("Java");

String s2 = s1.intern();
```

Memory:

```text
SCP

Java

Heap

Java
```

s2 points to SCP object.

---

# 11. Intern Example

```java
String s1 = new String("Java");
String s2 = "Java";

System.out.println(s1 == s2);
```

Output:

```text
false
```

Different objects.

Now:

```java
String s3 = s1.intern();

System.out.println(s3 == s2);
```

Output:

```text
true
```

Same SCP object.

---

# 12. Java Version Difference

## Java 6

String Pool stored in:

```text
PermGen
```

Issues:

* Limited size
* OutOfMemoryError

---

## Java 7

String Pool moved to:

```text
Heap Memory
```

Advantages:

* Better GC
* Dynamic growth

---

## Java 8+

PermGen removed.

Introduced:

```text
Metaspace
```

String Pool remains in Heap.

---

# 13. Garbage Collection with Strings

Example:

```java
String s = new String("Java");

s = null;
```

Heap object becomes:

```text
Eligible for GC
```

---

Literal object in SCP:

```java
"Java"
```

may remain for reuse.

---

# 14. Unused String Example

```java
new String("Selenium");
```

No reference.

Immediately becomes:

```text
Eligible for GC
```

Heap object only.

---

# 15. Real Memory Scenario

```java
String s1 = "Java";
String s2 = new String("Java");
String s3 = s2.intern();
```

Question:

How many objects?

Answer:

```text
SCP -> Java

Heap -> Java

Total = 2 Objects
```

---

# 16. Tricky Interview Example

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

Output:

```text
true
```

Because SCP reused.

---

Example:

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
```

Output:

```text
false
```

Different Heap objects.

---

# 17. Project-Level Example

Environment Configuration

```java
String env = "QA";
String role = "ADMIN";
```

Used thousands of times.

Because of SCP:

```text
Only one object per unique value.
```

Memory efficient.

---

# 18. Selenium Framework Example

```java
String browser = "Chrome";
```

Across hundreds of tests:

```java
if(browser == "Chrome")
```

May appear to work but is dangerous.

Correct:

```java
if(browser.equals("Chrome"))
```

Interviewers frequently ask this.

---

# 19. API Testing Example

```java
String token = response
        .jsonPath()
        .getString("token");
```

Returned value comes from Heap.

Comparisons should use:

```java
equals()
```

not

```java
==
```

---

# 20. Common Interview Questions

## Q1 Why String Pool was created?

To avoid duplicate String objects and reduce memory consumption.

---

## Q2 Where is String Pool stored?

Java 7+

```text
Heap Memory
```

---

## Q3 Difference between Literal and new String()?

Literal:

```text
Uses SCP
```

new:

```text
Creates Heap Object
```

---

## Q4 What does intern() do?

Returns SCP reference.

---

## Q5 How many objects?

```java
String s = new String("Java");
```

Answer:

Usually 2.

---

## Q6 Why String literals are faster?

Object reuse through SCP.

---

## Q7 Can String Pool objects be garbage collected?

Yes, when no longer strongly reachable and JVM determines they are reclaimable.

---

## Q8 Why is String memory efficient?

Because duplicate literals share same object.

---

## Q9 Where is reference stored?

```text
Stack Memory
```

---

## Q10 Where is actual String object stored?

```text
Heap/SCP
```

---

# Short Notes

✔ Literal → SCP

✔ new String() → Heap

✔ SCP avoids duplicates

✔ intern() returns SCP object

✔ Java 7 moved SCP into Heap

✔ String references stored in Stack

✔ Actual objects stored in Heap

✔ Heap objects eligible for GC

✔ String Pool improves performance

✔ String Pool reduces memory usage

---

# Revision Sheet

Remember:

```text
Literal
↓
SCP

new String()
↓
Heap

intern()
↓
Returns SCP Reference

Java 6
↓
PermGen

Java 7+
↓
Heap

Java 8+
↓
Metaspace + Heap Pool
```

---

# Part 2 Completed

Next Part:

Part 3 - String Methods Deep Dive

Topics:

* length()
* charAt()
* substring()
* indexOf()
* contains()
* startsWith()
* endsWith()
* replace()
* split()
* trim()
* strip()
* join()
* repeat()
* matches()
* compareTo()
* equalsIgnoreCase()
* 50+ Method-Based Interview Questions
* Selenium & API Testing Examples
* Performance Considerations
* Java 8 to Java 21 Updates
