# Java Variables Interview Master Guide
# Part 7 - Multithreading Variables & Concurrency

## Table of Contents

1. Introduction to Multithreading
2. Java Memory Model (JMM)
3. Shared Variables
4. Race Conditions
5. Synchronization
6. volatile Keyword
7. Atomic Variables
8. ThreadLocal Variables
9. Visibility vs Atomicity
10. Happens-Before Relationship
11. Locks & Monitors
12. Concurrent Collections
13. Selenium Parallel Execution
14. TestNG Parallel Execution
15. Framework Design Best Practices
16. Interview Questions
17. MCQs
18. Quick Revision Notes

---

# 1. Introduction to Multithreading

Multithreading allows multiple threads to execute concurrently.

Example:

```java
Thread t1 = new Thread();
Thread t2 = new Thread();
```

Benefits:

- Better CPU utilization
- Faster execution
- Parallel task processing

---

# 2. Java Memory Model (JMM)

Defines how threads interact with memory.

JMM controls:

- Visibility
- Ordering
- Atomicity

---

## Memory Structure

```text
Main Memory
     |
------------------
|       |        |
T1      T2       T3
Working Working Working
Memory  Memory  Memory
```

Each thread may cache variables.

---

# 3. Shared Variables

Shared variable accessed by multiple threads.

Example:

```java
class Counter {

    int count = 0;
}
```

Multiple threads accessing count.

Potential issue:

Race Condition.

---

# 4. Race Conditions

Occurs when multiple threads modify same variable simultaneously.

Example:

```java
count++;
```

Actually executes as:

```java
Read
Increment
Write
```

Not atomic.

---

## Scenario

Thread1 reads 5

Thread2 reads 5

Thread1 writes 6

Thread2 writes 6

Expected:

7

Actual:

6

---

# Interview Definition

Race Condition:

Outcome depends on thread execution order.

---

# 5. Synchronization

Used to prevent concurrent modification issues.

Example:

```java
synchronized void increment() {

    count++;
}
```

Only one thread executes at a time.

---

## Monitor Lock

Every Java object has monitor lock.

```java
synchronized(this)
```

Thread acquires lock before execution.

---

# Advantages

- Data consistency
- Thread safety

Disadvantages

- Reduced performance
- Lock contention

---

# 6. volatile Keyword

Most Asked Interview Topic

Example:

```java
volatile boolean running = true;
```

---

# Problem Without volatile

Thread may cache variable.

Updates not visible immediately.

---

Example

```java
while(running) {

}
```

Another thread:

```java
running = false;
```

Loop may never stop.

---

# Solution

```java
volatile boolean running;
```

Always read latest value from main memory.

---

# What volatile Guarantees

✔ Visibility

❌ Atomicity

---

# Interview Question

Can volatile replace synchronized?

No.

volatile provides visibility only.

---

# 7. Atomic Variables

Package:

```java
java.util.concurrent.atomic
```

Example:

```java
AtomicInteger counter =
new AtomicInteger(0);
```

---

Increment

```java
counter.incrementAndGet();
```

Thread-safe operation.

---

# Why Atomic Variables?

Alternative to synchronization.

Better performance.

---

# Common Atomic Classes

```java
AtomicInteger
AtomicLong
AtomicBoolean
AtomicReference
```

---

# 8. ThreadLocal Variables

Critical Selenium Interview Topic

Provides thread-specific storage.

Example:

```java
ThreadLocal<WebDriver> driver =
new ThreadLocal<>();
```

---

Set Value

```java
driver.set(new ChromeDriver());
```

Get Value

```java
driver.get();
```

---

# Why Needed?

Parallel execution.

Each thread gets separate WebDriver.

---

# Memory Diagram

```text
Thread1 -> Driver1

Thread2 -> Driver2

Thread3 -> Driver3
```

---

# Selenium Best Practice

```java
private static ThreadLocal<WebDriver>
driver = new ThreadLocal<>();
```

Most enterprise frameworks use this pattern.

---

# 9. Visibility vs Atomicity

Visibility

Can thread see latest value?

Handled by:

```java
volatile
```

---

Atomicity

Can operation complete as single unit?

Handled by:

```java
synchronized
AtomicInteger
```

---

Example

```java
count++;
```

Visible? Maybe.

Atomic? No.

---

# 10. Happens-Before Relationship

JMM Concept

Guarantees memory consistency.

---

Rule

If A happens-before B

Then B sees effects of A.

---

Examples

Thread Start Rule

```java
thread.start();
```

