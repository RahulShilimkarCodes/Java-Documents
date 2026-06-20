# Java String Master Guide

# Part 3 - String Methods Deep Dive

---

# Table of Contents

1. Introduction to String Methods
2. length()
3. charAt()
4. substring()
5. indexOf()
6. lastIndexOf()
7. contains()
8. startsWith()
9. endsWith()
10. equals()
11. equalsIgnoreCase()
12. compareTo()
13. replace()
14. replaceAll()
15. replaceFirst()
16. toUpperCase()
17. toLowerCase()
18. trim()
19. strip()
20. split()
21. join()
22. repeat()
23. isEmpty()
24. isBlank()
25. matches()
26. Real Project Examples
27. Interview Questions
28. Short Notes
29. Revision Sheet

---

# 1. Introduction to String Methods

The String class provides many built-in methods to manipulate text data.

Common usage:

* Selenium Validations
* API Response Parsing
* Database Validation
* Report Generation
* Log Processing

---

# 2. length()

Returns number of characters.

Syntax:

```java
str.length();
```

Example:

```java
String name = "Java";

System.out.println(name.length());
```

Output:

```text
4
```

---

## Interview Question

```java
String s = "";

System.out.println(s.length());
```

Output:

```text
0
```

---

# 3. charAt()

Returns character at specified index.

Syntax:

```java
str.charAt(index);
```

Example:

```java
String s = "Java";

System.out.println(s.charAt(2));
```

Output:

```text
v
```

Indexes:

```text
J a v a
0 1 2 3
```

---

## Exception

```java
s.charAt(10);
```

Throws:

```java
StringIndexOutOfBoundsException
```

---

# 4. substring()

Extracts portion of String.

Syntax:

```java
substring(beginIndex)
```

```java
substring(beginIndex,endIndex)
```

Example:

```java
String s = "Selenium";

System.out.println(s.substring(4));
```

Output:

```text
nium
```

---

Example:

```java
System.out.println(s.substring(0,4));
```

Output:

```text
Sele
```

End index excluded.

---

# 5. indexOf()

Returns first occurrence.

Example:

```java
String s = "Java Selenium";

System.out.println(s.indexOf('a'));
```

Output:

```text
1
```

---

Example:

```java
System.out.println(s.indexOf("Selenium"));
```

Output:

```text
5
```

---

Not found:

```java
System.out.println(s.indexOf("Python"));
```

Output:

```text
-1
```

---

# 6. lastIndexOf()

Returns last occurrence.

Example:

```java
String s = "Java Java";

System.out.println(s.lastIndexOf('a'));
```

Output:

```text
8
```

---

# 7. contains()

Checks presence of text.

Example:

```java
String s = "Automation Testing";

System.out.println(
s.contains("Testing"));
```

Output:

```text
true
```

---

Project Example:

```java
if(response.contains("success"))
{
   System.out.println("Pass");
}
```

---

# 8. startsWith()

Checks starting text.

Example:

```java
String url =
"https://google.com";

System.out.println(
url.startsWith("https"));
```

Output:

```text
true
```

---

Automation Usage

```java
Assert.assertTrue(
currentUrl.startsWith("https")
);
```

---

# 9. endsWith()

Checks ending text.

Example:

```java
String file = "report.pdf";

System.out.println(
file.endsWith(".pdf"));
```

Output:

```text
true
```

---

# 10. equals()

Compares content.

Example:

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(
s1.equals(s2));
```

Output:

```text
true
```

---

Most Important Interview Rule

```java
equals()
```

compares:

```text
Content
```

---

# 11. equalsIgnoreCase()

Ignores case.

Example:

```java
String s1 = "JAVA";
String s2 = "java";

System.out.println(
s1.equalsIgnoreCase(s2));
```

Output:

```text
true
```

---

API Example

```java
if(status.equalsIgnoreCase("success"))
{
   // pass
}
```

---

# 12. compareTo()

Lexicographical comparison.

Example:

```java
System.out.println(
"Apple".compareTo("Banana"));
```

Output:

```text
Negative Value
```

---

Example:

```java
System.out.println(
"Java".compareTo("Java"));
```

Output:

```text
0
```

---

Rules:

```text
0 = Equal

Positive = Greater

Negative = Smaller
```

---

# 13. replace()

Replaces text.

Example:

```java
String s =
"Java Selenium";

System.out.println(
s.replace("Java","Playwright"));
```

Output:

```text
Playwright Selenium
```

---

# 14. replaceAll()

Uses Regular Expression.

Example:

```java
String s = "abc123";

System.out.println(
s.replaceAll("[0-9]",""));
```

Output:

```text
abc
```

---

# 15. replaceFirst()

Replaces first match only.

Example:

```java
String s =
"Java Java Java";

System.out.println(
s.replaceFirst("Java","PW"));
```

Output:

```text
PW Java Java
```

---

# 16. toUpperCase()

Converts to uppercase.

Example:

```java
String s = "java";

System.out.println(
s.toUpperCase());
```

Output:

```text
JAVA
```

---

# 17. toLowerCase()

Converts to lowercase.

Example:

```java
String s = "JAVA";

