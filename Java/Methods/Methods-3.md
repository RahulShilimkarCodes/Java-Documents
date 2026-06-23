# Java Methods Master Guide

# Part 3 - Parameters & Arguments

---

# Table of Contents

1. Introduction
2. What are Parameters?
3. What are Arguments?
4. Parameters vs Arguments
5. Formal Parameters
6. Actual Arguments
7. Single Parameter Methods
8. Multiple Parameter Methods
9. Primitive Parameters
10. Object Parameters
11. String Parameters
12. Array Parameters
13. Method Signatures
14. Parameter Matching Rules
15. JVM Execution Flow
16. Real Project Examples
17. Selenium Framework Usage
18. API Framework Usage
19. Common Beginner Mistakes
20. Interview Questions
21. Quick Revision Notes
22. Final Cheat Sheet

---

# 1. Introduction

In Part 2, we learned:

* Method Declaration
* Method Calling
* Static Methods
* Non-Static Methods
* Void Methods
* Return Methods

In this part, we will learn:

```text id="k1r7dx"
Parameters

Arguments

Method Signatures

Parameter Passing

Primitive Parameters

Object Parameters

Real Framework Examples
```

This is one of the most frequently asked Java interview topics.

---

# 2. What are Parameters?

Parameters are variables declared inside the method definition.

Example:

```java id="h5z9tm"
public static void greet(String name){

}
```

Here:

```text id="h7z5yr"
name
```

is a Parameter.

---

Definition:

```text id="c8w7sn"
Parameters are placeholders
that receive values when a method is called.
```

---

# 3. What are Arguments?

Arguments are actual values passed during method call.

Example:

```java id="m4g8uk"
greet("Rahul");
```

Here:

```text id="98l1tk"
"Rahul"
```

is an Argument.

---

Definition:

```text id="w5e9xp"
Arguments are actual values supplied
to a method during execution.
```

---

# 4. Parameters vs Arguments

Example:

```java id="v6q8fc"
public static void greet(String name){

    System.out.println(name);
}

greet("Rahul");
```

Breakdown:

```text id="b3s7ye"
String name
→ Parameter

"Rahul"
→ Argument
```

---

Interview Definition:

```text id="j6z2rn"
Parameter
=
Method Definition

Argument
=
Method Call
```

---

# 5. Formal Parameters

Another interview term.

Example:

```java id="t7n8qs"
public static void add(int a,int b){

}
```

Formal Parameters:

```text id="y9m3kx"
a

b
```

---

Why Formal?

Because values are assigned later during execution.

---

# 6. Actual Arguments

Example:

```java id="r4j7un"
add(10,20);
```

Actual Arguments:

```text id="e7k2fs"
10

20
```

These values are supplied at runtime.

---

# 7. Single Parameter Methods

Example:

```java id="s2x5dw"
public static void greet(String name){

    System.out.println(name);
}
```

Call:

```java id="a6m9pt"
greet("Rahul");
```

Output:

```text id="d3v7nb"
Rahul
```

---

Execution:

```text id="j5z8qm"
Parameter
name

↓

Receives

↓

Rahul
```

---

# 8. Multiple Parameter Methods

Example:

```java id="u9r2kl"
public static void add(int a,int b){

    System.out.println(a+b);
}
```

Call:

```java id="p8t3sx"
add(10,20);
```

Output:

```text id="v1w5qe"
30
```

---

Execution:

```text id="k7m2nx"
a = 10

b = 20
```

---

# 9. Primitive Parameters

Primitive values can be passed as parameters.

Example:

```java id="q4h9lr"
public static void square(int num){

    System.out.println(num*num);
}
```

Call:

```java id="n2f7yc"
square(5);
```

Output:

```text id="r8k4vm"
25
```

---

Common Primitive Types:

```text id="c5j1ua"
int

double

float

char

boolean

long

short

byte
```

---

# 10. Object Parameters

Objects can also be passed.

Example:

```java id="g8m2sx"
class Employee{

}
```

Method:

```java id="t4p9vb"
public static void display(Employee emp){

}
```

Call:

```java id="k9x3rt"
Employee e =
new Employee();

display(e);
```

---

Interview Point:

```text id="v7j6pd"
Java passes object references by value.
```

Important topic.

Will be covered deeply in Pass By Value section.

---

# 11. String Parameters

String is the most commonly used parameter type.

Example:

```java id="w2n8qx"
public static void login(String username){

    System.out.println(username);
}
```

Call:

```java id="j6k9wp"
login("admin");
```

Output:

```text id="n1v5sz"
admin
```

---

Real Selenium Example:

```java id="p7q2xd"
enterUsername("admin");
```

---

# 12. Array Parameters

Methods can receive arrays.

Example:

```java id="d8r5tm"
public static void printArray(int[] arr){

    for(int num : arr){

        System.out.println(num);
    }
}
```

Call:

```java id="x4j7ku"
int[] numbers =
{
10,20,30
};

printArray(numbers);
```

Output:

```text id="w9s1ey"
10

20

30
```

---

Interview Favorite.

---

# 13. Method Signatures

Very Important Topic.

Example:

