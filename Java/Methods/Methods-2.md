# Java Methods Master Guide

# Part 2 - Method Declaration & Calling

---

# Table of Contents

1. Introduction
2. Method Declaration
3. Method Calling
4. Void Methods
5. Methods Returning Values
6. Static Methods
7. Non-Static Methods
8. Calling Methods Within Same Class
9. Calling Methods Across Different Classes
10. Method Execution Flow
11. Method Call Stack Examples
12. Real Project Examples
13. Selenium Framework Usage
14. API Framework Usage
15. Common Beginner Mistakes
16. Interview Questions
17. Quick Revision Notes
18. Final Cheat Sheet

---

# 1. Introduction

In Part 1, we learned:

* What methods are
* Why methods are important
* JVM execution flow
* Stack frames

In this part, we will learn:

```text
How methods are declared

How methods are called

Static vs Non-Static methods

Methods with and without return values

Method execution flow
```

These are some of the most frequently asked Java interview topics.

---

# 2. Method Declaration

Method Declaration means defining a method.

General Syntax:

```java
accessModifier returnType methodName(){

}
```

Example:

```java
public static void greet(){

    System.out.println("Hello");
}
```

Breakdown:

```text
public
→ Access Modifier

static
→ Belongs To Class

void
→ No Return Value

greet
→ Method Name
```

---

# 3. Method Calling

Declaring a method does not execute it.

Example:

```java
public static void greet(){

    System.out.println("Hello");
}
```

Nothing happens until method is called.

Method Call:

```java
greet();
```

Complete Program:

```java
public class Demo{

    public static void greet(){

        System.out.println("Hello");
    }

    public static void main(String[] args){

        greet();
    }
}
```

Output:

```text
Hello
```

---

# 4. Void Methods

Void means:

```text
Returns Nothing
```

Example:

```java
public static void displayMessage(){

    System.out.println("Welcome");
}
```

Call:

```java
displayMessage();
```

Output:

```text
Welcome
```

---

## Real World Example

```java
public static void launchBrowser(){

    System.out.println("Browser Launched");
}
```

No value returned.

Only performs an action.

---

# 5. Methods Returning Values

These methods return a result.

Example:

```java
public static int add(){

    return 10 + 20;
}
```

Call:

```java
int result = add();

System.out.println(result);
```

Output:

```text
30
```

---

## String Return Type

```java
public static String getName(){

    return "Rahul";
}
```

Call:

```java
String name = getName();
```

---

## Boolean Return Type

```java
public static boolean isLoginSuccessful(){

    return true;
}
```

Call:

```java
boolean status =
isLoginSuccessful();
```

---

# 6. Static Methods

Static methods belong to the class.

Example:

```java
public static void test(){

    System.out.println("Static Method");
}
```

Call:

```java
test();
```

OR

```java
Demo.test();
```

---

## Characteristics

```text
No Object Required

Class Level

Memory Efficient

Frequently Used In Utility Classes
```

---

## Real Project Example

```java
public static void captureScreenshot(){

}
```

Utility methods are often static.

---

# 7. Non-Static Methods

Non-static methods belong to objects.

Example:

```java
public void login(){

    System.out.println("Login Success");
}
```

Call:

```java
Demo d = new Demo();

d.login();
```

Output:

```text
Login Success
```

---

## Characteristics

```text
Object Required

Can Access Instance Variables

Object-Oriented Approach
```

---

# 8. Calling Methods Within Same Class

Example:

```java
public class Demo{

    public static void greet(){

        System.out.println("Hello");
    }

    public static void main(String[] args){

        greet();
    }
}
```

Execution:

```text
main()

↓

greet()

↓

Return
```

---

# 9. Calling Methods Across Different Classes

Class A:

```java
public class Utility{

    public static void display(){

        System.out.println("Utility Method");
    }
}
```

Class B:

```java
public class Test{

    public static void main(String[] args){

        Utility.display();
    }
}
```

Output:

```text
Utility Method
```

---

## Non-Static Example

Class A:

```java
public class LoginPage{

    public void login(){

        System.out.println("Login");
    }
}
```

Class B:

```java
public class Test{

    public static void main(String[] args){

        LoginPage page =
        new LoginPage();

        page.login();
    }
}
```