System.out.println(
s.toLowerCase());
```

Output:

```text
java
```

---

# 18. trim()

Removes leading and trailing spaces.

Example:

```java
String s = " Java ";

System.out.println(
s.trim());
```

Output:

```text
Java
```

---

# 19. strip() (Java 11)

Better Unicode-aware trimming.

Example:

```java
String s = " Java ";

System.out.println(
s.strip());
```

---

Interview Point

```text
strip() preferred in Java 11+
```

---

# 20. split()

Splits String into array.

Example:

```java
String data =
"Java,Selenium,API";

String[] arr =
data.split(",");
```

Output:

```text
Java
Selenium
API
```

---

Framework Usage

```java
String envs =
"QA,UAT,PROD";
```

Convert into list.

---

# 21. join()

Joins Strings.

Example:

```java
String result =
String.join("-",
"Java",
"Selenium",
"API");
```

Output:

```text
Java-Selenium-API
```

---

# 22. repeat()

Java 11 feature.

Example:

```java
System.out.println(
"*".repeat(5));
```

Output:

```text
*****
```

---

Framework Example

```java
System.out.println(
"-".repeat(50));
```

Used in reports.

---

# 23. isEmpty()

Checks length == 0

Example:

```java
String s = "";

System.out.println(
s.isEmpty());
```

Output:

```text
true
```

---

Example:

```java
String s = " ";

System.out.println(
s.isEmpty());
```

Output:

```text
false
```

---

# 24. isBlank() (Java 11)

Checks whitespace too.

Example:

```java
String s = " ";

System.out.println(
s.isBlank());
```

Output:

```text
true
```

---

Difference:

```text
isEmpty() -> Length 0

isBlank() -> Empty or Spaces
```

---

# 25. matches()

Regex validation.

Example:

```java
String email =
"abc@gmail.com";

System.out.println(
email.matches(
".+@.+\\..+"));
```

Output:

```text
true
```

---

Framework Usage

Validate:

* Email
* Phone
* PAN
* Aadhaar
* URLs

---

# 26. Selenium Project Examples

## Verify Title

```java
Assert.assertEquals(
driver.getTitle(),
"Dashboard"
);
```

---

## Verify URL

```java
Assert.assertTrue(
driver.getCurrentUrl()
      .contains("dashboard")
);
```

---

## Validate User

```java
String actual =
driver.findElement(locator)
      .getText();

Assert.assertEquals(
actual,
"Admin"
);
```

---

# 27. REST Assured Examples

Validate Response

```java
String status =
response.jsonPath()
        .getString("status");

Assert.assertEquals(
status,
"success"
);
```

---

Case-insensitive validation

```java
Assert.assertTrue(
status.equalsIgnoreCase("SUCCESS")
);
```

---

# 28. Common Interview Questions

## Q1 Difference between length() and length?

```text
String -> length()

Array -> length
```

---

## Q2 Difference between trim() and strip()?

```text
trim() -> Older

strip() -> Unicode Aware
```

---

## Q3 Difference between isEmpty() and isBlank()?

```text
isEmpty()
```

Checks:

```text
length == 0
```

---

```text
isBlank()
```

Checks:

```text
Empty + Whitespaces
```

---

## Q4 What if substring index is invalid?

Throws:

```java
StringIndexOutOfBoundsException
```

---

## Q5 Difference between replace and replaceAll?

```text
replace()
```

Normal replacement.

```text
replaceAll()
```

Regex replacement.

---

## Q6 What does contains() return?

```text
boolean
```

---

## Q7 compareTo() return values?

```text
0
Positive
Negative
```

---

## Q8 Which method checks ignoring case?

```java
equalsIgnoreCase()
```

---

## Q9 Which method is heavily used in Selenium?

```java
contains()
equals()
startsWith()
endsWith()
```

---

## Q10 Which methods were added in Java 11?

```java
isBlank()

repeat()

strip()
```

---

# Short Notes

✔ length()

✔ charAt()

✔ substring()

✔ indexOf()

✔ contains()

✔ startsWith()

✔ endsWith()

✔ equals()

✔ equalsIgnoreCase()

✔ compareTo()

✔ replace()

✔ split()

✔ join()

✔ repeat()

✔ trim()

✔ strip()

✔ isEmpty()

✔ isBlank()

✔ matches()

---

# Revision Sheet

```text
length()
↓
Count Characters

charAt()
↓
Get Character

substring()
↓
Extract Text

contains()
↓
Find Text

equals()
↓
Compare Content

compareTo()
↓
Sort Comparison

split()
↓
Convert To Array

join()
↓
Merge Strings

isEmpty()
↓
Length 0

isBlank()
↓
Whitespace Check
```

---

# Interview Rapid Revision

Most Frequently Asked Methods:

```text
equals()

equalsIgnoreCase()

contains()

substring()

split()

replace()

compareTo()

trim()

isEmpty()

isBlank()
```

---

# Part 3 Completed

Next Part:

Part 4 - String Comparison Deep Dive

Topics:

* == Operator
* equals()
* equalsIgnoreCase()
* compareTo()
* compareToIgnoreCase()
* SCP Impact on Comparisons
* Heap vs SCP Comparisons
* Interview Tricky Programs
* Memory Diagrams
* Real Selenium Scenarios
* 30+ Interview Questions
