# Java Loops & Conditional Statements Master Guide

# Part 1 - Basics of Conditionals (if, else, switch)

---

# Table of Contents

1. Introduction
2. Why Conditionals are Important
3. if Statement
4. if-else Statement
5. if-else-if Ladder
6. Nested if
7. switch Statement
8. break in switch
9. Real-time Usage in Automation
10. Common Interview Mistakes
11. Short Notes
12. Revision Sheet

---

# 1. Introduction

Conditional statements help Java decide:

```text id="c1"
Which block of code should execute based on condition
```

They are used in:

* Selenium validations
* API response checks
* Business logic decisions
* Framework flow control

---

# 2. Why Conditionals are Important

Without conditionals:

```text id="c2"
Program runs blindly
```

With conditionals:

```text id="c3"
Program makes decisions
```

Example:

* Login success → proceed
* Login fail → retry / stop

---

# 3. if Statement

Executes code only when condition is true.

```java id="c4"
int age = 20;

if(age >= 18){
    System.out.println("Eligible to vote");
}
```

Output:

```text id="c5"
Eligible to vote
```

---

# 4. if-else Statement

Used when we have two outcomes.

```java id="c6"
int marks = 40;

if(marks >= 50){
    System.out.println("Pass");
} else {
    System.out.println("Fail");
}
```

Output:

```text id="c7"
Fail
```

---

# 5. if-else-if Ladder

Used for multiple conditions.

```java id="c8"
int marks = 75;

if(marks >= 90){
    System.out.println("A Grade");
}
else if(marks >= 70){
    System.out.println("B Grade");
}
else if(marks >= 50){
    System.out.println("C Grade");
}
else{
    System.out.println("Fail");
}
```

Output:

```text id="c9"
B Grade
```

---

# 6. Nested if

if inside if.

```java id="c10"
int age = 25;
boolean hasLicense = true;

if(age >= 18){
    if(hasLicense){
        System.out.println("Can drive");
    }
}
```

Output:

```text id="c11"
Can drive
```

---

# 7. switch Statement

Used for multiple fixed values.

```java id="c12"
int day = 3;

switch(day){
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    default:
        System.out.println("Invalid day");
}
```

Output:

```text id="c13"
Wednesday
```

---

# 8. break in switch

Stops execution after match.

Without break:

```text id="c14"
All cases will execute (fall-through)
```

---

# 9. Real-time Automation Usage

## Login Validation

```java id="c15"
if(driver.getTitle().equals("Dashboard")){
    System.out.println("Login Successful");
} else {
    System.out.println("Login Failed");
}
```

---

## API Status Check

```java id="c16"
String status = "success";

if(status.equalsIgnoreCase("success")){
    System.out.println("Test Passed");
} else {
    System.out.println("Test Failed");
}
```

---

## Environment Selection

```java id="c17"
String env = "QA";

switch(env){
    case "QA":
        System.out.println("QA URL Loaded");
        break;
    case "UAT":
        System.out.println("UAT URL Loaded");
        break;
}
```

---

# 10. Common Interview Mistakes

## Mistake 1: Using = instead of ==

```java id="c18"
if(a = 10) // ❌ wrong
```

Correct:

```java id="c19"
if(a == 10)
```

---

## Mistake 2: Missing break in switch

Leads to unwanted execution.

---

## Mistake 3: Not handling null

```java id="c20"
if(status.equals("PASS")) // NPE risk
```

Fix:

```java id="c21"
"PASS".equals(status)
```

---

# 11. Short Notes

✔ if → single condition
✔ if-else → two conditions
✔ if-else-if → multiple conditions
✔ switch → fixed values
✔ break → stops switch execution
✔ nested if → condition inside condition

---

# 12. Revision Sheet

```text id="c22"
if → condition true execute

if-else → two choices

if-else-if → multiple choices

switch → fixed cases

break → stop execution

default → fallback case
```

---

# Interview Quick Summary

* Conditionals control program flow
* switch is faster for fixed values
* if-else is flexible
* Always handle null safely
* Avoid assignment in if condition

---

# Part 1 Completed

Next Part:

Part 2 - Loops Basics

Topics:

* for loop
* while loop
* do-while loop
* enhanced for loop
* loop control statements (break, continue)