```java id="m5r8tz"
public static void add(int a,int b){

}
```

Method Signature:

```text id="q7n3vx"
Method Name

+

Parameter List
```

Signature:

```text id="k2m9aw"
add(int,int)
```

---

Return Type NOT Included.

Example:

```java id="r6v3ks"
int add(int a,int b)
```

and

```java id="p4t8yn"
double add(int a,int b)
```

Compilation Error.

Reason:

Same Method Signature.

---

# 14. Parameter Matching Rules

Example:

```java id="u1q5mw"
public static void display(int num){

}
```

Valid:

```java id="j8n2sx"
display(10);
```

Invalid:

```java id="x3r7tk"
display("Hello");
```

Compilation Error.

Reason:

Parameter mismatch.

---

# 15. JVM Execution Flow

Example:

```java id="q9v6xp"
public static void greet(String name){

    System.out.println(name);
}

greet("Rahul");
```

Execution:

```text id="w2m8ks"
main()

↓

greet()

↓

Parameter Created

↓

Value Assigned

↓

Method Executes

↓

Return
```

---

Stack Frame:

```text id="s5k3vt"
+----------------+
| name = Rahul   |
+----------------+
```

Stored inside method stack frame.

---

# 16. Real Project Examples

---

## Login Method

```java id="r7j1ux"
login("admin");
```

---

## Search Product

```java id="h4m8qk"
searchProduct("Laptop");
```

---

## Environment Selection

```java id="k5v2nz"
launchBrowser("Chrome");
```

---

## Report Generation

```java id="w1t6yr"
generateReport("Regression");
```

---

# 17. Selenium Framework Usage

Common Methods:

```java id="n9q4tw"
enterUsername("admin");

enterPassword("admin123");

selectCountry("India");

searchProduct("iPhone");
```

Parameters make methods reusable.

---

Without Parameters:

```java id="m2k7vx"
enterAdminUsername();

enterIndiaCountry();
```

Poor design.

---

# 18. API Framework Usage

Example:

```java id="r8x1tm"
getUser(101);
```

---

```java id="p5q9wn"
deleteUser(101);
```

---

```java id="s3v6kr"
createUser("Rahul");
```

---

Dynamic methods improve framework flexibility.

---

# 19. Common Beginner Mistakes

---

## Mistake 1

Wrong Number Of Arguments

Method:

```java id="k8m4pt"
add(int a,int b)
```

Call:

```java id="w7n3qx"
add(10);
```

Compilation Error.

---

## Mistake 2

Wrong Data Type

Method:

```java id="d6r8tv"
display(int num);
```

Call:

```java id="x5p2ks"
display("Hello");
```

Compilation Error.

---

## Mistake 3

Parameter Name Confusion

```java id="t1m9xr"
public static void greet(String name){

}
```

Parameter name can be anything.

Example:

```java id="r4v8qn"
public static void greet(String value){

}
```

Still valid.

---

# 20. Interview Questions

---

## Q1 What is a Parameter?

Answer:

```text id="v7m2ks"
A variable declared
inside method definition.
```

---

## Q2 What is an Argument?

Answer:

```text id="p8x3tw"
Actual value supplied
during method call.
```

---

## Q3 Difference Between Parameter and Argument?

Answer:

```text id="s5r1nx"
Parameter
→ Placeholder

Argument
→ Actual Value
```

---

## Q4 What is Method Signature?

Answer:

```text id="m2q7vx"
Method Name

+

Parameter List
```

---

## Q5 Is Return Type Part Of Method Signature?

Answer:

```text id="r9t4ks"
No
```

---

## Q6 Can Arrays Be Passed To Methods?

Answer:

```text id="x8n6wp"
Yes
```

---

## Q7 Can Objects Be Passed To Methods?

Answer:

```text id="j1m5tx"
Yes
```

---

# 21. Quick Revision Notes

```text id="t7v9ks"
Parameter
→ Placeholder

Argument
→ Actual Value

Formal Parameter
→ Method Definition

Actual Argument
→ Method Call

Method Signature
→ Name + Parameters

Return Type
→ Not Part Of Signature

Arrays Can Be Passed

Objects Can Be Passed
```

---

# 22. Final Cheat Sheet

```text id="q4x8wp"
Parameter

public void test(int num)

Argument

test(10)

Method Signature

test(int)

Not Included

Return Type

Examples

login("admin")

searchProduct("Laptop")

getUser(101)

launchBrowser("Chrome")
```

---

# Interview Takeaway

If interviewer asks:

```text id="n6m3tx"
Difference between Parameter and Argument?
```

Strong Answer:

```text id="r2v8ks"
Parameters are variables declared
inside the method definition.

Arguments are actual values passed
during method invocation.

Parameters act as placeholders,
while arguments provide the real data
used during execution.
```

---

# End of Part 3

## Next Part

Part 4 → Return Types & Method Flow

Topics:

* Return Statement
* Returning Primitive Values
* Returning Objects
* Returning Arrays
* Returning Collections
* Returning Custom Objects
* Method Chaining
* Execution Flow
* JVM Internals
* Selenium Examples
* API Framework Examples
