# Java String Master Guide

# Part 4 - String Comparison Deep Dive

---

# Table of Contents

1. Why String Comparison is Important
2. == Operator
3. equals()
4. equalsIgnoreCase()
5. compareTo()
6. compareToIgnoreCase()
7. SCP Impact on Comparison
8. Heap vs SCP Comparison
9. Memory Diagrams
10. Common Mistakes
11. Selenium Project Examples
12. REST Assured Examples
13. Tricky Interview Programs
14. Best Practices
15. Interview Questions
16. Revision Sheet

---

# 1. Why String Comparison is Important

One of the most frequently asked Java interview topics.

Used in:

* Selenium Assertions
* API Response Validation
* Database Verification
* Login Verification
* Environment Checks
* Configuration Validation

A large number of bugs occur because developers misuse:

```java id="p1"
==
```

instead of

```java id="p2"
equals()
```

---

# 2. == Operator

The == operator compares:

```text id="p3"
Memory References
```

NOT content.

Example:

```java id="p4"
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

Output:

```text id="p5"
true
```

Why?

Both point to same SCP object.

---

Memory:

```text id="p6"
SCP

+------+
| Java |
+------+

s1 -----+
         |
s2 -----+
```

---

# 3. equals()

equals() compares:

```text id="p7"
Actual Content
```

Example:

```java id="p8"
String s1 = "Java";
String s2 = "Java";

System.out.println(
s1.equals(s2));
```

Output:

```text id="p9"
true
```

---

Example:

```java id="p10"
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(
s1.equals(s2));
```

Output:

```text id="p11"
true
```

Content same.

---

# 4. Most Important Interview Example

```java id="p12"
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
```

Output:

```text id="p13"
false
true
```

Explanation:

```text id="p14"
==        → Reference

equals() → Content
```

---

# 5. Heap Comparison

Example:

```java id="p15"
String s1 = new String("Java");
String s2 = new String("Java");
```

Memory:

```text id="p16"
Heap

+------+
| Java |
+------+

+------+
| Java |
+------+
```

Different objects.

Hence:

```java id="p17"
s1 == s2
```

returns:

```text id="p18"
false
```

---

# 6. SCP Comparison

Example:

```java id="p19"
String s1 = "Java";
String s2 = "Java";
```

Memory:

```text id="p20"
SCP

+------+
| Java |
+------+
```

Both references point to same object.

Result:

```java id="p21"
s1 == s2
```

Output:

```text id="p22"
true
```

---

# 7. Mixed Comparison

Example:

```java id="p23"
String s1 = "Java";
String s2 = new String("Java");

System.out.println(s1 == s2);
```

Output:

```text id="p24"
false
```

Reason:

```text id="p25"
s1 → SCP

s2 → Heap
```

Different references.

---

# 8. equalsIgnoreCase()

Ignores character case.

Example:

```java id="p26"
String s1 = "JAVA";
String s2 = "java";

System.out.println(
s1.equalsIgnoreCase(s2));
```

Output:

```text id="p27"
true
```

---

Example:

```java id="p28"
System.out.println(
s1.equals(s2));
```

Output:

```text id="p29"
false
```

---

# 9. compareTo()

Lexicographical comparison.

Syntax:

```java id="p30"
str1.compareTo(str2);
```

Returns:

```text id="p31"
0       -> Equal

Positive -> Greater

Negative -> Smaller
```

---

Example:

```java id="p32"
System.out.println(
"Java".compareTo("Java"));
```

Output:

```text id="p33"
0
```

---

Example:

```java id="p34"
System.out.println(
"Java".compareTo("Python"));
```

Output:

```text id="p35"
Negative Number
```

---

# 10. compareToIgnoreCase()

Same as compareTo but ignores case.

Example:

```java id="p36"
System.out.println(
"JAVA".compareToIgnoreCase("java"));
```

Output:

```text id="p37"
0
```

---

# 11. Intern Method Comparison

Example:

```java id="p38"
String s1 = new String("Java");

String s2 = s1.intern();

String s3 = "Java";
```

Comparison:

```java id="p39"
System.out.println(s2 == s3);
```

Output:

```text id="p40"
true
```

Both point to SCP.

---

Memory:

```text id="p41"
SCP

Java
 ^
 |
s2,s3

Heap

Java
 ^
 |
s1
```

---

# 12. Null Safe Comparison

Dangerous:

```java id="p42"
String status = null;

