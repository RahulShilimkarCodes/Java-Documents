# Java Variables Interview Master Guide
# Part 5 - Pass By Value (Complete Interview Guide)

## Table of Contents

1. What is Pass By Value?
2. What is Pass By Reference?
3. Why Java is Always Pass By Value
4. Primitive Parameter Passing
5. Object Parameter Passing
6. Array Passing
7. String Passing
8. Collection Passing
9. Mutable vs Immutable Behavior
10. JVM Method Call Internals
11. Selenium Framework Examples
12. TestNG Framework Examples
13. Tricky Interview Questions
14. MCQs
15. Quick Revision Notes

---

# 1. What is Pass By Value?

Pass By Value means a copy of the variable is passed to the method.

Changes inside the method do not affect the original variable.

Example:

```java
public static void main(String[] args) {

    int num = 10;

    modify(num);

    System.out.println(num);
}

static void modify(int num) {

    num = 100;
}
```

Output:

```text
10
```

Reason:

A copy of num was passed.

---

# Memory Representation

Before Method Call

```text
main()
---------
num = 10
---------
```

During Method Call

```text
main()
---------
num = 10
---------

modify()
---------
num = 10 (copy)
---------
```

Changes occur only in copied variable.

---

# 2. What is Pass By Reference?

Pass By Reference means the actual variable is passed.

Method directly modifies original variable.

Languages like C++ support true Pass By Reference.

Example:

```cpp
void modify(int &x)
{
   x = 100;
}
```

Java DOES NOT support this.

---

# 3. Why Java is Always Pass By Value

Most Asked Interview Question

Official Answer:

Java always passes a copy of the variable.

For primitives:

Copy of value.

For objects:

Copy of reference.

Not object itself.

---

# Interview Statement

Wrong:

Java is Pass By Reference.

Correct:

Java is Pass By Value.

Objects are passed as copied references.

---

# 4. Primitive Parameter Passing

Example

```java
int age = 25;

update(age);
```

Method

```java
static void update(int age) {

    age = 50;
}
```

Output:

```text
25
```

Original value remains unchanged.

---

# Memory Diagram

```text
main()
----------
age = 25
----------

update()
----------
age = 25 (copy)
----------
```

---

# 5. Object Parameter Passing

Example

```java
class Employee {

    String name;
}
```

```java
Employee emp = new Employee();

emp.name = "Rahul";

change(emp);
```

Method

```java
static void change(Employee emp) {

    emp.name = "Rohini";
}
```

Output:

```text
Rohini
```

---

# Why Did It Change?

Copy of reference passed.

Both references point to same object.

Memory

```text
main()
-------------
emp ----> 101
-------------

change()
-------------
emp ----> 101
-------------
```

Same object modified.

---

# Reassigning Object

Example

```java
static void change(Employee emp) {

    emp = new Employee();

    emp.name = "New";
}
```

Output

Original object unchanged.

Why?

Reference copy now points elsewhere.

---

# Memory Diagram

Before

```text
main emp ----> 101

change emp ----> 101
```

After Reassignment

```text
main emp ----> 101

change emp ----> 202
```

Original remains intact.

---

# 6. Array Passing

Arrays are objects.

Example

```java
int[] nums = {1,2,3};

modify(nums);
```

Method

```java
nums[0] = 99;
```

Output

```text
99 2 3
```

Array object modified.

---

# Array Reassignment

```java
nums = new int[5];
```

Only local copy changes.

Original array remains unchanged.

---

# 7. String Passing

String is immutable.

Example

```java
String name = "Java";

modify(name);
```

Method

```java
name = "Selenium";
```

Output

```text
Java
```

Original remains unchanged.

---

# Why?

String object cannot be modified.

New object created.

Reference copy updated locally.

---

# Memory Representation

```text
main

name --> Java

modify

name --> Selenium
```

Different references.

---

# 8. Collection Passing

Example

```java
List<String> names =
new ArrayList<>();
```

Method

```java
names.add("Java");
```

Original collection changes.

Reason:

Both references point to same object.

---

# Collection Reassignment

```java
names = new ArrayList<>();
```

Only local reference changes.

Original remains unchanged.

---

# 9. Mutable vs Immutable Behavior

## Mutable

Can be modified.

Examples:

- ArrayList
- HashMap
- StringBuilder
- Employee Object

---

## Immutable

Cannot be modified.

Examples:

- String
- Wrapper Classes

---

# Interview Trap

Question:

Why collection changes but String doesn't?

Answer:

Collections are mutable.

String is immutable.

---

# 10. JVM Method Call Internals

Method Invocation

```java
modify(emp);
```

JVM:

Step 1

Create stack frame.

Step 2

Copy variable value.

Step 3

Execute method.

Step 4

Destroy stack frame.

---

# Stack Frame Example

```text
main()

emp ---> 101
```

Method Call

```text
main()

emp ---> 101

modify()

emp ---> 101
```

Reference copied.

---

# Selenium Framework Example

Example

```java
public LoginPage(WebDriver driver) {

    this.driver = driver;
}
```

Interview Question

Why does this work?

Answer:

Copy of WebDriver reference passed.

Both references point to same browser session.

---

# Selenium Mistake

```java
driver = new ChromeDriver();
```

Inside method.

May create new browser instance.

Original reference unaffected.

---

# TestNG Example

```java
@BeforeMethod
public void setup() {

    initializeDriver(driver);
}
```

Driver reference passed by value.

Reference copied.

---

# REST Assured Example

```java
Response response =
given().when().get();
```

Response variable contains reference.

Actual Response object exists in heap.

---

# Tricky Interview Questions

### Q1. Is Java Pass By Value or Pass By Reference?

Pass By Value.

---

### Q2. Why object values appear modified?

Because copied references point to same object.

---

### Q3. Can method change original object?

Yes.

By modifying object's state.

---

### Q4. Can method replace original object?

No.

Only local reference copy changes.

---

### Q5. Are arrays passed by reference?

No.

Reference copy passed.

---

### Q6. Why String remains unchanged?

Immutable object.

---

### Q7. Why ArrayList changes?

Mutable object.

---

### Q8. What exactly gets copied?

Primitive value or object reference value.

---

# MCQs

Q1. Java supports?

A. Pass By Reference
B. Pass By Value

Answer: B

---

Q2. When object passed to method?

A. Object copied
B. Reference copied

Answer: B

---

Q3. String changes after method call?

A. Always
B. Never directly

Answer: B

---

Q4. ArrayList is?

A. Immutable
B. Mutable

Answer: B

---

Q5. Stack frame stores?

A. Local Variables
B. Objects

Answer: A

---

# Quick Revision Notes

PASS BY VALUE

- Copy passed

PRIMITIVES

- Value copied

OBJECTS

- Reference copied

ARRAYS

- Reference copied

STRING

- Immutable

COLLECTIONS

- Mutable

METHOD CALL

- New stack frame

JAVA

- Never Pass By Reference

---

# One Minute Interview Cheat Sheet

Primitive → Value Copy

Object → Reference Copy

Array → Reference Copy

String → Immutable

Collection → Mutable

Method Call → New Stack Frame

Object State Can Change

Object Reference Cannot Be Replaced Outside Method

Java = Always Pass By Value

Most Important Interview Answer:

Java passes copies of variables.
For objects, the copied value is the reference address.
