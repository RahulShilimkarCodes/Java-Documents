# Java Variables Interview Master Guide
# Part 9 - 100+ Java Variables Interview Questions & Answers

## Table of Contents

1. Basic Interview Questions (1-25)
2. Intermediate Questions (26-50)
3. Advanced Questions (51-75)
4. Framework & Project Questions (76-100)
5. Rapid Revision Notes

---

# BASIC INTERVIEW QUESTIONS (1-25)

## Q1. What is a Variable?

A variable is a named memory location used to store data.

Example:

```java
int age = 25;
```

---

## Q2. Why are variables required?

Variables allow programs to store and manipulate data dynamically.

---

## Q3. What are the types of variables in Java?

- Local Variable
- Instance Variable
- Static Variable

---

## Q4. What is a Local Variable?

Declared inside methods, constructors, or blocks.

Stored in Stack Memory.

---

## Q5. What is an Instance Variable?

Declared inside class but outside methods.

Belongs to object.

Stored in Heap Memory.

---

## Q6. What is a Static Variable?

Belongs to class.

Shared across all objects.

---

## Q7. What is a Final Variable?

Cannot be reassigned after initialization.

---

## Q8. Can local variables have default values?

No.

They must be initialized explicitly.

---

## Q9. Do instance variables get default values?

Yes.

Example:

```java
int x;
```

Default value = 0

---

## Q10. Where are local variables stored?

Stack Memory.

---

## Q11. Where are objects stored?

Heap Memory.

---

## Q12. Where are static variables stored?

Metaspace / Method Area.

---

## Q13. Can variable names start with numbers?

No.

```java
int 1age;
```

Invalid.

---

## Q14. Can variable names start with _?

Yes.

```java
int _age;
```

Valid.

---

## Q15. Is Java case-sensitive?

Yes.

```java
age
Age
AGE
```

Different variables.

---

## Q16. What is variable initialization?

Assigning value during declaration or later.

---

## Q17. Can local variables be static?

No.

---

## Q18. Can instance variables be final?

Yes.

---

## Q19. Can static variables be final?

Yes.

Most common constant pattern.

---

## Q20. What is variable scope?

Region where variable is accessible.

---

## Q21. What is variable lifetime?

Duration variable exists in memory.

---

## Q22. What is variable declaration?

Creating variable name and type.

---

## Q23. What is variable definition?

Declaration plus memory allocation.

---

## Q24. Difference between declaration and initialization?

Declaration:

```java
int age;
```

Initialization:

```java
age = 25;
```

---

## Q25. Why use final constants?

Prevent accidental modification.

---

# INTERMEDIATE QUESTIONS (26-50)

## Q26. Difference between Local and Instance Variables?

Local:

Method-level.

Instance:

Object-level.

---

## Q27. Difference between Instance and Static Variables?

Instance:

One copy per object.

Static:

One copy per class.

---

## Q28. Why local variables don't get default values?

Compiler forces initialization.

---

## Q29. Why instance variables get default values?

Object memory initialized by JVM.

---

## Q30. What is Variable Shadowing?

Local variable hides instance variable.

---

## Q31. What is Variable Hiding?

Child variable hides parent variable.

---

## Q32. Why use this keyword?

Access current object's members.

---

## Q33. Why use super keyword?

Access parent class members.

---

## Q34. Can static method access instance variable?

No directly.

---

## Q35. Can instance method access static variable?

Yes.

---

## Q36. What is effectively final variable?

Not modified after initialization.

---

## Q37. Why lambdas require effectively final variables?

Consistency and thread safety.

---

## Q38. What is autoboxing?

Primitive → Wrapper conversion.

---

## Q39. What is unboxing?

Wrapper → Primitive conversion.

---

## Q40. Why wrapper classes exist?

Collections require objects.

---

## Q41. Difference between primitive and reference variable?

Primitive stores value.

Reference stores address.

---

## Q42. What is immutable object?

Cannot be modified after creation.

---

## Q43. Is String immutable?

Yes.

---

## Q44. Benefits of String immutability?

Security, Thread Safety, Pool Optimization.

---

## Q45. Difference between StringBuilder and StringBuffer?

Thread Safety.

---

## Q46. Difference between == and equals()?

Address vs Content.

---

## Q47. What is shallow copy?

Copies references.

---

## Q48. What is deep copy?

Creates separate object.

---

## Q49. What is String Pool?

Memory area for string literals.

---

## Q50. Why String Pool exists?

Reduce duplicate objects.

---

# ADVANCED QUESTIONS (51-75)

## Q51. Is Java Pass By Reference?

No.

Always Pass By Value.

---

## Q52. What gets copied when object passed?

Reference value.

---

## Q53. What is StackOverflowError?

Excessive stack frame creation.

---

