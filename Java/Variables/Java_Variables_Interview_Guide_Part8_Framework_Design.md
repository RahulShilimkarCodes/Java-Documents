# Java Variables Interview Master Guide
# Part 8 - Framework-Level Variables & Real Project Design

## Table of Contents

1. Variables in Automation Frameworks
2. DriverManager Design
3. ThreadLocal Driver Factory
4. ConfigReader Variables
5. Constants Management
6. Test Data Variables
7. Environment Variables
8. Singleton Pattern
9. Dependency Injection Concepts
10. Static vs Instance Variables in Frameworks
11. REST Assured Framework Variables
12. Playwright Framework Variables
13. Real Framework Structure
14. Real Interview Scenarios
15. Advanced Interview Questions
16. MCQs
17. Quick Revision Notes

---

# 1. Variables in Automation Frameworks

Variables are the backbone of framework design.

Used for:

- Driver Management
- Configuration Management
- Test Data Storage
- Environment Switching
- Reporting
- API Utilities

---

# Framework Layers

```text
Tests
 ↓
Pages
 ↓
Utilities
 ↓
Driver Manager
 ↓
Configuration
```

Variables exist at every layer.

---

# 2. DriverManager Design

Most Asked Selenium Interview Topic

Example:

```java
public class DriverManager {

    private static WebDriver driver;
}
```

---

## Why Driver Variable Required?

Stores browser session.

Used throughout framework.

---

## Problem

```java
private static WebDriver driver;
```

Fails during parallel execution.

Shared by all threads.

---

# Better Solution

```java
private static ThreadLocal<WebDriver>
driver = new ThreadLocal<>();
```

Thread-safe implementation.

---

# 3. ThreadLocal Driver Factory

Enterprise Framework Design

```java
public class DriverFactory {

    private static ThreadLocal<WebDriver>
    driver = new ThreadLocal<>();
}
```

---

## Set Driver

```java
driver.set(new ChromeDriver());
```

---

## Get Driver

```java
driver.get();
```

---

## Remove Driver

```java
driver.remove();
```

Prevents memory leaks.

---

# Interview Question

Why use ThreadLocal?

Answer:

Provides separate driver instance per thread.

---

# 4. ConfigReader Variables

Stores framework configuration.

Example:

config.properties

```properties
browser=chrome
url=https://testsite.com
timeout=30
```

---

Java Class

```java
Properties prop;
```

---

Methods

```java
getBrowser()
getUrl()
getTimeout()
```

---

# Why Not Hardcode?

Bad:

```java
driver.get("https://testsite.com");
```

Good:

```java
driver.get(config.getUrl());
```

---

# 5. Constants Management

Centralized constants.

Example:

```java
public class Constants {

    public static final int TIMEOUT = 30;

    public static final String URL =
    "https://testsite.com";
}
```

---

Benefits

- Easy maintenance
- Single source of truth

---

# Interview Question

Why static final?

static

Shared by all objects.

final

Cannot change.

---

# 6. Test Data Variables

Example

```java
String username =
"testuser";

String password =
"password123";
```

---

Better Design

Excel

CSV

JSON

Database

---

Example

```java
User user =
JsonReader.getUser();
```

---

Benefits

- Reusable
- Dynamic
- Environment independent

---

# 7. Environment Variables

Framework supports multiple environments.

Example

```properties
env=qa
```

---

QA

```properties
url=https://qa.site.com
```

---

UAT

```properties
url=https://uat.site.com
```

---

Production

```properties
url=https://prod.site.com
```

---

# Runtime Selection

```bash
mvn test -Denv=qa
```

---

Interview Question

Why use environment variables?

Avoid code changes across environments.

---

# 8. Singleton Pattern

Very Common Interview Topic

Goal:

Single object instance.

---

Example

```java
public class ConfigManager {

    private static ConfigManager
    instance;

    private ConfigManager() {

    }
}
```

---

Getter

```java
public static ConfigManager
getInstance() {

    if(instance == null) {

        instance =
        new ConfigManager();
    }

    return instance;
}
```

---

Benefits

- Memory efficient
- Centralized access

---

# Selenium Use Cases

- Config Manager
- Logger Manager
- Report Manager

---

# 9. Dependency Injection Concepts

Advanced Framework Topic

Instead of creating objects:

```java
new LoginPage();
```

Inject dependencies.

---

Example

```java
LoginPage page =
new LoginPage(driver);
```

---

Benefits

- Loose coupling
- Better testing
- Easy maintenance

---

# Interview Question

