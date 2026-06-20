# Java String Master Guide

# Part 5 - StringBuilder & StringBuffer Deep Dive

---

# Table of Contents

1. Why StringBuilder & StringBuffer exist
2. Mutable vs Immutable Strings
3. StringBuilder Overview
4. StringBuffer Overview
5. Difference: String vs StringBuilder vs StringBuffer
6. append()
7. insert()
8. delete()
9. reverse()
10. replace()
11. capacity() vs length()
12. Performance Comparison
13. Thread Safety Concept
14. Memory Behavior
15. Real Project Examples (Selenium & API)
16. Common Interview Questions
17. Tricky Programs
18. Short Notes
19. Revision Sheet

---

# 1. Why StringBuilder & StringBuffer Exist

String is immutable:

```java
String s = "Java";
s.concat(" Selenium");
```

This creates a new object every time → poor performance in loops.

Problem:

```text
High memory usage + slow execution
```

Solution:

* StringBuilder (fast, non-thread-safe)
* StringBuffer (slower, thread-safe)

---

# 2. Mutable vs Immutable

| Type          | Mutable? | Example                    |
| ------------- | -------- | -------------------------- |
| String        | ❌ No     | String s = "Java"          |
| StringBuilder | ✅ Yes    | append changes same object |
| StringBuffer  | ✅ Yes    | synchronized modifications |

---

# 3. StringBuilder Overview

Used for:

* Fast string manipulation
* Single-threaded applications
* Performance-critical code

Example:

```java
StringBuilder sb = new StringBuilder("Java");
sb.append(" Selenium");
System.out.println(sb);
```

Output:

```
Java Selenium
```

---

# 4. StringBuffer Overview

Used for:

* Thread-safe string operations
* Multi-threaded environments

Example:

```java
StringBuffer sb = new StringBuffer("Java");
sb.append(" Selenium");
System.out.println(sb);
```

Output:

```
Java Selenium
```

---

# 5. String vs StringBuilder vs StringBuffer

| Feature       | String                 | StringBuilder | StringBuffer        |
| ------------- | ---------------------- | ------------- | ------------------- |
| Mutability    | Immutable              | Mutable       | Mutable             |
| Thread Safety | Yes                    | No            | Yes                 |
| Performance   | Slow                   | Fast          | Medium              |
| Memory        | High (objects created) | Low           | Medium              |
| Usage         | Fixed text             | Dynamic text  | Multi-threaded apps |

---

# 6. append()

Adds text at end.

```java
StringBuilder sb = new StringBuilder("Java");
sb.append(" Selenium");
System.out.println(sb);
```

Output:

```
Java Selenium
```

---

# 7. insert()

Inserts text at position.

```java
StringBuilder sb = new StringBuilder("Java");
sb.insert(4, " Selenium");
System.out.println(sb);
```

Output:

```
Java Selenium
```

---

# 8. delete()

Deletes part of string.

```java
StringBuilder sb = new StringBuilder("Java Selenium");
sb.delete(4, 12);
System.out.println(sb);
```

Output:

```
Java
```

---

# 9. reverse()

Reverses string.

```java
StringBuilder sb = new StringBuilder("Java");
sb.reverse();
System.out.println(sb);
```

Output:

```
avaJ
```

---

# 10. replace()

Replaces part of string.

```java
StringBuilder sb = new StringBuilder("Java Selenium");
sb.replace(0, 4, "Playwright");
System.out.println(sb);
```

Output:

```
Playwright Selenium
```

---

# 11. capacity() vs length()

## length()

Actual characters:

```java
StringBuilder sb = new StringBuilder("Java");
System.out.println(sb.length());
```

Output:

```
4
```

---

## capacity()

Internal buffer size:

```java
System.out.println(sb.capacity());
```

Default formula:

```
16 + initial string length
```

---

# 12. Performance Comparison

Example loop:

```java
String s = "";
for(int i=0; i<1000; i++){
    s += i;
}
```