status.equals("PASS");
```

Throws:

```java id="p43"
NullPointerException
```

---

Safe:

```java id="p44"
"PASS".equals(status);
```

Output:

```text id="p45"
false
```

No exception.

---

# 13. Selenium Project Example

Wrong:

```java id="p46"
if(driver.getTitle() == "Dashboard")
{
}
```

Never recommended.

---

Correct:

```java id="p47"
if(driver.getTitle()
         .equals("Dashboard"))
{
}
```

---

Best:

```java id="p48"
Assert.assertEquals(
driver.getTitle(),
"Dashboard");
```

---

# 14. URL Validation Example

```java id="p49"
Assert.assertTrue(
driver.getCurrentUrl()
      .contains("dashboard")
);
```

Uses String comparison internally.

---

# 15. API Testing Example

Response:

```json id="p50"
{
  "status":"SUCCESS"
}
```

Validation:

```java id="p51"
String status =
response.jsonPath()
        .getString("status");

Assert.assertTrue(
status.equalsIgnoreCase("success")
);
```

---

# 16. Database Validation Example

```java id="p52"
String dbValue = "Admin";

String uiValue = "Admin";

Assert.assertEquals(
dbValue,
uiValue
);
```

---

# 17. Tricky Interview Program #1

```java id="p53"
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

Output:

```text id="p54"
true
```

---

# 18. Tricky Interview Program #2

```java id="p55"
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
```

Output:

```text id="p56"
false
```

---

# 19. Tricky Interview Program #3

```java id="p57"
String s1 = "Java";

String s2 =
new String("Java");

System.out.println(
s1.equals(s2));
```

Output:

```text id="p58"
true
```

---

# 20. Tricky Interview Program #4

```java id="p59"
String s1 = "Java";

String s2 = "Ja";

String s3 = s2 + "va";

System.out.println(
s1 == s3);
```

Output:

```text id="p60"
false
```

Because:

```text id="p61"
s3 created at runtime
```

Heap object created.

---

# 21. Tricky Interview Program #5

```java id="p62"
String s1 = "Java";

String s2 = "Ja" + "va";

System.out.println(
s1 == s2);
```

Output:

```text id="p63"
true
```

Compile-time optimization.

---

# 22. Tricky Interview Program #6

```java id="p64"
final String s = "Ja";

String result = s + "va";

String original = "Java";

System.out.println(
result == original);
```

Output:

```text id="p65"
true
```

Compiler optimization.

---

# 23. Tricky Interview Program #7

```java id="p66"
String s1 = null;

System.out.println(
"Java".equals(s1));
```

Output:

```text id="p67"
false
```

Safe comparison.

---

# 24. Best Practices

Always use:

```java id="p68"
equals()
```

for content comparison.

---

Use:

```java id="p69"
equalsIgnoreCase()
```

for user input.

---

Avoid:

```java id="p70"
==
```

unless checking references.

---

Use:

```java id="p71"
constant.equals(variable)
```

for null safety.

---

# 25. Common Interview Questions

## Q1 What does == compare?

```text id="p72"
Memory Reference
```

---

## Q2 What does equals compare?

```text id="p73"
Content
```

---

## Q3 Which comparison is used in Selenium?

```java id="p74"
equals()
```

---

## Q4 Why is == dangerous?

Because same content may exist in different objects.

---

## Q5 Difference between equals and equalsIgnoreCase?

Case sensitivity.

---

## Q6 What does compareTo return?

```text id="p75"
0

Positive

Negative
```

---

## Q7 Can equals throw NPE?

Yes.

Example:

```java id="p76"
null.equals("Java");
```

---

## Q8 How to avoid NPE?

```java id="p77"
"Java".equals(value);
```

---

## Q9 Why does String Pool affect ==?

Because same SCP object may be reused.

---

## Q10 Which comparison method is most used in frameworks?

```java id="p78"
equals()

equalsIgnoreCase()

contains()
```

---

# Short Notes

✔ == compares references

✔ equals compares content

✔ equalsIgnoreCase ignores case

✔ compareTo supports sorting

✔ compareToIgnoreCase ignores case

✔ intern() returns SCP reference

✔ SCP can make == return true

✔ Heap objects usually make == return false

✔ Use constant.equals(variable)

✔ Avoid == for content comparison

---

# Revision Sheet

```text id="p79"
==
↓
Reference Comparison

equals()
↓
Content Comparison

equalsIgnoreCase()
↓
Case Insensitive

compareTo()
↓
Sorting Comparison

intern()
↓
SCP Reference
```

---

# Interview Rapid Revision

Most Asked Question:

```java id="p80"
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
```

Output:

```text id="p81"
false
true
```

Reason:

```text id="p82"
==       -> Reference

equals() -> Content
```

---

# Part 4 Completed

Next Part:

Part 5 - StringBuilder & StringBuffer Deep Dive

Topics:

* Why StringBuilder Exists
* Mutable vs Immutable
* StringBuilder Internals
* StringBuffer Internals
* Thread Safety
* append()
* insert()
* delete()
* reverse()
* replace()
* Capacity vs Length
* Performance Benchmarks
* Real Project Examples
* 30+ Interview Questions
