# Java Loops & Conditional Statements Master Guide

# Part 4 - Advanced Loop Problems (Interview Coding)

---

# Table of Contents

1. Introduction
2. Factorial Using Loop
3. Fibonacci Series
4. Prime Number Check
5. Prime Numbers in Range
6. Reverse a Number
7. Palindrome Number
8. Sum of Digits
9. Armstrong Number
10. Array Problems Using Loops
11. Loop Optimization Tips
12. Selenium Real Usage
13. API Real Usage
14. Common Interview Mistakes
15. Short Notes
16. Revision Sheet

---

# 1. Introduction

Advanced loop problems are:

```text id="b1"
Most asked in Java + Automation interviews
```

They test:

* Logic building
* Mathematical thinking
* Loop control mastery

---

# 2. Factorial Using Loop

```java id="b2"
int num = 5;
int fact = 1;

for(int i = 1; i <= num; i++){
    fact = fact * i;
}

System.out.println(fact);
```

Output:

```text id="b3"
120
```

---

# 3. Fibonacci Series

```java id="b4"
int n = 10;
int a = 0, b = 1;

for(int i = 1; i <= n; i++){
    System.out.print(a + " ");
    
    int c = a + b;
    a = b;
    b = c;
}
```

Output:

```text id="b5"
0 1 1 2 3 5 8 13 21 34
```

---

# 4. Prime Number Check

```java id="b6"
int num = 7;
boolean isPrime = true;

for(int i = 2; i < num; i++){
    if(num % i == 0){
        isPrime = false;
        break;
    }
}

System.out.println(isPrime);
```

Output:

```text id="b7"
true
```

---

# 5. Prime Numbers in Range

```java id="b8"
for(int num = 2; num <= 20; num++){
    boolean isPrime = true;

    for(int i = 2; i < num; i++){
        if(num % i == 0){
            isPrime = false;
            break;
        }
    }

    if(isPrime){
        System.out.print(num + " ");
    }
}
```

Output:

```text id="b9"
2 3 5 7 11 13 17 19
```

---

# 6. Reverse a Number

```java id="b10"
int num = 1234;
int rev = 0;

while(num != 0){
    int digit = num % 10;
    rev = rev * 10 + digit;
    num = num / 10;
}

System.out.println(rev);
```

Output:

```text id="b11"
4321
```

---

# 7. Palindrome Number

```java id="b12"
int num = 121;
int temp = num;
int rev = 0;

while(num != 0){
    int digit = num % 10;
    rev = rev * 10 + digit;
    num = num / 10;
}

if(temp == rev){
    System.out.println("Palindrome");
}
```

Output:

```text id="b13"
Palindrome
```

---

# 8. Sum of Digits

```java id="b14"
int num = 1234;
int sum = 0;

while(num != 0){
    sum += num % 10;
    num = num / 10;
}

System.out.println(sum);
```

Output:

```text id="b15"
10
```

---

# 9. Armstrong Number

```java id="b16"
int num = 153;
int temp = num;
int sum = 0;

while(num != 0){
    int digit = num % 10;
    sum += digit * digit * digit;
    num = num / 10;
}

if(temp == sum){
    System.out.println("Armstrong");
}
```

Output:

```text id="b17"
Armstrong
```

---

# 10. Array Problems Using Loops

## Find Largest Element

```java id="b18"
int arr[] = {10, 20, 5, 40, 15};

int max = arr[0];

for(int i = 1; i < arr.length; i++){
    if(arr[i] > max){
        max = arr[i];
    }
}

System.out.println(max);
```

Output:

```text id="b19"
40
```

---

## Sum of Array

```java id="b20"
int arr[] = {1,2,3,4};

int sum = 0;

for(int i = 0; i < arr.length; i++){
    sum += arr[i];
}

System.out.println(sum);
```

Output:

```text id="b21"
10
```

---

# 11. Loop Optimization Tips

```text id="b22"
✔ Break early when condition met  
✔ Avoid nested loops when possible  
✔ Use while for unknown iterations  
✔ Use for-each for arrays  
✔ Cache arr.length in variable  
```

---

# 12. Selenium Real Usage

## Validate Multiple Elements

```java id="b23"
List<WebElement> links = driver.findElements(By.tagName("a"));

for(WebElement link : links){
    if(link.getText().contains("Login")){
        link.click();
        break;
    }
}
```

---

## Retry Mechanism

```java id="b24"
for(int i = 0; i < 3; i++){
    try{
        driver.get("https://test.com");
        break;
    } catch(Exception e){
        continue;
    }
}
```

---

# 13. API Real Usage

```java id="b25"
List<Integer> ids = response.jsonPath().getList("data.id");

for(int id : ids){
    System.out.println(id);
}
```

---

# 14. Common Interview Mistakes

## Mistake 1: Wrong prime logic

```java id="b26"
for(int i = 2; i <= num; i++)
```

Should be:

```text id="b27"
i < num
```

---

## Mistake 2: Not resetting variables in loops

---

## Mistake 3: Infinite while loop

---

# 15. Short Notes

✔ Factorial = multiplication loop
✔ Fibonacci = previous + current
✔ Prime = divisible check
✔ Reverse number = mod/div logic
✔ Armstrong = power sum
✔ Arrays = loop traversal

---

# 16. Revision Sheet

```text id="b28"
Factorial → product loop

Fibonacci → a + b logic

Prime → divisibility check

Reverse → % and /

Palindrome → reverse compare

Array → traversal loop
```

---

# Interview Quick Summary

* These are **most asked coding questions**
* Always use loops efficiently
* Break early when possible
* Arrays + loops = very important
* Logic clarity matters more than syntax

---

# Part 4 Completed

Next Part:

Part 5 - Loop Optimization + Interview Patterns + Framework Usage

Topics:

* Sliding window style loops
* Performance optimization
* Selenium advanced iteration
* API batch processing
* Real framework design patterns