## Q54. What is OutOfMemoryError?

Heap exhausted.

---

## Q55. Explain JVM Memory Areas.

Stack, Heap, Metaspace, PC Register.

---

## Q56. Difference between Stack and Heap?

Stack:

Method execution.

Heap:

Object storage.

---

## Q57. Why Stack is faster?

Sequential memory allocation.

---

## Q58. Explain Object Creation Process.

Class load → Heap allocation → Constructor execution.

---

## Q59. Where are references stored?

Stack.

---

## Q60. Where are instance variables stored?

Heap.

---

## Q61. Where are static variables stored?

Metaspace.

---

## Q62. What is Garbage Collection?

Automatic memory cleanup.

---

## Q63. When object becomes eligible for GC?

When unreachable.

---

## Q64. Does eligible mean immediately collected?

No.

---

## Q65. What is Memory Leak?

Unused objects retained unnecessarily.

---

## Q66. Can Java have memory leaks?

Yes.

---

## Q67. What is volatile variable?

Provides visibility guarantee.

---

## Q68. Does volatile provide atomicity?

No.

---

## Q69. Difference between volatile and synchronized?

Visibility vs Visibility+Atomicity.

---

## Q70. What is Race Condition?

Multiple threads modifying shared data.

---

## Q71. What is AtomicInteger?

Thread-safe counter.

---

## Q72. What is ThreadLocal?

Thread-specific variable storage.

---

## Q73. Why use ThreadLocal?

Parallel execution support.

---

## Q74. What is Happens-Before Relationship?

Memory visibility guarantee.

---

## Q75. Why HashMap is not thread-safe?

No synchronization.

---

# FRAMEWORK & PROJECT QUESTIONS (76-100)

## Q76. Why WebDriver often stored as variable?

Shared browser session management.

---

## Q77. Why static WebDriver is dangerous?

Parallel execution failures.

---

## Q78. Best WebDriver storage mechanism?

ThreadLocal<WebDriver>

---

## Q79. Why use DriverFactory?

Centralized driver management.

---

## Q80. Why use ConfigReader?

External configuration management.

---

## Q81. Why use Properties object?

Read configuration dynamically.

---

## Q82. Why avoid hardcoded URLs?

Maintainability.

---

## Q83. Why use Constants class?

Centralized constant management.

---

## Q84. Why static final constants?

Shared immutable values.

---

## Q85. Why use Singleton ConfigManager?

Single configuration instance.

---

## Q86. Why constructor injection?

Dependency Injection.

---

## Q87. Why pass driver in Page Object constructor?

Loose coupling.

---

## Q88. Why this.driver = driver?

Avoid shadowing.

---

## Q89. Why use ThreadLocal in Selenium?

Separate browser per thread.

---

## Q90. How to avoid driver memory leaks?

driver.quit() + driver.remove()

---

## Q91. What variable stores API response?

Response object.

---

## Q92. What variable stores API request setup?

RequestSpecification.

---

## Q93. Why reusable RequestSpecification?

Reduce duplication.

---

## Q94. Playwright Page variable represents?

Browser tab.

---

## Q95. Playwright Browser variable represents?

Browser process.

---

## Q96. Difference between Browser and BrowserContext?

Context isolates sessions.

---

## Q97. Why environment variables?

Environment switching.

---

## Q98. How to support QA/UAT/PROD?

Properties + Environment Variables.

---

## Q99. What is most common Selenium framework mistake?

Static shared WebDriver.

---

## Q100. Best automation framework variable design?

ThreadLocal + Dependency Injection + Constants + ConfigReader.

---

# RAPID REVISION NOTES

LOCAL VARIABLE

- Stack
- No default value

INSTANCE VARIABLE

- Heap
- Default values

STATIC VARIABLE

- Class-level
- Shared

FINAL VARIABLE

- Constant

STRING

- Immutable

STRINGBUILDER

- Fast

STRINGBUFFER

- Thread Safe

PASS BY VALUE

- Always

THREADLOCAL

- Thread-specific

VOLATILE

- Visibility

SYNCHRONIZED

- Atomicity + Visibility

DRIVER MANAGEMENT

- ThreadLocal<WebDriver>

CONFIGURATION

- Properties

CONSTANTS

- static final

DEPENDENCY INJECTION

- Constructor Injection

---

# TOP 10 INTERVIEW ANSWERS TO MEMORIZE

1. Java is always Pass By Value.
2. Objects are stored in Heap Memory.
3. References are stored in Stack Memory.
4. Static variables belong to class.
5. String is immutable.
6. volatile provides visibility only.
7. synchronized provides visibility and atomicity.
8. ThreadLocal is best for parallel WebDriver execution.
9. this.driver = driver avoids variable shadowing.
10. static WebDriver is unsafe in parallel execution.
