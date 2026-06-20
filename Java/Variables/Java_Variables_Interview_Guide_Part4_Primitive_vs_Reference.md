# Java Variables Interview Master Guide
# Part 4 - Primitive vs Reference Variables (Deep Dive)

## Table of Contents

1. Primitive Data Types
2. Reference Variables
3. Memory Storage Differences
4. Wrapper Classes
5. Autoboxing & Unboxing
6. Mutable vs Immutable Objects
7. String Immutability
8. StringBuilder vs StringBuffer
9. == vs equals()
10. Shallow Copy vs Deep Copy
11. Pass By Value with Objects
12. Selenium Framework Examples
13. REST Assured Examples
14. Interview Questions
15. MCQs
16. Quick Revision Notes

---

# 1. Primitive Data Types

Primitive types store actual values directly.

Java has 8 primitive types:

| Type | Size |
|--------|--------|
| byte | 1 byte |
| short | 2 bytes |
| int | 4 bytes |
| long | 8 bytes |
| float | 4 bytes |
| double | 8 bytes |
| char | 2 bytes |
| boolean | JVM dependent |

Example:

```java
int age = 25;
double salary = 50000.50;
char grade = 'A';
```

---

## Characteristics

- Fast access
- Fixed memory size
- Stored directly
- Cannot call methods

Example:

```java
int x = 10;
```

---

# 2. Reference Variables

Reference variables store addresses of objects.

Example:

```java
Employee emp = new Employee();
```

Memory:

```text
Stack
-------
emp -----> 101
-------

Heap
-------
Employee Object
-------
```

---

## Characteristics

- Store address/reference
- Can access methods
- Object stored in heap

Example:

```java
emp.getName();
```

---

# Primitive vs Reference Comparison

| Primitive | Reference |
|------------|------------|
| Stores value | Stores address |
| Faster | Slightly slower |
| Fixed size | Dynamic |
| No methods | Methods available |
| Stack | Heap + Stack |

---

# 3. Wrapper Classes

Every primitive has a corresponding wrapper class.

| Primitive | Wrapper |
|------------|------------|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

---

Example

```java
Integer age = 25;
Double salary = 1000.5;
```

Why Needed?

Collections can store objects, not primitives.

```java
List<Integer> numbers = new ArrayList<>();
```

---

# 4. Autoboxing

Automatic conversion:

Primitive → Wrapper

Example:

```java
Integer num = 10;
```

Compiler converts:

```java
Integer num = Integer.valueOf(10);
```

---

# 5. Unboxing

Wrapper → Primitive

Example:

```java
Integer num = 10;

int value = num;
```

Compiler:

```java
int value = num.intValue();
```

---

# Interview Question

What is Autoboxing?

Automatic conversion of primitive to wrapper object.

---

# 6. Mutable vs Immutable Objects

## Mutable

Object can change.

Example:

```java
StringBuilder sb = new StringBuilder("Java");

sb.append(" Selenium");
```

Original object changes.

---

## Immutable

Object cannot change.

Example:

```java
String str = "Java";

str.concat(" Selenium");
```

New object created.

Original remains unchanged.

---

# 7. String Immutability

Most Asked Interview Topic

```java
String name = "Java";

name.concat(" Selenium");
```

Output:

Java

Why?

String objects are immutable.

---

## Benefits

- Security
- Thread Safety
- String Pool Optimization
- Better Performance

---

## Memory Diagram

```text
String Pool

Java
Java Selenium
```

New string created instead of modifying existing one.

---

# 8. StringBuilder vs StringBuffer

## StringBuilder

```java
StringBuilder sb = new StringBuilder();
```

Characteristics:

- Fast
- Not Thread Safe
- Recommended for single-thread use

---

## StringBuffer

```java
StringBuffer sb = new StringBuffer();
```

Characteristics:

- Thread Safe
- Synchronized
- Slightly slower

---

## Comparison

| Feature | StringBuilder | StringBuffer |
|-----------|--------------|--------------|
| Thread Safe | No | Yes |
| Faster | Yes | No |
| Synchronization | No | Yes |

