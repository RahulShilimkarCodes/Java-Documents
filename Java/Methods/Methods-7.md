# Java Methods Master Guide

# Part 7 - Pass By Value Deep Dive

---

# Table of Contents

1. Introduction
2. What is Parameter Passing?
3. Pass By Value vs Pass By Reference
4. How Java Passes Parameters
5. Primitive Variables
6. Primitive Pass By Value Examples
7. Object References
8. Object Pass By Value Internals
9. String Parameters
10. Array Parameters
11. Wrapper Class Parameters
12. Memory Diagrams
13. JVM Stack & Heap Analysis
14. Common Interview Traps
15. Real Project Examples
16. Selenium Framework Usage
17. API Framework Usage
18. Advanced Interview Questions
19. Quick Revision Notes
20. Final Cheat Sheet

---

# 1. Introduction

This is one of the most misunderstood topics in Java interviews.

Many developers incorrectly say:

```text id="pbv1"
Java passes objects by reference
```

This statement is WRONG.

---

Correct Statement:

```text id="pbv2"
Java is ALWAYS Pass By Value.
```

Whether:

```text id="pbv3"
Primitive Variables

Objects

Arrays

Strings

Collections
```

Java ALWAYS uses Pass By Value.

---

Interviewers love this topic because it reveals whether a candidate truly understands JVM memory.

---

# 2. What is Parameter Passing?

Definition:

```text id="pbv4"
Parameter Passing is the process of
sending data from the calling method
to the called method.
```

Example:

```java id="pbv5"
display(100);
```

Here:

```text id="pbv6"
100
```

is passed to the method.

---

# 3. Pass By Value vs Pass By Reference

---

## Pass By Value

A COPY of the value is passed.

Changes inside method do not affect original variable.

---

## Pass By Reference

Actual memory reference is passed.

Changes affect original object directly.

---

Interview Point:

```text id="pbv7"
Java does NOT support Pass By Reference.
```

---

# 4. How Java Passes Parameters

Java always copies something.

For Primitive:

```text id="pbv8"
Copies Actual Value
```

For Objects:

```text id="pbv9"
Copies Reference Value
```

This is the key concept.

---

Example:

```java id="pbv10"
Employee emp =
new Employee();
```

Java copies:

```text id="pbv11"
Reference Address Value
```

Not the actual object.

---

# 5. Primitive Variables

Example:

```java id="pbv12"
public static void update(int num){

    num = 50;
}
```

Call:

```java id="pbv13"
int value = 10;

update(value);

System.out.println(value);
```

Output:

```text id="pbv14"
10
```

---

Why?

Because:

```text id="pbv15"
Copy of 10 was passed
```

Original variable remains unchanged.

---

# 6. Primitive Pass By Value Example

Example:

```java id="pbv16"
public static void modify(int x){

    x = x + 100;
}
```

Call:

```java id="pbv17"
int num = 20;

modify(num);

System.out.println(num);
```

Output:

```text id="pbv18"
20
```

---

Memory Diagram

Before Call:

```text id="pbv19"
num = 20
```

---

Method Call:

```text id="pbv20"
x = 20
```

Copy created.

---

Method Modification:

```text id="pbv21"
x = 120
```

Only local copy changes.

---

Original:

```text id="pbv22"
num = 20
```

Remains unchanged.

---

# 7. Object References

Most Important Interview Area.

Class:

```java id="pbv23"
class Employee{

    String name;
}
```

---

Method:

```java id="pbv24"
public static void update(Employee emp){

    emp.name = "Rahul";
}
```

Call:

```java id="pbv25"
Employee e =
new Employee();

e.name = "Java";

update(e);

System.out.println(e.name);
```

Output:

```text id="pbv26"
Rahul
```

---

Many developers think:

```text id="pbv27"
Java passed object by reference
```

Wrong.

---

# 8. Object Pass By Value Internals

Suppose:

```java id="pbv28"
Employee e =
new Employee();
```

Memory:

```text id="pbv29"
STACK

e → 1000

HEAP

Object @1000
```

---

Method Call:

```java id="pbv30"
update(e);
```

Copy Created:

```text id="pbv31"
STACK

e → 1000

emp → 1000
```

---

Important:

```text id="pbv32"
Two references

One object
```

---

Changing object:

```java id="pbv33"
emp.name = "Rahul";
```

Same object modified.

Hence changes visible outside.

---

# 9. String Parameters

Example:

```java id="pbv34"
public static void update(String name){

    name = "Selenium";
}
```

Call:

```java id="pbv35"
String value = "Java";

update(value);

System.out.println(value);
```

Output:

```text id="pbv36"
Java
```

---

Why?

Strings are Immutable.

---

Inside method:

```java id="pbv37"
name = "Selenium";
```

creates a new String reference.

Original String unchanged.

---

# 10. Array Parameters

