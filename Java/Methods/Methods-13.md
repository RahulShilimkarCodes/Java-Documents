# Java Methods Master Guide

# Part 13 - Methods in Selenium, TestNG & API Frameworks

---

# Table of Contents

1. Introduction
2. Why Methods Are Critical in Automation Frameworks
3. Framework Architecture Overview
4. Methods in Selenium Framework
5. Page Object Methods
6. Utility Methods
7. Wait Methods
8. Screenshot Methods
9. Browser Management Methods
10. Driver Factory Methods
11. Method Chaining in Selenium
12. Fluent Page Object Model
13. TestNG Configuration Methods
14. DataProvider Methods
15. Retry Methods
16. Listener Methods
17. Methods in API Frameworks
18. Request Builder Methods
19. Authentication Methods
20. Response Validation Methods
21. JSON Utility Methods
22. Framework Design Best Practices
23. Real Project Scenarios
24. Top Interview Questions
25. Final Cheat Sheet

---

# 1. Introduction

In real projects, Java methods are the foundation of:

```text
Selenium Frameworks

Playwright Frameworks

REST Assured Frameworks

TestNG Frameworks

Hybrid Automation Frameworks
```

---

Interview Question:

```text
Where are methods used in automation frameworks?
```

Answer:

```text
Methods are used to implement reusable business actions,
framework utilities, reporting modules,
API services, validations and test workflows.
```

---

# 2. Why Methods Are Critical in Automation Frameworks

Without Methods:

```java
driver.findElement(locator).click();

driver.findElement(locator).sendKeys("Rahul");

driver.findElement(locator).click();
```

Repeated hundreds of times.

---

With Methods:

```java
loginPage.login();
```

---

Benefits:

```text
Reusability

Maintainability

Readability

Scalability

Reduced Duplication
```

---

# 3. Framework Architecture Overview

Typical Selenium Framework

```text
Tests
 │
 ▼
Page Objects
 │
 ▼
Business Methods
 │
 ▼
Utility Methods
 │
 ▼
WebDriver
```

---

Methods exist at every layer.

---

# 4. Methods in Selenium Framework

Example:

```java
public void clickLoginButton(){

    loginButton.click();
}
```

---

Usage:

```java
loginPage.clickLoginButton();
```

---

Interview Point:

```text
Page methods should represent business actions,
not WebDriver commands.
```

---

Bad:

```java
clickButton();
```

Good:

```java
clickLoginButton();
```

---

# 5. Page Object Methods

Page Object Model (POM)

Example:

```java
public class LoginPage {

}
```

---

Methods:

```java
enterUsername()

enterPassword()

clickLogin()

login()
```

---

Implementation:

```java
public void login(String user,String pass){

    username.sendKeys(user);

    password.sendKeys(pass);

    loginBtn.click();
}
```

---

Test:

```java
loginPage.login("admin","admin123");
```

---

# 6. Utility Methods

Common reusable methods.

Example:

```java
public static String getCurrentDate(){

}
```

---

```java
public static void captureScreenshot(){

}
```

---

Utility Class:

```java
DateUtil

ExcelUtil

ConfigUtil

ScreenshotUtil

JsonUtil
```

---

Interview Point:

```text
Utility methods are generally static.
```

---

# 7. Wait Methods

Frameworks often centralize waits.

Bad:

```java
Thread.sleep(5000);
```

---

Good:

```java
waitForElement(locator);
```

---

Example:

```java
public void waitForElement(By locator){

    wait.until(
      ExpectedConditions
      .visibilityOfElementLocated(locator));
}
```

---

Advantages:

```text
Reusable

Stable

Maintainable
```

---

# 8. Screenshot Methods

Common Framework Utility.

Example:

```java
public static void captureScreenshot(
String testName){

}
```

---

Usage:

```java
ScreenshotUtil.captureScreenshot(
"LoginTest");
```

---

Interview Question:

```text
Why make screenshot method static?
```

Answer:

```text
No object state required.
```

---

# 9. Browser Management Methods

Example:

```java
launchBrowser()

maximizeWindow()

closeBrowser()

quitDriver()
```

---

Implementation:

```java
public void launchBrowser(){

    driver =
    new ChromeDriver();
}
```

---

Framework Usage:

```java
driverFactory.launchBrowser();
```

---

# 10. Driver Factory Methods

Most Modern Frameworks

Example:

```java
public static WebDriver getDriver(){

}
```

---

ThreadLocal Example:

```java
public static WebDriver getDriver(){

    return driver.get();
}
```

---

Frequently Asked In Interviews.

---

# 11. Method Chaining in Selenium

Example:

```java
loginPage
.enterUsername("Rahul")
.enterPassword("Pass")
.clickLogin();
```

---

Method:

