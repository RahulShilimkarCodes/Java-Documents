# Java Loops & Conditional Statements Master Guide

# Part 5 - Loop Optimization, Patterns & Framework Usage

---

# Table of Contents

1. Introduction
2. Why Loop Optimization Matters
3. Time Complexity Optimization
4. Sliding Window Style Looping
5. Two Pointer Logic (Loop-Based)
6. Loop Optimization Techniques
7. Nested Loop Optimization
8. Selenium Advanced Loop Usage
9. API Batch Processing with Loops
10. Framework Design Patterns Using Loops
11. Common Interview Scenarios
12. Performance Bottlenecks
13. Short Notes
14. Revision Sheet

---

# 1. Introduction

Loop optimization is about:

```text id="c1"
Reducing unnecessary iterations and improving performance
```

Used heavily in:

* Automation frameworks
* Backend services
* API processing
* Large dataset handling

---

# 2. Why Loop Optimization Matters

Bad loops cause:

```text id="c2"
Slow execution + high CPU usage + memory overhead
```

Optimized loops:

```text id="c3"
Faster execution + scalable frameworks
```

---

# 3. Time Complexity Optimization

## Before Optimization

```java id="c4"
for(int i = 0; i < n; i++){
    for(int j = 0; j < n; j++){
        System.out.println(i + j);
    }
}
```

Time:

```text id="c5"
O(n²)
```

---

## After Optimization (when possible)

Reduce nested loops:

```text id="c6"
Use HashMap / Set / precomputation
```

---

# 4. Sliding Window Style Looping

Used in substring problems.

Example:

```java id="c7"
String s = "abcabcbb";

for(int i = 0; i < s.length() - 2; i++){
    String window = s.substring(i, i+3);
    System.out.println(window);
}
```

Output:

```text id="c8"
abc
bca
cab
abc
cbb
```

---

# 5. Two Pointer Logic (Loop-Based)

```java id="c9"
int i = 0, j = arr.length - 1;

while(i < j){
    System.out.println(arr[i] + " " + arr[j]);
    i++;
    j--;
}
```

Used in:

* Searching pairs
* Reverse operations
* Optimization problems

---

# 6. Loop Optimization Techniques

## Technique 1: Break early

```java id="c10"
for(int i = 0; i < n; i++){
    if(arr[i] == target){
        break;
    }
}
```

---

## Technique 2: Cache length

```java id="c11"
int len = arr.length;
for(int i = 0; i < len; i++)
```

---

## Technique 3: Avoid repeated method calls

Bad:

```java id="c12"
for(int i = 0; i < list.size(); i++)
```

Good:

```java id="c13"
int size = list.size();
for(int i = 0; i < size; i++)
```

---

## Technique 4: Use HashSet instead of nested loops

```java id="c14"
Set<Integer> set = new HashSet<>();
```

---

# 7. Nested Loop Optimization

## Problem:

```text id="c15"
O(n²) complexity
```

## Fix:

* Use maps
* Use indexing
* Pre-store values

---

Example:

```java id="c16"
Map<Integer, Integer> map = new HashMap<>();

for(int i : arr){
    map.put(i, map.getOrDefault(i, 0) + 1);
}
```

---

# 8. Selenium Advanced Loop Usage

## Clicking Specific Element

```java id="c17"
List<WebElement> buttons = driver.findElements(By.tagName("button"));

for(WebElement btn : buttons){
    if(btn.getText().equals("Login")){
        btn.click();
        break;
    }
}
```

---

## Handling Dynamic Tables

```java id="c18"
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

## Optimized Element Search

```java id="c19"
for(WebElement e : elements){
    if(e.isDisplayed()){
        e.click();
        break;
    }
}
```

---

# 9. API Batch Processing with Loops

## Process List Response

```java id="c20"
List<String> users = response.jsonPath().getList("data.name");

for(String user : users){
    System.out.println("Processing: " + user);
}
```

---

## Filter Data

```java id="c21"
for(String user : users){
    if(user.startsWith("A")){
        System.out.println(user);
    }
}
```

---

# 10. Framework Design Patterns Using Loops

## Retry Mechanism

```java id="c22"
for(int i = 0; i < 3; i++){
    try{
        System.out.println("Test execution attempt " + i);
        break;
    } catch(Exception e){
        continue;
    }
}
```

---

## Test Data Execution Loop

```java id="c23"
for(String data : testData){
    executeTest(data);
}
```

---

## Parallel Concept (Logical)

```text id="c24"
Loop → distribute test cases → execution engine
```

---

# 11. Common Interview Scenarios

## Scenario 1: Slow framework

Cause:

```text id="c25"
Nested loops + repeated DOM calls
```

Fix:

```text id="c26"
Cache elements + reduce DOM access
```

---

## Scenario 2: Flaky automation

Cause:

```text id="c27"
No break condition in loop
```

Fix:

```text id="c28"
Add break after match
```

---

## Scenario 3: API slow processing

Cause:

```text id="c29"
Repeated parsing in loop
```

Fix:

```text id="c30"
Parse once, reuse result
```

---

# 12. Performance Bottlenecks

```text id="c31"
❌ Nested loops on large data
❌ Repeated size() calls
❌ Repeated JSON parsing
❌ Unnecessary DOM calls in Selenium
```

---

# 13. Short Notes

✔ Break early improves speed
✔ Cache values inside loops
✔ Avoid nested loops when possible
✔ Use HashMap/Set for optimization
✔ Selenium loops should include break
✔ API loops should reuse parsed data

---

# 14. Revision Sheet

```text id="c32"
Sliding Window → substring optimization

Two Pointer → i and j traversal

Break → exit early

Cache → avoid repeated calls

Hashing → replace nested loops

Selenium → loop + click + break

API → loop + JSON extraction
```

---

# Interview Quick Summary

* Loop optimization is critical in real projects
* Always avoid unnecessary iterations
* Replace nested loops with data structures
* Selenium heavily depends on optimized loops
* API frameworks rely on loop efficiency

---

# Part 5 Completed

Next Part:

👉 Part 6 - Final Revision + Mixed Interview Coding + Real Framework Scenarios

Topics:

* Mixed loops + conditionals
* Full interview coding set
* Framework design questions
* Real-time debugging scenarios
* Final revision cheat sheet
