# Java Abstraction Master Guide – Part 8

## Abstraction in Multithreading (Interview Deep Dive)

---

# Table of Contents

1. Introduction to Multithreading Abstraction
2. Why Abstraction is Needed in Threads
3. Thread vs Runnable (Core Concept)
4. Runnable Interface Deep Dive
5. Thread Class vs Runnable Interface
6. Callable Interface
7. Future and FutureTask
8. ExecutorService Abstraction
9. Thread Pool Concept
10. CompletableFuture (Modern Java)
11. JVM Thread Model
12. Context Switching Concept
13. Real Project Usage
14. Selenium Parallel Execution
15. Spring Boot Async Processing
16. Common Coding Scenarios
17. Common Mistakes
18. Advanced Interview Questions
19. Tricky Interview Questions
20. Revision Notes
21. Cheat Sheet
22. Summary
23. Practice Questions

---

# 1. Introduction to Multithreading Abstraction

Multithreading in Java is heavily based on abstraction.

Java hides:

* Thread creation complexity
* CPU scheduling
* Context switching
* Resource allocation

Developer focuses only on:

```text id="m1"
WHAT task to execute
```

not:

```text id="m2"
HOW OS executes threads
```

---

# 2. Why Abstraction is Needed in Threads

Without abstraction:

```text id="m3"
Direct OS thread handling
Manual scheduling
Complex memory handling
```

With abstraction:

```text id="m4"
Runnable / Callable / ExecutorService
```

---

# 3. Thread vs Runnable (Core Concept)

---

## Thread Class

Represents actual thread execution.

```java id="t1"
Thread t = new Thread();
```

---

## Runnable Interface

Represents task.

```java id="t2"
Runnable task = () -> System.out.println("Task");
```

---

# Key Idea:

```text id="m5"
Runnable = WHAT to do
Thread = HOW to run it
```

---

# 4. Runnable Interface Deep Dive

---

Example:

```java id="r1"
class MyTask implements Runnable {

    public void run() {
        System.out.println("Task executed");
    }
}
```

---

Execution:

```java id="r2"
Thread t = new Thread(new MyTask());
t.start();
```

---

Output:

```text id="r3"
Task executed
```

---

# Why Runnable is Better?

* Separates task and execution
* Supports multiple inheritance
* Promotes loose coupling

---

# 5. Thread vs Runnable

| Feature           | Thread       | Runnable  |
| ----------------- | ------------ | --------- |
| Type              | Class        | Interface |
| Inheritance       | Not flexible | Flexible  |
| Reusability       | Low          | High      |
| Abstraction Level | Low          | High      |

---

# 6. Callable Interface

Runnable:

```text id="m6"
No return value
```

Callable:

```text id="m7"
Returns value + exception handling
```

---

Example:

```java id="c1"
Callable<Integer> task = () -> 10 + 20;
```

---

Execution:

```java id="c2"
ExecutorService service =
    Executors.newSingleThreadExecutor();

Future<Integer> result =
    service.submit(task);

System.out.println(result.get());
```

Output:

```text id="c3"
30
```

---

# 7. Future and FutureTask

---

## Future

Represents result of async computation.

```java id="f1"
Future<Integer> future;
```

---

## FutureTask

Wrapper for Callable.

```java id="f2"
FutureTask<Integer> task =
    new FutureTask<>(callable);
```

---

# 8. ExecutorService Abstraction

Very important interview topic.

---

Instead of:

```text id="m8"
Manually creating threads
```

We use:

```java id="e1"
ExecutorService executor =
    Executors.newFixedThreadPool(5);
```

---

Submit task:

```java id="e2"
executor.submit(() ->
    System.out.println("Task"));
```

---

# Why ExecutorService?

* Thread reuse
* Better performance
* Resource management
* Scalable architecture

---

# 9. Thread Pool Concept

Instead of creating new threads:

```text id="m9"
Reuse existing threads
```

---

Types:

```text id="m10"
Fixed Thread Pool
Cached Thread Pool
Single Thread Executor
Scheduled Thread Pool
```

---

# 10. CompletableFuture (Modern Java)

Advanced async programming.

---

Example:

```java id="cf1"
CompletableFuture.supplyAsync(() -> 10)
    .thenApply(x -> x * 2)
    .thenAccept(System.out::println);
```

Output:

```text id="cf2"
20
```

