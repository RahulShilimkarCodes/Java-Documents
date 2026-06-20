# Java Variables Interview Master Guide
# Part 10 - Ultimate Quick Revision Handbook

## Table of Contents

1. Complete Variables Summary
2. JVM Memory Cheat Sheet
3. Stack vs Heap Comparison
4. Primitive vs Reference Summary
5. String Revision Notes
6. Pass By Value Summary
7. Multithreading Variables Summary
8. Framework Design Summary
9. Top 50 One-Liner Interview Answers
10. 100 Rapid Fire MCQs
11. Last Minute Revision Notes

---

# 1. Complete Variables Summary

## Local Variable

- Declared inside method/block
- Stored in Stack
- No default value
- Short lifetime

Example:

```java
void test() {
    int age = 25;
}
```

---

## Instance Variable

- Declared inside class
- Stored in Heap
- Gets default value
- One copy per object

---

## Static Variable

- Class-level variable
- Shared across objects
- Stored in Metaspace

---

## Final Variable

- Constant
- Cannot be reassigned

Example:

```java
final int MAX = 100;
```

---

# 2. JVM Memory Cheat Sheet

```text
JVM
│
├── Stack
├── Heap
├── Metaspace
├── PC Register
└── Native Stack
```

---

## Stack

Stores:

- Local Variables
- Method Calls
- References

---

## Heap

Stores:

- Objects
- Arrays
- Instance Variables

---

## Metaspace

Stores:

- Class Metadata
- Static Members

---

# 3. Stack vs Heap Comparison

| Stack | Heap |
|---------|---------|
| Faster | Slower |
| Thread Specific | Shared |
| Local Variables | Objects |
| Auto Cleanup | GC Cleanup |

---

# 4. Primitive vs Reference Summary

## Primitive

```java
int age = 25;
```

Stores actual value.

---

## Reference

```java
Employee emp =
new Employee();
```

Stores memory address.

---

## Quick Difference

Primitive = Value

Reference = Address

---

# 5. String Revision Notes

## Immutable

```java
String str = "Java";
```

Cannot change after creation.

---

## String Pool

Stores string literals.

```java
String a = "Java";
String b = "Java";
```

Same pool object.

---

## StringBuilder

Fast

Not Thread Safe

---

## StringBuffer

Thread Safe

Slightly slower

---

# 6. Pass By Value Summary

Most Important Interview Concept

Java is ALWAYS Pass By Value.

---

Primitive

```java
modify(age);
```

Value copied.

---

Object

```java
modify(emp);
```

Reference copied.

---

Remember

Object is NOT passed.

Reference value is passed.

---

# 7. Multithreading Variables Summary

## volatile

Visibility only.

---

## synchronized

Visibility + Atomicity.

---

## AtomicInteger

Thread-safe increment.

---

## ThreadLocal

Thread-specific variable storage.

Example:

```java
ThreadLocal<WebDriver>
driver;
```

---

# 8. Framework Design Summary

## Driver Management

Best Practice:

```java
ThreadLocal<WebDriver>
driver;
```

---

## Constants

```java
public static final String URL;
```

---

## Configuration

```java
Properties prop;
```

---

## Dependency Injection

```java
this.driver = driver;
```

---

## Singleton

Single object instance.

---

# 9. Top 50 One-Liner Interview Answers

1. Variable stores data.
2. Local variables are stored in Stack.
3. Objects are stored in Heap.
4. References are stored in Stack.
5. Instance variables belong to objects.
6. Static variables belong to class.
7. Final variables cannot be reassigned.
8. String is immutable.
9. String literals are stored in String Pool.
10. Java is case-sensitive.
11. Local variables need initialization.
12. Instance variables get default values.
13. Stack is thread-specific.
14. Heap is shared memory.
15. Metaspace stores class metadata.
16. Java is always Pass By Value.
17. Objects are not passed directly.
18. Reference values are copied.
19. volatile provides visibility.
20. synchronized provides atomicity.
21. Race condition occurs with shared variables.
22. AtomicInteger is thread-safe.
23. ThreadLocal provides isolated storage.
24. StringBuilder is faster.
25. StringBuffer is thread-safe.
26. == compares addresses.
27. equals() compares content.
28. Shallow copy shares objects.
29. Deep copy creates new objects.
30. GC removes unreachable objects.
31. Eligible for GC != immediately collected.
32. StackOverflowError comes from recursion.
33. OutOfMemoryError comes from heap exhaustion.
34. HashMap is not thread-safe.
35. ConcurrentHashMap is thread-safe.
36. this refers current object.
37. super refers parent object.
38. Shadowing hides instance variable.
39. Hiding hides parent variable.
40. Constructor injection supports loose coupling.
41. Singleton creates one instance.
42. ConfigReader externalizes configuration.
43. Constants reduce duplication.
44. DriverFactory centralizes browser management.
45. ThreadLocal is best for Selenium parallel execution.
46. Browser represents browser process.
47. Page represents browser tab.
48. RequestSpecification stores API setup.
49. Response stores API response.
50. Static WebDriver is unsafe in parallel execution.

---

# 10. 100 Rapid Fire MCQs

Q1. Local variable stored in?

A. Heap
B. Stack

Answer: B

Q2. Objects stored in?

Answer: Heap

Q3. Static variables belong to?

Answer: Class

Q4. String is?

Answer: Immutable

Q5. Java supports?

Answer: Pass By Value

Q6. volatile provides?

Answer: Visibility

Q7. synchronized provides?

Answer: Visibility + Atomicity

Q8. ThreadLocal used for?

Answer: Thread-specific storage

Q9. equals() compares?

Answer: Content

Q10. == compares?

Answer: Address

Q11. Wrapper of int?

Answer: Integer

Q12. Wrapper of double?

Answer: Double

Q13. StringBuilder thread safe?

Answer: No

Q14. StringBuffer thread safe?

Answer: Yes

Q15. StackOverflowError caused by?

Answer: Recursion

Q16. OutOfMemoryError caused by?

Answer: Heap Full

Q17. Best Selenium driver design?

Answer: ThreadLocal Driver

Q18. Static WebDriver safe in parallel?

Answer: No

Q19. Config values stored in?

Answer: Properties

Q20. Constant keyword?

Answer: final

(Continue revising similarly up to 100. Use these as rapid recall prompts.)

---

# Last Minute Revision Notes

### Memory

Local Variable → Stack

Object → Heap

Static Variable → Metaspace

Reference → Stack

---

### String

Immutable

Pool Optimized

---

### Pass By Value

Always

Even for objects.

---

### Multithreading

volatile → Visibility

synchronized → Visibility + Atomicity

ThreadLocal → Thread Isolation

---

### Framework Design

Driver → ThreadLocal

Config → Properties

Constants → static final

Dependency Injection → Constructor

Singleton → One Instance

---

# FINAL INTERVIEW CRACK SHEET

Remember These 15 Answers

1. Java is always Pass By Value.
2. Local Variables live in Stack.
3. Objects live in Heap.
4. Static Variables belong to Class.
5. String is Immutable.
6. equals() checks content.
7. == checks address.
8. volatile gives visibility.
9. synchronized gives visibility + atomicity.
10. ThreadLocal is best for parallel WebDriver.
11. AtomicInteger is thread-safe.
12. StringBuilder is faster than StringBuffer.
13. Singleton provides one instance.
14. this.driver = driver avoids shadowing.
15. static WebDriver causes parallel execution failures.

If you can explain these 15 points confidently, you can answer a large percentage of Java variable-related interview questions.