```java
public LoginPage enterUsername(
String user){

    username.sendKeys(user);

    return this;
}
```

---

Benefits:

```text
Readable

Professional

Fluent Design
```

---

# 12. Fluent Page Object Model

Advanced Framework Design.

Example:

```java
HomePage home =
loginPage
.enterUsername("admin")
.enterPassword("admin")
.clickLogin();
```

---

Industry Standard Pattern.

---

# 13. TestNG Configuration Methods

Important Interview Topic.

---

@BeforeSuite

```java
@BeforeSuite
public void beforeSuite(){

}
```

Runs once.

---

@BeforeTest

```java
@BeforeTest
public void beforeTest(){

}
```

Runs before test tag.

---

@BeforeClass

```java
@BeforeClass
public void setup(){

}
```

Runs once per class.

---

@BeforeMethod

```java
@BeforeMethod
public void launch(){

}
```

Runs before every test.

---

Execution Flow

```text
BeforeSuite

BeforeTest

BeforeClass

BeforeMethod

@Test

AfterMethod

AfterClass

AfterTest

AfterSuite
```

---

# 14. DataProvider Methods

Most Asked TestNG Topic.

Example:

```java
@DataProvider
public Object[][] getData(){

    return new Object[][]{

      {"admin","admin123"},
      {"user","user123"}

    };
}
```

---

Usage:

```java
@Test(dataProvider="getData")
```

---

Benefits:

```text
Data Driven Testing

Reusable Test Data
```

---

# 15. Retry Methods

Common Framework Feature.

Example:

```java
public boolean retry(
ITestResult result){

}
```

---

Purpose:

```text
Retry Failed Tests
```

---

Interview Question:

```text
How do you rerun failed tests automatically?
```

Answer:

```text
IRetryAnalyzer
```

---

# 16. Listener Methods

Frequently Asked.

Example:

```java
onTestStart()

onTestSuccess()

onTestFailure()

onFinish()
```

---

Implementation:

```java
public void onTestFailure(
ITestResult result){

}
```

---

Common Use:

```text
Screenshot Capture

Logging

Reporting
```

---

# 17. Methods in API Frameworks

API Framework Layers

```text
Tests

↓

Services

↓

Utilities

↓

REST Assured
```

---

Service Methods:

```java
createUser()

updateUser()

deleteUser()

getUser()
```

---

# 18. Request Builder Methods

Example:

```java
public RequestSpecification
getRequest(){

}
```

---

Usage:

```java
given()
.spec(getRequest())
.when()
.get();
```

---

Reusable Framework Design.

---

# 19. Authentication Methods

Examples:

```java
generateToken()

getBearerToken()

refreshToken()
```

---

Implementation:

```java
public String generateToken(){

}
```

---

Frequently Used In REST Assured Frameworks.

---

# 20. Response Validation Methods

Example:

```java
validateStatusCode()

validateSchema()

validateResponseTime()
```

---

Implementation:

```java
public void validateStatusCode(
Response response,
int expected){

}
```

---

Reusable validation layer.

---

# 21. JSON Utility Methods

Examples:

```java
readJson()

writeJson()

parseResponse()

getJsonValue()
```

---

Utility Example:

```java
JsonUtil.getValue(
response,
"name");
```

---

# 22. Framework Design Best Practices

Good Method:

```java
login()
```

---

Bad Method:

```java
loginSearchCheckoutLogout();
```

---

Rules:

```text
Single Responsibility

Reusable

Readable

Small

Independent
```

---

# 23. Real Project Scenarios

Selenium:

```java
login()

searchProduct()

addToCart()

checkout()
```

---

API:

```java
createUser()

updateUser()

deleteUser()
```

---

Utilities:

```java
captureScreenshot()

generateReport()

readExcel()
```

---

# 24. Top Interview Questions

### Q1 Why Use Methods In Frameworks?

```text
Reusability
```

---

### Q2 Why Are Utility Methods Static?

```text
No Object State Required
```

---

### Q3 What Is Method Chaining?

```text
Methods Returning Objects
```

---

### Q4 What Is Fluent POM?

```text
Method Chaining Based Page Objects
```

---

### Q5 Most Common Framework Methods?

```text
login()

logout()

captureScreenshot()

waitForElement()

generateToken()
```

---

# 25. Final Cheat Sheet

```text
Framework Methods

Page Methods

login()

searchProduct()

checkout()

Utility Methods

captureScreenshot()

readExcel()

generateReport()

TestNG Methods

@BeforeMethod

@DataProvider

Listeners

Retry Analyzer

API Methods

createUser()

updateUser()

deleteUser()

Design Rule

Reusable

Small

Single Responsibility
```

---

# End of Part 13

## Next Part

Part 14 → JVM Internals, Stack Frames & Memory Management