Why pass WebDriver in constructor?

Dependency Injection.

---

# 10. Static vs Instance Variables

Critical Framework Design Question

---

## Static Variable

```java
static WebDriver driver;
```

Shared.

---

## Instance Variable

```java
private WebDriver driver;
```

Object specific.

---

## Interview Comparison

Static

Pros:

- Easy access

Cons:

- Parallel execution issues

---

Instance

Pros:

- Better OOP
- Thread safe

Cons:

- Need object creation

---

# Recommended Design

```java
private WebDriver driver;
```

Inside Page Objects

---

# 11. REST Assured Framework Variables

Base URI

```java
public static final String
BASE_URL =
"https://api.site.com";
```

---

Request Specification

```java
RequestSpecification request;
```

---

Response Variable

```java
Response response;
```

---

Reusable Setup

```java
request =
given()
.baseUri(BASE_URL);
```

---

Interview Question

Why create reusable RequestSpecification?

Avoid duplication.

---

# API Framework Structure

```text
api
├── endpoints
├── requests
├── responses
├── utils
```

---

# 12. Playwright Framework Variables

Playwright Java

---

Browser

```java
Browser browser;
```

---

Page

```java
Page page;
```

---

BrowserContext

```java
BrowserContext context;
```

---

Typical Design

```java
public class BaseTest {

    protected Page page;
}
```

---

Interview Question

Difference between Browser and Page?

Browser

Actual browser process.

Page

Single tab.

---

# 13. Real Framework Structure

```text
src/test/java

├── tests
├── pages
├── utils
├── drivers
├── config
├── constants
├── listeners
├── reports
```

---

Variables Usage

drivers

WebDriver

config

Properties

constants

static final

reports

ExtentReports

---

# 14. Real Interview Scenarios

Scenario 1

Question:

Why static WebDriver fails in parallel execution?

Answer:

All threads share same variable.

---

Scenario 2

Question:

How do you manage drivers in Selenium framework?

Answer:

ThreadLocal DriverFactory.

---

Scenario 3

Question:

How do you switch environments?

Answer:

Environment variables and properties files.

---

Scenario 4

Question:

How do you store framework constants?

Answer:

Constants class using static final.

---

Scenario 5

Question:

How do you avoid hardcoded test data?

Answer:

Externalize into JSON/Excel/DB.

---

# Advanced Interview Questions

### Q1. Why use ThreadLocal<WebDriver>?

Parallel execution support.

---

### Q2. Why static final constants?

Shared immutable values.

---

### Q3. Why Singleton ConfigManager?

Single configuration instance.

---

### Q4. Why Dependency Injection?

Loose coupling.

---

### Q5. Why externalize test data?

Maintainability.

---

### Q6. Why use RequestSpecification?

Reusable API setup.

---

### Q7. Why environment variables?

Environment switching.

---

### Q8. Why not static Page Objects?

Shared state issues.

---

### Q9. How to prevent driver memory leaks?

driver.quit()

driver.remove()

---

### Q10. Best driver architecture?

ThreadLocal DriverFactory.

---

# MCQs

Q1. Best WebDriver variable for parallel execution?

A. static WebDriver
B. ThreadLocal<WebDriver>

Answer: B

---

Q2. Which keyword creates constant?

A. static
B. final

Answer: B

---

Q3. Singleton allows?

A. Multiple Objects
B. Single Object

Answer: B

---

Q4. RequestSpecification belongs to?

A. Selenium
B. REST Assured

Answer: B

---

Q5. Page object should usually store?

A. WebDriver
B. Browser Name

Answer: A

---

# Quick Revision Notes

THREADLOCAL

- Thread specific storage

CONFIGREADER

- Reads properties

CONSTANTS

- static final

SINGLETON

- One instance

DEPENDENCY INJECTION

- Pass dependency through constructor

REST ASSURED

- RequestSpecification
- Response

PLAYWRIGHT

- Browser
- Context
- Page

ENVIRONMENT VARIABLES

- QA
- UAT
- PROD

---

# One Minute Interview Cheat Sheet

WebDriver

→ ThreadLocal

Constants

→ static final

Config

→ Singleton

Test Data

→ JSON / Excel

Environment

→ Properties

Dependency Injection

→ Constructor Injection

REST Assured

→ RequestSpecification

Playwright

→ Browser → Context → Page

Most Asked Automation Interview Answer:

Use ThreadLocal<WebDriver> with DriverFactory to support parallel execution and avoid shared driver issues caused by static WebDriver.
