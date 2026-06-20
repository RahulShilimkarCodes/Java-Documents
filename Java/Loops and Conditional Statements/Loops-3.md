# Java Loops & Conditional Statements Master Guide

# Part 3 - Advanced Loops, Nested Loops & Patterns

---

# Table of Contents

1. Introduction to Advanced Loops
2. Nested Loops Concept
3. Time Complexity of Loops
4. Star Patterns
5. Number Patterns
6. Alphabet Patterns
7. Pyramid Patterns
8. Interview Coding Patterns
9. break & continue in Nested Loops
10. Real-time Selenium Usage
11. Real API Usage
12. Common Interview Mistakes
13. Short Notes
14. Revision Sheet

---

# 1. Introduction to Advanced Loops

Advanced loops involve:

* Nested loops
* Pattern printing
* Optimization thinking
* Interview-based logic building

Used heavily in:

```text id="a1"
Coding interviews + automation frameworks
```

---

# 2. Nested Loops Concept

Loop inside another loop.

Example:

```java id="a2"
for(int i = 1; i <= 3; i++){
    for(int j = 1; j <= 3; j++){
        System.out.println(i + " " + j);
    }
}
```

Output:

```text id="a3"
1 1
1 2
1 3
2 1
2 2
2 3
3 1
3 2
3 3
```

---

# 3. Time Complexity

Nested loops:

```text id="a4"
O(n²)
```

Single loop:

```text id="a5"
O(n)
```

Important interview point:

```text id="a6"
Avoid nested loops for large datasets
```

---

# 4. Star Patterns

## Pattern 1: Square

```java id="a7"
for(int i = 1; i <= 4; i++){
    for(int j = 1; j <= 4; j++){
        System.out.print("* ");
    }
    System.out.println();
}
```

Output:

```text id="a8"
* * * *
* * * *
* * * *
* * * *
```

---

## Pattern 2: Right Triangle

```java id="a9"
for(int i = 1; i <= 5; i++){
    for(int j = 1; j <= i; j++){
        System.out.print("* ");
    }
    System.out.println();
}
```

Output:

```text id="a10"
*
* *
* * *
* * * *
* * * * *
```

---

# 5. Number Patterns

## Pattern 1

```java id="a11"
for(int i = 1; i <= 5; i++){
    for(int j = 1; j <= i; j++){
        System.out.print(j + " ");
    }
    System.out.println();
}
```

Output:

```text id="a12"
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
```

---

## Pattern 2 (Same number row)

```java id="a13"
for(int i = 1; i <= 5; i++){
    for(int j = 1; j <= i; j++){
        System.out.print(i + " ");
    }
    System.out.println();
}
```

Output:

```text id="a14"
1
2 2
3 3 3
4 4 4 4
5 5 5 5 5
```

---

# 6. Alphabet Patterns

```java id="a15"
for(char i = 'A'; i <= 'E'; i++){
    for(char j = 'A'; j <= i; j++){
        System.out.print(j + " ");
    }
    System.out.println();
}
```

Output:

```text id="a16"
A
A B
A B C
A B C D
A B C D E
```

---

# 7. Pyramid Pattern

```java id="a17"
for(int i = 1; i <= 5; i++){
    for(int j = 5; j > i; j--){
        System.out.print(" ");
    }
    for(int k = 1; k <= (2*i-1); k++){
        System.out.print("*");
    }
    System.out.println();
}
```

Output:

```text id="a18"
    *
   ***
  *****
 *******
*********
```

---

# 8. Interview Coding Patterns

Most asked patterns:

```text id="a19"
Star patterns
Number triangle
Floyd's triangle
Pyramid patterns
Reverse patterns
```

---

# 9. break & continue in Nested Loops

## break example

```java id="a20"
for(int i = 1; i <= 3; i++){
    for(int j = 1; j <= 3; j++){
        if(j == 2){
            break;
        }
        System.out.println(i + " " + j);
    }
}
```

---

## continue example

```java id="a21"
for(int i = 1; i <= 3; i++){
    for(int j = 1; j <= 3; j++){
        if(j == 2){
            continue;
        }
        System.out.println(i + " " + j);
    }
}
```

---

# 10. Selenium Real Usage

## Iterating Web Elements

```java id="a22"
List<WebElement> links = driver.findElements(By.tagName("a"));

for(WebElement link : links){
    System.out.println(link.getText());
}
```

---

## Table Handling

```java id="a23"
List<WebElement> rows = driver.findElements(By.xpath("//table/tr"));

for(WebElement row : rows){
    List<WebElement> cols = row.findElements(By.tagName("td"));
    
    for(WebElement col : cols){
        System.out.print(col.getText() + " ");
    }
    System.out.println();
}
```

---

# 11. API Real Usage

```java id="a24"
List<String> users = response.jsonPath().getList("data.name");

for(String user : users){
    System.out.println(user);
}
```

---

# 12. Common Interview Mistakes

## Mistake 1: Wrong loop boundary

```java id="a25"
for(int i = 0; i <= arr.length; i++)
```

Correct:

```java id="a26"
i < arr.length
```

---

## Mistake 2: Infinite nested loop

---

## Mistake 3: Using wrong loop type for patterns

---

# 13. Short Notes

✔ Nested loops = loop inside loop
✔ Pattern printing = interview favorite
✔ Time complexity increases with nesting
✔ break exits loop
✔ continue skips iteration
✔ for loop best for patterns

---

# 14. Revision Sheet

```text id="a27"
Nested Loop → i + j loop

Patterns → star/number/alphabet

Time Complexity → O(n²)

break → exit loop

continue → skip iteration

Selenium → used for element iteration
```

---

# Interview Quick Summary

* Nested loops = pattern building tool
* Used in coding + automation
* Always optimize loops
* Patterns are highly asked in interviews
* Selenium heavily uses loops for UI traversal

---

# Part 3 Completed

Next Part:

Part 4 - Advanced Loop Problems & Interview Coding Questions

Topics:

* Prime numbers
* Fibonacci series
* Factorial using loops
* Reverse number logic
* Array + loop problems
* Real interview coding patterns