---

# 10. Method Execution Flow

Example:

```java
public static void methodA(){

    methodB();
}

public static void methodB(){

    methodC();
}

public static void methodC(){

    System.out.println("Done");
}
```

Execution:

```text
main()

↓

methodA()

↓

methodB()

↓

methodC()

↓

Return

↓

Return

↓

Return
```

---

# 11. Method Call Stack Example

Example:

```java
public static void A(){

    B();
}

public static void B(){

    C();
}

public static void C(){

}
```

Stack During Execution:

```text
+------+
| C()  |
+------+
| B()  |
+------+
| A()  |
+------+
|main()|
+------+
```

After C completes:

```text
+------+
| B()  |
+------+
| A()  |
+------+
|main()|
+------+
```

This is called:

```text
Call Stack
```

---

# 12. Real Project Examples

---

## Login Flow

```java
login();
```

---

## Search Flow

```java
searchProduct();
```

---

## Reporting

```java
generateReport();
```

---

## Screenshot Utility

```java
captureScreenshot();
```

---

## Browser Launch

```java
launchBrowser();
```

---

# 13. Selenium Framework Usage

Common Methods:

```java
launchBrowser();

login();

searchProduct();

addToCart();

checkout();

captureScreenshot();

closeBrowser();
```

---

Framework Structure:

```text
Test Class

↓

Page Methods

↓

Utility Methods

↓

WebDriver Actions
```

---

# 14. API Framework Usage

Common Methods:

```java
createUser();

updateUser();

deleteUser();

getUser();

validateResponse();
```

---

Example:

```java
Response response =
getUser();
```

Returned response used later.

---

# 15. Common Beginner Mistakes

---

## Mistake 1

Method Not Called

```java
public static void test(){

}
```

No output.

---

## Mistake 2

Ignoring Return Value

```java
add();
```

Better:

```java
int result = add();
```

---

## Mistake 3

Calling Non-Static Method Incorrectly

Wrong:

```java
login();
```

Correct:

```java
Demo d = new Demo();

d.login();
```

---

## Mistake 4

Wrong Return Type

```java
public static int test(){

    return "Hello";
}
```

Compilation Error.

---

# 16. Interview Questions

---

## Q1 What is Method Declaration?

Answer:

```text
Defining a method
using syntax and body.
```

---

## Q2 What is Method Calling?

Answer:

```text
Executing a method
using its name.
```

---

## Q3 Difference Between Void and Return Method?

Answer:

```text
Void Method
→ Returns Nothing

Return Method
→ Returns A Value
```

---

## Q4 Difference Between Static and Non-Static Method?

Answer:

```text
Static
→ Class Level

Non-Static
→ Object Level
```

---

## Q5 Can Static Method Call Non-Static Method Directly?

Answer:

```text
No

Object Creation Required
```

---

## Q6 Which Memory Is Used During Method Execution?

Answer:

```text
Stack Memory
```

---

# 17. Quick Revision Notes

```text
Method Declaration
→ Defining Method

Method Calling
→ Executing Method

Void Method
→ No Return Value

Return Method
→ Returns Value

Static Method
→ No Object Needed

Non-Static Method
→ Object Needed

Method Execution
→ Uses Stack Memory
```

---

# 18. Final Cheat Sheet

```text
Method Declaration

public static void test(){

}

Method Call

test();

Void Method

Returns Nothing

Return Method

Returns Value

Static Method

Class Level

Non-Static Method

Object Level

Execution

Method Call

↓

Stack Frame Created

↓

Execution

↓

Return

↓

Frame Removed
```

---

# Interview Takeaway

If interviewer asks:

```text
Explain Static vs Non-Static Methods.
```

Strong Answer:

```text
Static methods belong to the class and
can be called without object creation.

Non-static methods belong to objects and
require object creation before calling.

Static methods are commonly used in utility
classes, while non-static methods are used
when object state needs to be accessed.
```

---

# End of Part 2

## Next Part

Part 3 → Parameters & Arguments

Topics:

* Formal Parameters
* Actual Arguments
* Parameter Passing
* Primitive Parameters
* Object Parameters
* Multiple Parameters
* Method Signatures
* Interview Questions
* Selenium Examples
* API Framework Examples