Slow because:

* new object created each iteration

---

Better:

```java
StringBuilder sb = new StringBuilder();
for(int i=0; i<1000; i++){
    sb.append(i);
}
```

Fast and memory efficient.

---

# 13. Thread Safety Concept

| Class         | Thread Safe |
| ------------- | ----------- |
| StringBuilder | ❌ No        |
| StringBuffer  | ✅ Yes       |

Reason:

StringBuffer methods are synchronized.

Example:

```java
public synchronized StringBuffer append(...)
```

---

# 14. Memory Behavior

## String (Bad for loops)

```
Each modification → new object
```

## StringBuilder

```
Single object reused
```

---

Diagram:

```
String:
Java → Java1 → Java2 → Java3 (new objects)

StringBuilder:
Java → Java123 (same object)
```

---

# 15. Real Project Usage

## Selenium Logging

```java
StringBuilder log = new StringBuilder();
log.append("Test Started");
log.append(" -> Login Passed");
log.append(" -> Test Ended");
```

---

## API Request Builder

```java
StringBuilder payload = new StringBuilder();
payload.append("{");
payload.append("\"name\":\"Rahul\"");
payload.append("}");
```

---

## Report Generation

```java
StringBuffer report = new StringBuffer();
report.append("Step 1 Passed\n");
report.append("Step 2 Passed\n");
```

---

# 16. Common Interview Questions

## Q1 Why StringBuilder is faster than String?

Because it modifies same object.

---

## Q2 Difference between StringBuffer and StringBuilder?

Thread safety vs performance.

---

## Q3 Why String is immutable?

Security + caching + thread safety.

---

## Q4 When to use StringBuilder?

Single-threaded applications.

---

## Q5 When to use StringBuffer?

Multi-threaded environments.

---

## Q6 What is default capacity?

```
16 + length
```

---

## Q7 What happens when capacity exceeds?

New array created internally (resizing).

---

## Q8 Is StringBuilder synchronized?

No.

---

## Q9 Is StringBuffer synchronized?

Yes.

---

## Q10 Which is used in frameworks?

Mostly StringBuilder.

---

# 17. Tricky Interview Programs

## Program 1

```java
StringBuilder sb = new StringBuilder("Java");
sb.append("Java");
System.out.println(sb);
```

Output:

```
JavaJava
```

---

## Program 2

```java
String s = "Java";
s.concat("Java");
System.out.println(s);
```

Output:

```
Java
```

---

## Program 3

```java
StringBuilder sb = new StringBuilder("A");
sb.append("B").append("C");
System.out.println(sb);
```

Output:

```
ABC
```

---

## Program 4

```java
StringBuilder sb1 = new StringBuilder("Java");
StringBuilder sb2 = sb1;

sb2.append(" Selenium");

System.out.println(sb1);
```

Output:

```
Java Selenium
```

Same object reference.

---

# 18. Short Notes

✔ String is immutable

✔ StringBuilder is mutable

✔ StringBuffer is thread-safe

✔ StringBuilder is faster

✔ StringBuffer is synchronized

✔ append() modifies same object

✔ insert() adds at index

✔ delete() removes characters

✔ reverse() reverses string

✔ capacity() is internal buffer size

✔ length() is actual size

---

# 19. Revision Sheet

```
String → Immutable → Slow in loops

StringBuilder → Mutable → Fast → Not thread-safe

StringBuffer → Mutable → Slower → Thread-safe
```

---

# Interview Quick Summary

* Use String for fixed values
* Use StringBuilder for performance
* Use StringBuffer for multithreading
* Avoid + operator in loops
* Prefer append() for efficiency

---

# Part 5 Completed

Next Part:

Part 6 - String Memory Management & JVM Deep Dive

Topics:

* Heap deep structure
* Stack vs Heap vs SCP interaction
* GC behavior with Strings
* Escape analysis
* String optimization tricks
* Real-time framework memory issues
* Interview diagrams
* 30+ advanced questions
