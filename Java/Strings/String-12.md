# Java String Master Guide

# Part 12 - FINAL REVISION (Interview Cheat Sheet)

---

# 1. Core Concept Revision (Must Remember)

## String Basics

```text id="r1"
String = Immutable object
Stored in String Constant Pool (SCP)
```

* Any modification → new object created
* Stored in Heap (Java 7+ SCP is part of Heap)

---

## Memory Model

```text id="r2"
Stack → Reference variables
Heap → Objects
SCP → Reused string literals
```

---

# 2. String Creation Types

```java id="r3"
String s1 = "Java";              // SCP
String s2 = new String("Java");  // Heap
```

---

# 3. Most Important Difference Table

| Concept            | Meaning                     |
| ------------------ | --------------------------- |
| ==                 | Reference comparison        |
| equals()           | Content comparison          |
| equalsIgnoreCase() | Case-insensitive comparison |
| compareTo()        | Lexicographical comparison  |

---

# 4. String Pool Rules

```text id="r4"
- String literals go to SCP
- SCP avoids duplicate objects
- intern() forces pooling
```

Example:

```java id="r5"
String s1 = new String("Java");
String s2 = s1.intern();
```

---

# 5. Frequently Used Methods

## Basic Methods

```text id="r6"
length()
charAt()
substring()
indexOf()
lastIndexOf()
```

## Validation Methods

```text id="r7"
contains()
startsWith()
endsWith()
equals()
equalsIgnoreCase()
```

## Transformation Methods

```text id="r8"
replace()
replaceAll()
toUpperCase()
toLowerCase()
trim()
strip()
```

---

# 6. Java 11 Important Methods

```text id="r9"
isBlank()
strip()
repeat()
```

---

# 7. StringBuilder vs StringBuffer

| Feature       | StringBuilder | StringBuffer |
| ------------- | ------------- | ------------ |
| Speed         | Fast          | Slow         |
| Thread Safety | No            | Yes          |
| Usage         | Single-thread | Multi-thread |

---

# 8. Most Important Coding Patterns

## Reverse String

```java id="r10"
StringBuilder sb = new StringBuilder("Java");
sb.reverse();
```

---

## Palindrome

```text id="r11"
original == reverse
```

---

## Frequency Count

```text id="r12"
Use loop + counter OR HashMap
```

---

## Remove Duplicates

```text id="r13"
Use Set OR indexOf check
```

---

## First Non-Repeating

```text id="r14"
indexOf(c) == lastIndexOf(c)
```

---

# 9. Common Interview Traps

## Trap 1

```java id="r15"
String s = "Java";
s.concat("Test");
System.out.println(s);
```

Output:

```text id="r16"
Java
```

---

## Trap 2

```java id="r17"
String s1 = "Java";
String s2 = "Java";
System.out.println(s1 == s2);
```

Output:

```text id="r18"
true (SCP)
```

---

## Trap 3

```java id="r19"
String s1 = new String("Java");
String s2 = new String("Java");
System.out.println(s1 == s2);
```

Output:

```text id="r20"
false
```

---

# 10. Performance Rules (VERY IMPORTANT)

```text id="r21"
❌ Avoid + in loops
❌ Avoid new String()
❌ Avoid substring in heavy loops
```

```text id="r22"
✔ Use StringBuilder
✔ Use String constants
✔ Use equals() safely
```

---

# 11. Null Safety Rule

```java id="r23"
"Java".equals(variable)
```

✔ Prevents NullPointerException

---

# 12. Selenium Usage Revision

```text id="r24"
equals() → Assertions
contains() → URL validation
startsWith() → environment checks
trim() → text cleanup
```

---

# 13. API Testing Usage

```text id="r25"
equalsIgnoreCase() → status validation
contains() → response checks
jsonPath() + String → extraction
```

---

# 14. JVM Memory Quick View

```text id="r26"
Heap → Objects
Stack → References
SCP → String literals
GC → Clears heap objects
```

---

# 15. Most Asked Interview Questions

## Q1 Why String is immutable?

* Security
* Thread safety
* Caching

---

## Q2 Difference between == and equals?

* == → reference
* equals → content

---

## Q3 Why StringBuilder is faster?

No new object creation.

---

## Q4 Why StringBuffer is thread-safe?

Synchronized methods.

---

## Q5 What is String pool?

Memory optimization area for reuse.

---

## Q6 What is intern()?

Moves string to SCP.

---

## Q7 Why substring was risky?

Old JVM shared char arrays.

---

## Q8 Why + is slow in loops?

Creates multiple intermediate objects.

---

## Q9 When to use StringBuilder?

Dynamic string manipulation.

---

## Q10 When to use StringBuffer?

Multi-threaded environments.

---

# 16. FINAL ONE-LINE REVISION

```text id="r27"
String = Immutable + SCP + Memory Optimized
```

```text id="r28"
StringBuilder = Fast + Mutable + No Sync
```

```text id="r29"
StringBuffer = Safe + Slow + Sync
```

---

# 17. FINAL INTERVIEW CHEAT SHEET

✔ String = most important Java topic
✔ Used in Selenium + API + Backend
✔ Always prefer equals()
✔ Avoid == for content comparison
✔ Use StringBuilder for performance
✔ Understand memory model
✔ Know SCP behavior
✔ Master coding patterns

---

# END OF JAVA STRING MASTER GUIDE SERIES

---

## If you want next upgrade:

I can also create:

✔ 200+ Java coding interview questions
✔ Selenium framework using String concepts
✔ Real-time automation architecture
✔ Mock interview Q&A set
✔ Full PDF book version

Just tell me 👍
