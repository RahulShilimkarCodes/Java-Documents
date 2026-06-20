# Java String Master Guide

# Part 7 - String Coding Problems (Basic Level)

---

# Table of Contents

1. Introduction to String Coding Problems
2. Reverse a String
3. Palindrome Check
4. Count Characters in String
5. Count Vowels and Consonants
6. Remove Duplicate Characters
7. Frequency Count of Characters
8. First Non-Repeating Character
9. Swap Strings Without Temp Variable
10. String Anagram Check (Basic)
11. Remove Spaces from String
12. Find Duplicate Words
13. Interview Tricky Cases
14. Selenium + API Usage Patterns
15. Short Notes
16. Revision Sheet

---

# 1. Introduction to String Coding Problems

String coding questions are the MOST asked topic in:

* Java Interviews
* Selenium Automation Interviews
* API Testing Interviews
* Product-based companies

They test:

* Logic building
* String manipulation
* Time complexity awareness

---

# 2. Reverse a String

## Using loop

```java id="r1"
String s = "Java";
String rev = "";

for(int i = s.length()-1; i>=0; i--){
    rev += s.charAt(i);
}

System.out.println(rev);
```

Output:

```text id="r2"
avaJ
```

---

## Using StringBuilder

```java id="r3"
String s = "Java";

StringBuilder sb = new StringBuilder(s);
System.out.println(sb.reverse());
```

---

# 3. Palindrome Check

A string is palindrome if:

```text id="r4"
reverse == original
```

Example:

```java id="r5"
String s = "madam";
String rev = "";

for(int i = s.length()-1; i>=0; i--){
    rev += s.charAt(i);
}

if(s.equals(rev)){
    System.out.println("Palindrome");
}
```

Output:

```text id="r6"
Palindrome
```

---

# 4. Count Characters in String

```java id="r7"
String s = "Java";

System.out.println(s.length());
```

Output:

```text id="r8"
4
```

---

# 5. Count Vowels and Consonants

```java id="r9"
String s = "Automation";
int vowels = 0, consonants = 0;

for(char c : s.toCharArray()){
    if("aeiouAEIOU".indexOf(c) != -1){
        vowels++;
    } else {
        consonants++;
    }
}

System.out.println("Vowels: " + vowels);
System.out.println("Consonants: " + consonants);
```

---

# 6. Remove Duplicate Characters

```java id="r10"
String s = "aabbcc";
String result = "";

for(char c : s.toCharArray()){
    if(result.indexOf(c) == -1){
        result += c;
    }
}

System.out.println(result);
```

Output:

```text id="r11"
abc
```

---

# 7. Frequency Count of Characters

```java id="r12"
String s = "java";
int count = 0;

char target = 'a';

for(char c : s.toCharArray()){
    if(c == target){
        count++;
    }
}

System.out.println(count);
```

Output:

```text id="r13"
2
```

---

# 8. First Non-Repeating Character

```java id="r14"
String s = "aabbcde";

for(char c : s.toCharArray()){
    if(s.indexOf(c) == s.lastIndexOf(c)){
        System.out.println(c);
        break;
    }
}
```

Output:

```text id="r15"
c
```

---

# 9. Swap Strings Without Temp Variable

```java id="r16"
String a = "Java";
String b = "Selenium";

a = a + b;
b = a.substring(0, a.length() - b.length());
a = a.substring(b.length());

System.out.println(a);
System.out.println(b);
```

Output:

```text id="r17"
Selenium
Java
```

---

# 10. Basic Anagram Check

```java id="r18"
String s1 = "listen";
String s2 = "silent";

char[] a = s1.toCharArray();
char[] b = s2.toCharArray();

Arrays.sort(a);
Arrays.sort(b);

System.out.println(Arrays.equals(a, b));
```

Output:

```text id="r19"
true
```

---

# 11. Remove Spaces from String

```java id="r20"
String s = "Java Selenium";

System.out.println(s.replace(" ", ""));
```

Output:

```text id="r21"
JavaSelenium
```

---

# 12. Find Duplicate Words

```java id="r22"
String s = "Java Selenium Java API Selenium";

String[] words = s.split(" ");

Set<String> set = new HashSet<>();
Set<String> duplicates = new HashSet<>();

for(String w : words){
    if(!set.add(w)){
        duplicates.add(w);
    }
}

System.out.println(duplicates);
```

---

# 13. Interview Tricky Case

```java id="r23"
String s = "Java";

s.concat(" Selenium");

System.out.println(s);
```

Output:

```text id="r24"
Java
```

Reason:

```text id="r25"
String is immutable
```

---

# 14. Selenium Usage Example

```java id="r26"
String actualTitle = driver.getTitle();
String expectedTitle = "Dashboard";

Assert.assertEquals(actualTitle, expectedTitle);
```

---

# 15. API Usage Example

```java id="r27"
String status = response.jsonPath().getString("status");

if(status.equalsIgnoreCase("success")){
    System.out.println("Test Passed");
}
```

---

# 16. Pattern: Frequent Interview Logic

Most asked patterns:

```text id="r28"
Reverse String
Palindrome
Frequency Count
First Non-Repeating
Anagram
Remove Duplicates
```

---

# 17. Short Notes

✔ Use charAt() for reverse logic
✔ Use indexOf/lastIndexOf for uniqueness
✔ Use HashSet for duplicates
✔ Use StringBuilder for performance
✔ equals() for comparison
✔ split() for word problems

---

# 18. Revision Sheet

```text id="r29"
Reverse → loop / StringBuilder

Palindrome → reverse compare

Frequency → loop count

Duplicates → Set

Anagram → sort + compare

Non-repeating → indexOf == lastIndexOf
```

---

# Interview Quick Summary

* Strings are immutable
* Avoid + in loops
* Use StringBuilder for efficiency
* HashSet helps remove duplicates
* Sorting helps in anagram problems
* indexOf logic is widely used

---

# Part 7 Completed

Next Part:

Part 8 - Intermediate String Coding Problems

Topics:

* Sliding window string problems
* Substring problems
* Pattern matching
* Longest substring without repeating characters
* String rotation problems
* Advanced interview patterns
* Selenium real-world automation logic
