# Java Loops & Conditional Statements Master Guide

# Part 2 - Loops Basics in Java

---

# Table of Contents

1. Introduction to Loops
2. Why Loops are Important
3. for Loop
4. while Loop
5. do-while Loop
6. Enhanced for Loop (for-each)
7. break Statement
8. continue Statement
9. Loop Flow Visualization
10. Real-time Automation Usage
11. Common Interview Mistakes
12. Short Notes
13. Revision Sheet

---

# 1. Introduction to Loops

Loops are used to execute a block of code:

```text id="l1"
multiple times automatically
```

Without loops:

```text id="l2"
You would repeat code manually
```

---

# 2. Why Loops are Important

Used in:

* Selenium automation (find multiple elements)
* API response iteration
* Data processing
* Test data execution
* Report generation

---

# 3. for Loop

Used when number of iterations is known.

```java id="l3"
for(int i = 1; i <= 5; i++){
    System.out.println(i);
}
```

Output:

```text id="l4"
1 2 3 4 5
```

---

# 4. while Loop

Used when condition is checked before execution.

```java id="l5"
int i = 1;

while(i <= 5){
    System.out.println(i);
    i++;
}
```

Output:

```text id="l6"
1 2 3 4 5
```

---

# 5. do-while Loop

Executes at least once.

```java id="l7"
int i = 1;

do{
    System.out.println(i);
    i++;
} while(i <= 5);
```

Output:

```text id="l8"
1 2 3 4 5
```

---

Important Rule:

```text id="l9"
do-while → executes once even if condition is false
```

---

# 6. Enhanced for Loop (for-each)

Used for arrays and collections.

```java id="l10"
int arr[] = {1,2,3,4};

for(int num : arr){
    System.out.println(num);
}
```

Output:

```text id="l11"
1 2 3 4
```

---

# 7. break Statement

Stops loop immediately.

```java id="l12"
for(int i = 1; i <= 10; i++){
    if(i == 5){
        break;
    }
    System.out.println(i);
}
```

Output:

```text id="l13"
1 2 3 4
```

---

# 8. continue Statement

Skips current iteration.

```java id="l14"
for(int i = 1; i <= 5; i++){
    if(i == 3){
        continue;
    }
    System.out.println(i);
}
```

Output:

```text id="l15"
1 2 4 5
```

---

# 9. Loop Flow Visualization

## for loop

```text id="l16"
Initialize → Condition → Execute → Increment → Repeat
```

## while loop

```text id="l17"
Condition → Execute → Repeat
```

## do-while loop

```text id="l18"
Execute → Condition → Repeat
```

---

# 10. Real-time Automation Usage

## Selenium: Multiple Elements

```java id="l19"
List<WebElement> buttons = driver.findElements(By.tagName("button"));

for(WebElement btn : buttons){
    System.out.println(btn.getText());
}
```

---

## API Response Iteration

```java id="l20"
List<String> names = response.jsonPath().getList("data.name");

for(String name : names){
    System.out.println(name);
}
```

---

## Retry Logic Example

```java id="l21"
for(int i = 0; i < 3; i++){
    try{
        System.out.println("Attempt " + i);
        break;
    } catch(Exception e){
        continue;
    }
}
```

---

# 11. Common Interview Mistakes

## Mistake 1: Infinite loop

```java id="l22"
while(true){
    System.out.println("Hello");
}
```

---

## Mistake 2: Missing increment

```java id="l23"
while(i < 5){
    System.out.println(i);
}
```

---

## Mistake 3: Using wrong loop type

* for → known iterations
* while → unknown iterations
* do-while → must execute once

---

# 12. Short Notes

✔ for → fixed iterations
✔ while → condition-based loop
✔ do-while → runs at least once
✔ for-each → arrays/collections
✔ break → stop loop
✔ continue → skip iteration

---

# 13. Revision Sheet

```text id="l24"
for → known iterations

while → condition check first

do-while → execute first

for-each → collections/arrays

break → exit loop

continue → skip iteration
```

---

# Interview Quick Summary

* Loops reduce repetition
* for loop is most used
* for-each is best for collections
* break stops execution
* continue skips iteration
* avoid infinite loops

---

# Part 2 Completed

Next Part:

Part 3 - Advanced Loops + Nested Loops + Patterns

Topics:

* Nested loops
* Pattern printing (stars, numbers)
* Loop complexity
* Interview coding patterns
* Selenium iteration patterns