---

# Advantages:

* Non-blocking
* Functional style
* Pipeline processing

---

# 11. JVM Thread Model

JVM manages:

* Thread scheduling
* Memory allocation
* Stack per thread

---

Memory:

```text id="jvm1"
Each thread has own stack
Shared heap memory
```

---

# 12. Context Switching

When CPU switches between threads:

```text id="cs1"
Save state of thread A
Load state of thread B
```

---

This is abstracted from developer.

---

# 13. Real Project Usage

---

## E-commerce Order Processing

```java id="p1"
ExecutorService service =
    Executors.newFixedThreadPool(10);
```

---

Tasks:

* Payment
* Inventory update
* Notification

---

# 14. Selenium Parallel Execution

TestNG + Threads:

```java id="s1"
@Test(threadPoolSize = 3)
public void testLogin() {

}
```

---

Selenium Grid:

* Multiple browsers
* Parallel execution
* Remote execution

---

# 15. Spring Boot Async Processing

---

Enable async:

```java id="sp1"
@EnableAsync
```

---

Service:

```java id="sp2"
@Async
public void sendEmail() {

}
```

---

Spring uses thread pool abstraction internally.

---

# 16. Common Coding Scenarios

---

## Scenario 1: Parallel Tasks

```java id="cs2"
ExecutorService service =
    Executors.newFixedThreadPool(3);

service.submit(() ->
    System.out.println("Task1"));
```

---

## Scenario 2: Return Value Task

```java id="cs3"
Callable<String> task =
    () -> "Hello";
```

---

# 17. Common Mistakes

---

## Mistake 1

Using Thread instead of Runnable

```java id="cm1"
class Task extends Thread {}
```

Bad design.

---

## Mistake 2

Not shutting down ExecutorService

```java id="cm2"
executor.shutdown();
```

---

## Mistake 3

Blocking CompletableFuture unnecessarily

---

# 18. Advanced Interview Questions

---

## Q1

Why use Runnable instead of Thread?

Answer:

Runnable provides better abstraction and separation of concerns.

---

## Q2

What is ExecutorService?

Answer:

A framework to manage thread lifecycle and execution.

---

## Q3

Difference between Callable and Runnable?

Answer:

| Runnable     | Callable            |
| ------------ | ------------------- |
| No return    | Returns value       |
| No exception | Can throw exception |

---

## Q4

What is CompletableFuture?

Answer:

Async programming model with chaining support.

---

## Q5

What is thread pool?

Answer:

Reusable pool of threads for executing tasks.

---

# 19. Tricky Interview Questions

---

## Q1

Can Runnable return value?

Answer:

No.

---

## Q2

Can we reuse Thread object?

Answer:

No.

---

## Q3

What happens if ExecutorService is not shutdown?

Answer:

Memory leak and thread leakage.

---

## Q4

Is CompletableFuture blocking?

Answer:

No, it is non-blocking.

---

## Q5

Can multiple threads share same Runnable?

Answer:

Yes.

---

# 20. Revision Notes

```text id="rev1"
Multithreading Abstraction
--------------------------

Runnable = Task

Thread = Execution

ExecutorService = Thread Management

Callable = Task with Return Value

CompletableFuture = Async Pipeline

JVM handles:
-------------
Scheduling
Memory
Context Switching
```

---

# 21. Cheat Sheet

```text id="cs1"
Runnable -> task
Thread -> execution
Callable -> return task
ExecutorService -> thread manager
Future -> result holder
CompletableFuture -> async pipeline
```

---

# 22. Summary

Multithreading is deeply abstracted in Java.

Key points:

* Developers define tasks only
* JVM handles execution
* ExecutorService manages threads
* CompletableFuture enables modern async programming

Used in:

* Selenium parallel execution
* Spring Boot async processing
* Microservices
* High-performance systems

---

# 23. Practice Questions

1. What is Runnable?
2. What is Thread?
3. Why use Runnable instead of Thread?
4. What is ExecutorService?
5. What is thread pool?
6. Difference between Callable and Runnable?
7. What is Future?
8. What is CompletableFuture?
9. Explain JVM thread model.
10. What is context switching?
11. How is multithreading abstraction achieved?
12. Explain Selenium parallel execution.
13. Explain Spring async processing.
14. What happens if executor is not shut down?
15. Explain real-world use case of threads.