Actions before start visible to thread.

---

Thread Join Rule

```java
thread.join();
```

Actions completed before join returns.

---

volatile Rule

Write happens-before read.

---

# 11. Locks & Monitors

## Intrinsic Lock

```java
synchronized(this)
```

Uses object monitor.

---

## ReentrantLock

```java
Lock lock =
new ReentrantLock();
```

---

Advantages

- Try Lock
- Fair Locking
- Explicit Unlock

---

Example

```java
lock.lock();

try {

}
finally {

    lock.unlock();
}
```

---

# 12. Concurrent Collections

Thread-safe collections.

---

## ConcurrentHashMap

```java
ConcurrentHashMap<String,String>
map = new ConcurrentHashMap<>();
```

---

## CopyOnWriteArrayList

```java
CopyOnWriteArrayList<String>
list;
```

Useful for read-heavy applications.

---

# Why Not HashMap?

HashMap is not thread-safe.

Can cause data corruption.

---

# 13. Selenium Parallel Execution

Most Asked Framework Question

---

Bad Design

```java
public static WebDriver driver;
```

Problem:

Shared by all threads.

---

Thread1

Driver = Chrome

Thread2

Driver = Edge

Thread overwrite occurs.

---

Result

Random failures.

---

# Correct Design

```java
ThreadLocal<WebDriver> driver;
```

Each thread gets separate driver.

---

# Example Framework

```java
public class DriverManager {

    private static ThreadLocal<WebDriver>
    driver = new ThreadLocal<>();
}
```

---

# 14. TestNG Parallel Execution

Example

```xml
<suite parallel="tests"
thread-count="5">
```

Multiple threads execute.

---

Need thread-safe driver management.

---

Common Interview Question

Why static WebDriver fails in parallel execution?

Answer:

Shared variable overwritten by multiple threads.

---

# 15. Framework Design Best Practices

Use:

✔ ThreadLocal

✔ Atomic Variables

✔ Concurrent Collections

Avoid:

✘ Global Mutable Static Variables

✘ Shared WebDriver

✘ Unsynchronized Counters

---

# Frequently Asked Interview Questions

### Q1. What is Race Condition?

Multiple threads updating shared data simultaneously.

---

### Q2. What does volatile do?

Ensures visibility.

---

### Q3. Does volatile guarantee atomicity?

No.

---

### Q4. Difference between synchronized and volatile?

synchronized:

Visibility + Atomicity

volatile:

Visibility only

---

### Q5. What is AtomicInteger?

Thread-safe integer operations.

---

### Q6. Why use ThreadLocal?

Thread-specific storage.

---

### Q7. Why ThreadLocal in Selenium?

Parallel execution support.

---

### Q8. What is Happens-Before?

Memory visibility guarantee.

---

### Q9. Is HashMap thread-safe?

No.

---

### Q10. Best WebDriver design for parallel execution?

ThreadLocal<WebDriver>

---

# MCQs

Q1. volatile guarantees?

A. Atomicity
B. Visibility

Answer: B

---

Q2. AtomicInteger provides?

A. Thread-safe increment
B. Visibility only

Answer: A

---

Q3. Which collection is thread-safe?

A. HashMap
B. ConcurrentHashMap

Answer: B

---

Q4. Which keyword provides locking?

A. volatile
B. synchronized

Answer: B

---

Q5. Selenium parallel execution should use?

A. Static Driver
B. ThreadLocal Driver

Answer: B

---

# Quick Revision Notes

RACE CONDITION

- Shared variable issue

SYNCHRONIZED

- Visibility + Atomicity

VOLATILE

- Visibility only

ATOMICINTEGER

- Thread-safe operations

THREADLOCAL

- Per-thread storage

HASHMAP

- Not thread-safe

CONCURRENTHASHMAP

- Thread-safe

STATIC WEBDRIVER

- Bad for parallel execution

THREADLOCAL WEBDRIVER

- Recommended

---

# One Minute Interview Cheat Sheet

volatile

→ Visibility

synchronized

→ Visibility + Atomicity

AtomicInteger

→ Lock-free thread-safe counter

ThreadLocal

→ Thread-specific variables

Race Condition

→ Multiple threads modifying same data

ConcurrentHashMap

→ Thread-safe map

Selenium Parallel Framework

→ ThreadLocal<WebDriver>

Most Asked Interview Answer:

Static WebDriver causes failures in parallel execution because all threads share the same driver instance. ThreadLocal<WebDriver> provides isolated browser instances for each thread.