---

# 9. == vs equals()

Most Asked Question

## ==

Checks memory address.

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
```

Output:

false

---

## equals()

Checks content.

```java
System.out.println(s1.equals(s2));
```

Output:

true

---

## String Pool Case

```java
String a = "Java";
String b = "Java";
```

```java
a == b
```

Output:

true

Because both point to same pool object.

---

# 10. Shallow Copy vs Deep Copy

## Shallow Copy

Copies references.

```java
Employee e1 = new Employee();

Employee e2 = e1;
```

Both point to same object.

---

Memory

```text
e1 -----> 101
e2 -----> 101
```

---

## Deep Copy

Creates separate object.

```java
Employee e2 =
new Employee(e1);
```

---

Memory

```text
e1 -----> 101

e2 -----> 202
```

Independent objects.

---

# 11. Pass By Value with Objects

Favorite Interview Question

Java is ALWAYS Pass By Value.

Example:

```java
Employee emp = new Employee();
```

Reference value copied.

Not object itself.

---

Method Call

```java
modify(emp);
```

JVM copies reference value.

Object is not passed directly.

---

Interview Answer

Java passes copies of variables.

For objects, copy of reference is passed.

---

# Selenium Framework Example

## Bad Practice

```java
WebDriver driver1 = driver;
WebDriver driver2 = driver;
```

Multiple references to same object.

Can create maintenance issues.

---

## Better Design

Use Page Objects.

```java
LoginPage loginPage =
new LoginPage(driver);
```

Clear ownership.

---

# REST Assured Example

```java
Response response =
given().when().get();
```

Response is reference variable.

Actual object stored in heap.

---

# Frequently Asked Interview Questions

### Q1. Difference between Primitive and Reference Variable?

Primitive stores value.

Reference stores address.

---

### Q2. Why Wrapper Classes exist?

Collections require objects.

---

### Q3. What is Autoboxing?

Primitive to Wrapper conversion.

---

### Q4. What is Unboxing?

Wrapper to Primitive conversion.

---

### Q5. Why String is Immutable?

Security, Thread Safety, Performance.

---

### Q6. Difference between StringBuilder and StringBuffer?

Thread Safety.

---

### Q7. Difference between == and equals()?

Address vs Content.

---

### Q8. Is Java Pass By Reference?

No.

Java is Pass By Value.

---

### Q9. What is Deep Copy?

Separate object creation.

---

### Q10. What is Shallow Copy?

Reference copied.

---

# MCQs

Q1. Which stores actual value?

A. Reference Variable
B. Primitive Variable

Answer: B

---

Q2. Which class is immutable?

A. StringBuilder
B. StringBuffer
C. String

Answer: C

---

Q3. Which is thread safe?

A. StringBuilder
B. StringBuffer

Answer: B

---

Q4. equals() compares?

A. Address
B. Content

Answer: B

---

Q5. Java supports?

A. Pass By Reference
B. Pass By Value

Answer: B

---

# Quick Revision Notes

PRIMITIVE

- Stores value
- Faster
- Fixed size

REFERENCE

- Stores address
- Object in heap

WRAPPER CLASSES

- Object versions of primitives

AUTOBOXING

- Primitive → Wrapper

UNBOXING

- Wrapper → Primitive

STRING

- Immutable

STRINGBUILDER

- Fast
- Not Thread Safe

STRINGBUFFER

- Thread Safe

==

- Address comparison

equals()

- Content comparison

SHALLOW COPY

- Same object

DEEP COPY

- Separate objects

JAVA

- Always Pass By Value

---

# One Minute Interview Cheat Sheet

Primitive = Value

Reference = Address

Integer = Wrapper of int

Autoboxing = int → Integer

Unboxing = Integer → int

String = Immutable

StringBuilder = Faster

StringBuffer = Thread Safe

== = Address

equals() = Content

Shallow Copy = Same Object

Deep Copy = New Object

Java = Pass By Value Always
