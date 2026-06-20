# Java String Master Guide

# Part 6 - String Memory Management & JVM Deep Dive

---

# Table of Contents

1. JVM Memory Overview
2. Heap Memory Structure
3. Stack vs Heap vs String Pool
4. String Object Lifecycle
5. Garbage Collection (GC) for Strings
6. Escape Analysis (Important Advanced Topic)
7. String Deduplication
8. Memory Optimization Techniques
9. Hidden Memory Costs of String
10. Intern Pool Behavior in Java 7+
11. Real Framework Memory Problems
12. Performance Bottlenecks
13. Memory Leak Scenarios
14. Interview Tricky Questions
15. Short Notes
16. Revision Sheet

---

# 1. JVM Memory Overview

JVM memory is divided into:

```text id="m1"
JVM Memory

├── Heap Memory
├── Stack Memory
├── Method Area
├── Metaspace
└── String Constant Pool
```

For Strings, most important areas:

* Heap
* Stack
* String Pool

---

# 2. Heap Memory Structure

Heap stores:

* Objects
* Instance variables
* String objects (Java 7+ String Pool also here)

Example:

```java id="m2"
String s = new String("Java");
```

Stored in Heap.

---

# 3. Stack vs Heap vs String Pool

| Area        | Stores          | Example      |
| ----------- | --------------- | ------------ |
| Stack       | References      | s, obj       |
| Heap        | Objects         | new String() |
| String Pool | Reused literals | "Java"       |

---

Memory Flow:

```text id="m3"
Stack → Reference

Heap → Object

Pool → Shared literal
```

---

# 4. String Object Lifecycle

Example:

```java id="m4"
String s = "Java";
```

Steps:

1. Check String Pool
2. If exists → reuse
3. Else → create in Pool
4. Reference stored in Stack

---

# 5. Garbage Collection (GC) for Strings

Example:

```java id="m5"
String s = new String("Java");
s = null;
```

Now:

* Heap object becomes unreachable
* Eligible for GC

---

Important:

```text id="m6"
String Pool objects are rarely GC collected
```

Because they are reused.

---

# 6. GC Behavior Diagram

```text id="m7"
Heap Object:
Java → unreachable → GC

String Pool:
Java → still referenced → NOT GC easily
```

---

# 7. Escape Analysis (Advanced Concept)

JVM optimization:

If object does not escape method → allocated on stack.

Example:

```java id="m8"
public void test() {
    StringBuilder sb = new StringBuilder();
    sb.append("Java");
}
```

JVM may optimize:

```text id="m9"
No heap allocation (in some cases)
```

---

# 8. String Deduplication

Java 8+ feature in G1 GC.

Duplicates are removed.

Example:

```java id="m10"
String a = new String("Java");
String b = new String("Java");
```

After GC:

```text id="m11"
Both point to same char array (optimized)
```

---

# 9. Hidden Memory Cost of String

Each String contains:

* char[]
* metadata
* hash field
* object header

Example:

```java id="m12"
String s = "Automation";
```

Internally:

```text id="m13"
Object + char[] array
```

So String is NOT lightweight.

---

# 10. Intern Pool Behavior (Java 7+)

Before Java 7:

```text id="m14"
PermGen
```

After Java 7:

```text id="m15"
Heap Memory
```

Now String Pool:

* Scalable
* GC managed
* Dynamic

---

# 11. Intern Example

```java id="m16"
String s1 = new String("Java");
String s2 = s1.intern();
String s3 = "Java";
```

Result:

```java id="m17"
s2 == s3 → true
```

Because both point to Pool.

---

# 12. Real Framework Memory Problem

Bad Code:

```java id="m18"
for(int i=0;i<10000;i++){
    String s = new String("TestData");
}
```

Problem:

* 10000 Heap objects
* GC pressure increases

---

Better:

```java id="m19"
String s = "TestData";
for(int i=0;i<10000;i++){
    // reuse same object
}
```

---

# 13. Selenium Memory Issue Example

```java id="m20"
String xpath =
"//input[@id='username']";
```

If created repeatedly:

* Memory waste
* Slower execution

---

