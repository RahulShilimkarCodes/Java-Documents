# Java Methods Master Guide

# Part 4 - Return Types & Method Flow

---

# Table of Contents

1. Introduction
2. What is a Return Type?
3. Return Statement
4. Void vs Return Methods
5. Returning Primitive Values
6. Returning String Values
7. Returning Boolean Values
8. Returning Objects
9. Returning Arrays
10. Returning Collections
11. Returning Custom Objects
12. Method Chaining
13. JVM Execution Flow
14. Stack Memory & Return Values
15. Real Project Examples
16. Selenium Framework Usage
17. API Framework Usage
18. Common Beginner Mistakes
19. Interview Questions
20. Quick Revision Notes
21. Final Cheat Sheet

---

# 1. Introduction

In previous parts we learned:

* Method Declaration
* Method Calling
* Parameters
* Arguments
* Method Signatures

In this part we will learn:

```text id="a1r2m3"
Return Types

Return Statements

Returning Objects

Returning Arrays

Method Chaining

Method Flow

JVM Return Mechanism
```

This is one of the most important Java interview topics.

---

# 2. What is a Return Type?

Definition:

```text id="b2s3n4"
A return type specifies what value
a method sends back to the caller
after execution completes.
```

Example:

```java id="c3t4o5"
public static int add(){

    return 10;
}
```

Return Type:

```text id="d4u5p6"
int
```

---

# Why Return Values?

Without Return:

```java id="e5v6q7"
public static void add(){

    System.out.println(10+20);
}
```

Cannot reuse result.

---

With Return:

```java id="f6w7r8"
public static int add(){

    return 10+20;
}
```

Result can be stored and reused.

---

# 3. Return Statement

The return keyword terminates a method and sends a value back.

Syntax:

```java id="g7x8s9"
return value;
```

Example:

```java id="h8y9t0"
public static int square(int num){

    return num*num;
}
```

Call:

```java id="i9z0u1"
int result =
square(5);
```

Output:

```text id="j0a1v2"
25
```

---

# 4. Void vs Return Methods

---

## Void Method

Returns nothing.

Example:

```java id="k1b2w3"
public static void display(){

    System.out.println("Hello");
}
```

---

## Return Method

Returns a value.

Example:

```java id="l2c3x4"
public static String getName(){

    return "Rahul";
}
```

---

Comparison:

```text id="m3d4y5"
Void
→ Returns Nothing

Return Method
→ Returns Value
```

---

# 5. Returning Primitive Values

Most common interview topic.

Example:

```java id="n4e5z6"
public static int add(int a,int b){

    return a+b;
}
```

Call:

```java id="o5f6a7"
int sum =
add(10,20);
```

Output:

```text id="p6g7b8"
30
```

---

Other Examples:

```java id="q7h8c9"
public static double getSalary(){

    return 50000.50;
}
```

---

```java id="r8i9d0"
public static char getGrade(){

    return 'A';
}
```

---

# 6. Returning String Values

Very common in Selenium projects.

Example:

```java id="s9j0e1"
public static String getUserName(){

    return "admin";
}
```

Call:

```java id="t0k1f2"
String user =
getUserName();
```

Output:

```text id="u1l2g3"
admin
```

---

Real Framework Example:

```java id="v2m3h4"
String environment =
getEnvironment();
```

---

# 7. Returning Boolean Values

Frequently used in validations.

Example:

```java id="w3n4i5"
public static boolean isLoginSuccessful(){

    return true;
}
```

Call:

```java id="x4o5j6"
boolean status =
isLoginSuccessful();
```

---

Real Selenium Example:

```java id="y5p6k7"
if(isElementDisplayed()){

}
```

---

Real API Example:

```java id="z6q7l8"
if(isStatusCodeValid()){

}
```

---

# 8. Returning Objects

Very Important Interview Topic.

Example:

```java id="a7r8m9"
class Employee{

}
```

Method:

```java id="b8s9n0"
public static Employee getEmployee(){

    Employee e =
    new Employee();

    return e;
}
```

Call:

```java id="c9t0o1"
Employee emp =
getEmployee();
```

---

Interview Point:

```text id="d0u1p2"
Methods can return object references.
```

---

# 9. Returning Arrays

Frequently Asked.

Example:

```java id="e1v2q3"
public static int[] getNumbers(){

    return new int[]
    {
        10,
        20,
        30
    };
}
```

Call:

```java id="f2w3r4"
int[] arr =
getNumbers();
```

Output:

```text id="g3x4s5"
10

20

30
```

---

Real Framework Example:

```java id="h4y5t6"
String[] getSupportedBrowsers()
```

---

# 10. Returning Collections

Common in enterprise projects.

Example:

```java id="i5z6u7"
public static List<String> getUsers(){

    return users;
}
```

Call:

```java id="j6a7v8"
List<String> users =
getUsers();
```

---

Why Collections?

```text id="k7b8w9"
Dynamic Size

Flexible Storage

Enterprise Usage
```

---

# 11. Returning Custom Objects

Real Project Scenario.

Class:

```java id="l8c9x0"
class User{

    String name;
}
```

Method:

```java id="m9d0y1"
public static User createUser(){

    User user =
    new User();

    return user;
}
```

Call:

```java id="n0e1z2"
User user =
createUser();
```

---

Used extensively in:

```text id="o1f2a3"
API Frameworks

Page Objects

Business Layers
```

---

# 12. Method Chaining

Advanced Interview Topic.

Example:

```java id="p2g3b4"
String name =
"java";
```

Method Chain:

```java id="q3h4c5"
name.toUpperCase()
    .trim()
    .substring(1);
```

Execution:

```text id="r4i5d6"
Method 1 Executes

↓

Returns Value

↓

Method 2 Executes

↓

Returns Value

↓

Method 3 Executes
```

---

Why Possible?

Because each method returns something.

---

# 13. JVM Execution Flow

Example:

```java id="s5j6e7"
public static int add(){

    return 10;
}
```

Execution:

```text id="t6k7f8"
main()

↓

add()

↓

return 10

↓

main()
```

---

Stack Frame:

```text id="u7l8g9"
+------------+
| add()      |
| return 10  |
+------------+
```

---

# 14. Stack Memory & Return Values

Important Interview Question.

Example:

```java id="v8m9h0"
int result =
add();
```

Execution:

```text id="w9n0i1"
Method Executes

↓

Return Value Generated

↓

Value Sent To Caller

↓

Stack Frame Removed
```

---

Key Point:

```text id="x0o1j2"
Returned Value Survives

Method Stack Frame Does Not
```

---

# 15. Real Project Examples

---

## Configuration Reader

```java id="y1p2k3"
String getEnvironment()
```

---

## Browser Factory

```java id="z2q3l4"
WebDriver getDriver()
```

---

## User Builder

```java id="a3r4m5"
User createUser()
```

---

## API Response

```java id="b4s5n6"
Response getUser()
```

---

# 16. Selenium Framework Usage

Common Return Methods:

```java id="c5t6o7"
getTitle()

getCurrentUrl()

getText()

isDisplayed()

isEnabled()
```

Examples:

```java id="d6u7p8"
String title =
driver.getTitle();
```

---

```java id="e7v8q9"
boolean visible =
element.isDisplayed();
```

---

# 17. API Framework Usage

Common Examples:

```java id="f8w9r0"
Response response =
getUser();
```

---

```java id="g9x0s1"
String token =
generateToken();
```

---

```java id="h0y1t2"
boolean valid =
validateResponse();
```

---

# 18. Common Beginner Mistakes

---

## Mistake 1

Missing Return Statement

```java id="i1z2u3"
public static int add(){

}
```

Compilation Error.

---

## Mistake 2

Wrong Return Type

```java id="j2a3v4"
public static int getName(){

    return "Rahul";
}
```

Compilation Error.

---

## Mistake 3

Ignoring Returned Value

```java id="k3b4w5"
getName();
```

Better:

```java id="l4c5x6"
String name =
getName();
```

---

## Mistake 4

Returning Wrong Object

```java id="m5d6y7"
public static Employee getEmployee(){

    return new User();
}
```

Compilation Error.

---

# 19. Interview Questions

---

## Q1 What is a Return Type?

Answer:

```text id="n6e7z8"
Specifies the type of value
returned by a method.
```

---

## Q2 What is Return Statement?

Answer:

```text id="o7f8a9"
Used to terminate a method
and send a value back.
```

---

## Q3 Can a Method Return an Object?

Answer:

```text id="p8g9b0"
Yes
```

---

## Q4 Can a Method Return an Array?

Answer:

```text id="q9h0c1"
Yes
```

---

## Q5 Can a Method Return a Collection?

Answer:

```text id="r0i1d2"
Yes
```

---

## Q6 Can Void Methods Return Values?

Answer:

```text id="s1j2e3"
No
```

---

## Q7 Why Use Return Values?

Answer:

```text id="t2k3f4"
To reuse results
in other parts of application.
```

---

# 20. Quick Revision Notes

```text id="u3l4g5"
Return Type

Specifies Returned Value

Void

Returns Nothing

Primitive Values

Can Be Returned

Objects

Can Be Returned

Arrays

Can Be Returned

Collections

Can Be Returned

Method Chaining

Requires Return Values
```

---

# 21. Final Cheat Sheet

```text id="v4m5h6"
Return Type

public int add()

Return Statement

return value;

Examples

return 10;

return "Rahul";

return true;

return employee;

return array;

return list;

Method Chaining

object.method1()
      .method2()
      .method3();
```

---

# Interview Takeaway

If interviewer asks:

```text id="w5n6i7"
Can a Java method return an object?
```

Strong Answer:

```text id="x6o7j8"
Yes.

Java methods can return primitive values,
objects, arrays, collections,
and custom objects.

When an object is returned,
the method actually returns
the reference to that object.
```

---

# End of Part 4

## Next Part

Part 5 → Method Overloading

Topics:

* What is Overloading
* Compile Time Polymorphism
* Method Signatures
* Overloading Rules
* Type Promotion
* Ambiguous Calls
* Real Project Examples
* Selenium Framework Usage
* Advanced Interview Questions