Example:

```java id="pbv38"
public static void modify(int[] arr){

    arr[0] = 999;
}
```

Call:

```java id="pbv39"
int[] nums =
{
10,
20,
30
};

modify(nums);
```

Output:

```text id="pbv40"
999
20
30
```

---

Reason:

Both references point to same array object.

---

Memory:

```text id="pbv41"
nums → Array

arr → Same Array
```

---

# 11. Wrapper Class Parameters

Example:

```java id="pbv42"
public static void modify(Integer num){

    num = 100;
}
```

Call:

```java id="pbv43"
Integer x = 10;

modify(x);

System.out.println(x);
```

Output:

```text id="pbv44"
10
```

---

Reason:

Wrapper classes are immutable.

---

# 12. Memory Diagrams

Primitive Example:

```text id="pbv45"
value = 10

↓

copy

↓

num = 10
```

Independent variables.

---

Object Example:

```text id="pbv46"
e → Object

↓

copy reference

↓

emp → Same Object
```

Shared object.

---

Array Example:

```text id="pbv47"
arr1 → Array

↓

copy reference

↓

arr2 → Same Array
```

Shared array.

---

# 13. JVM Stack & Heap Analysis

Primitive:

```text id="pbv48"
Stack

num = 10

x = 10
```

Separate values.

---

Object:

```text id="pbv49"
Stack

e → 1000

emp → 1000

Heap

Object @1000
```

---

Interview Point:

```text id="pbv50"
Reference copied

Object not copied
```

---

# 14. Common Interview Traps

---

## Trap 1

Question:

```text id="pbv51"
Does Java support Pass By Reference?
```

Answer:

```text id="pbv52"
No
```

---

## Trap 2

Question:

```text id="pbv53"
Why can object changes be seen outside method?
```

Answer:

```text id="pbv54"
Because copied references
point to same object.
```

---

## Trap 3

Question:

```text id="pbv55"
Why String does not change?
```

Answer:

```text id="pbv56"
Strings are immutable.
```

---

# 15. Real Project Examples

---

## Selenium Driver

```java id="pbv57"
launchBrowser(driver);
```

Driver reference copied.

---

## API Response

```java id="pbv58"
validateResponse(response);
```

Response reference copied.

---

## Test Data Object

```java id="pbv59"
updateUser(user);
```

User reference copied.

---

# 16. Selenium Framework Usage

Example:

```java id="pbv60"
public void clickElement(WebElement element){

}
```

---

Method receives:

```text id="pbv61"
Copy of WebElement Reference
```

---

Not actual object copy.

---

Common Framework Example:

```java id="pbv62"
sendKeys(element,text);
```

---

# 17. API Framework Usage

Example:

```java id="pbv63"
validateResponse(Response response)
```

---

Reference copied.

Actual response object shared.

---

Frameworks heavily rely on object references.

---

# 18. Advanced Interview Questions

---

## Q1 Is Java Pass By Value or Pass By Reference?

Answer:

```text id="pbv64"
Java is always Pass By Value.
```

---

## Q2 What gets copied for objects?

Answer:

```text id="pbv65"
Reference Value
```

---

## Q3 What gets copied for primitives?

Answer:

```text id="pbv66"
Actual Value
```

---

## Q4 Why do object modifications persist?

Answer:

```text id="pbv67"
Multiple references point
to same object.
```

---

## Q5 Why don't String modifications persist?

Answer:

```text id="pbv68"
Strings are immutable.
```

---

# 19. Quick Revision Notes

```text id="pbv69"
Java Always Pass By Value

Primitive

Copy Value

Object

Copy Reference Value

String

Immutable

Array

Shared Object

Reference Copied

Object Not Copied
```

---

# 20. Final Cheat Sheet

```text id="pbv70"
Java Parameter Passing

Primitive

10 → Copy → 10

Object

Reference → Copy

Both Point To Same Object

Array

Reference → Copy

Same Array Shared

String

Immutable

New Object Created

Interview Answer

Java Is Always Pass By Value
```

---

# Interview Takeaway

If interviewer asks:

```text id="pbv71"
Explain why Java is always Pass By Value.
```

Strong Answer:

```text id="pbv72"
Java always passes a copy of a value.

For primitive variables,
the actual value is copied.

For objects,
the reference value is copied.

Because the copied reference and original
reference point to the same object,
changes to the object's state are visible
outside the method.

However, Java never passes the actual object
or memory reference itself, which is why
Java is strictly Pass By Value.
```

---

# End of Part 7

## Next Part

Part 8 → Variable Arguments (Varargs) & Recursion

Topics:

* Varargs (...)
* Varargs Rules
* Varargs vs Arrays
* Recursive Methods
* Recursion Stack Frames
* Factorial Program
* Fibonacci Program
* Real Interview Problems
* JVM Internals
* StackOverflowError