Better:

```java id="m21"
final String USER_XPATH =
"//input[@id='username']";
```

---

# 14. API Framework Memory Issue

Bad:

```java id="m22"
String payload = "{name: \"Rahul\"}";
payload += ", age: 25";
```

Problem:

* Multiple objects created

---

Better:

```java id="m23"
StringBuilder payload = new StringBuilder();
payload.append("{name: \"Rahul\", age: 25}");
```

---

# 15. Memory Leak Scenarios

## Scenario 1 - Large String Retention

```java id="m24"
String large = "........ huge data ........";
```

Stored in Pool → never released easily.

---

## Scenario 2 - Static String Reference

```java id="m25"
static String cache = "DATA";
```

Prevents GC.

---

## Scenario 3 - Substring Issue (Old Java)

Before Java 7 update:

```text id="m26"
substring() retained full array
```

Caused memory leaks.

---

# 16. Performance Bottlenecks

Using + operator:

```java id="m27"
String s = "";
for(int i=0;i<1000;i++){
    s += i;
}
```

Problem:

* New object every iteration
* O(n²) complexity

---

Better:

```java id="m28"
StringBuilder sb = new StringBuilder();
for(int i=0;i<1000;i++){
    sb.append(i);
}
```

---

# 17. Stack Memory Role

Stack stores:

* Method calls
* References to objects

Example:

```java id="m29"
String s = "Java";
```

Stack:

```text id="m30"
s → reference
```

Heap:

```text id="m31"
Java object
```

---

# 18. Heap Memory Role

Heap stores:

* Actual String objects
* Arrays inside String

Example:

```java id="m32"
String s = new String("Java");
```

Two objects:

* Heap object
* Pool object

---

# 19. String Optimization Tricks

## Trick 1

Use literals:

```java id="m33"
String s = "Java";
```

---

## Trick 2

Reuse constants:

```java id="m34"
final String URL = "https://site.com";
```

---

## Trick 3

Use StringBuilder in loops:

```java id="m35"
StringBuilder sb = new StringBuilder();
```

---

# 20. Interview Tricky Questions

## Q1 How many objects?

```java id="m36"
String s = new String("Java");
```

Answer:

```text id="m37"
2 objects
```

---

## Q2 Where is String Pool stored?

Java 7+

```text id="m38"
Heap Memory
```

---

## Q3 Why String Pool exists?

```text id="m39"
Memory optimization + reuse
```

---

## Q4 Can String be GCed?

Yes, but rarely from Pool.

---

## Q5 Why String is heavy?

Because of char[] + metadata.

---

## Q6 Why substring caused memory leak?

Old Java versions retained full array.

---

## Q7 Difference between Heap and Stack?

Stack → references
Heap → objects

---

## Q8 What is escape analysis?

JVM optimization for stack allocation.

---

## Q9 Why intern() is used?

To move string to pool.

---

## Q10 Which is best for performance?

StringBuilder

---

# Short Notes

✔ Heap stores objects
✔ Stack stores references
✔ String Pool stores literals
✔ Java 7 moved pool to heap
✔ GC collects heap objects
✔ Pool objects are reused
✔ String is memory heavy
✔ substring() may cause leaks (old JVM)
✔ StringBuilder is fastest
✔ Escape analysis optimizes memory

---

# Revision Sheet

```text id="m40"
Stack → Reference

Heap → Objects

Pool → Shared Strings

GC → Frees Heap

intern() → Moves to Pool

StringBuilder → Fast

StringBuffer → Thread-safe

String → Immutable + Heavy
```

---

# Interview Rapid Revision

Must Remember:

* String is immutable
* String Pool reduces memory
* Heap stores objects
* Stack stores references
* StringBuilder is fastest
* StringBuffer is thread-safe
* Escape analysis improves performance
* GC cleans heap objects only

---

# Part 6 Completed

Next Part:

Part 7 - String Coding Problems (Basic Level)

Topics:

* Reverse string
* Palindrome check
* Count characters
* Remove duplicates
* Frequency count
* First non-repeating character
* String swap logic
* Interview coding patterns
* Selenium + API coding usage
