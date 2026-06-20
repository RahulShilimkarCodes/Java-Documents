# Java String Master Guide

# Part 8 - Intermediate String Coding Problems

---

# Table of Contents

1. Introduction to Intermediate String Problems
2. Longest Substring Without Repeating Characters
3. Substring Search (Brute Force)
4. String Rotation Check
5. Count Occurrence of Substring
6. Remove All Occurrences of a Character
7. Longest Palindromic Substring (Basic Approach)
8. String Compression (Run Length Encoding)
9. Check if One String is Rotation of Another
10. Pattern Matching Basics
11. Anagram Grouping (Intermediate Level)
12. Sliding Window Concept for Strings
13. Interview Tricky Cases
14. Selenium & API Real Scenarios
15. Short Notes
16. Revision Sheet

---

# 1. Introduction to Intermediate Problems

These questions test:

* Sliding window logic
* Nested loops optimization
* Hashing techniques
* String manipulation efficiency

Used heavily in:

* Product companies
* Automation frameworks
* API validation logic

---

# 2. Longest Substring Without Repeating Characters

## Brute Force Approach

```java id="a1"
String s = "abcabcbb";
int max = 0;

for(int i = 0; i < s.length(); i++){
    String temp = "";
    
    for(int j = i; j < s.length(); j++){
        if(temp.indexOf(s.charAt(j)) != -1){
            break;
        }
        temp += s.charAt(j);
        max = Math.max(max, temp.length());
    }
}

System.out.println(max);
```

Output:

```text id="a2"
3
```

---

# 3. Substring Search (Basic)

```java id="a3"
String s = "Java Selenium";
String target = "Selenium";

System.out.println(s.contains(target));
```

Output:

```text id="a4"
true
```

---

# 4. String Rotation Check

Check if:

```text id="a5"
s2 is rotation of s1
```

Example:

```java id="a6"
String s1 = "abcd";
String s2 = "cdab";

String temp = s1 + s1;

System.out.println(temp.contains(s2));
```

Output:

```text id="a7"
true
```

---

# 5. Count Occurrence of Substring

```java id="a8"
String s = "abababa";
String sub = "aba";

int count = 0;

for(int i = 0; i <= s.length() - sub.length(); i++){
    if(s.substring(i, i + sub.length()).equals(sub)){
        count++;
    }
}

System.out.println(count);
```

Output:

```text id="a9"
2
```

---

# 6. Remove All Occurrences of Character

```java id="a10"
String s = "automation";
char remove = 'a';

String result = "";

for(char c : s.toCharArray()){
    if(c != remove){
        result += c;
    }
}

System.out.println(result);
```

Output:

```text id="a11"
utomtion
```

---

# 7. Longest Palindromic Substring (Basic)

```java id="a12"
String s = "babad";
String longest = "";

for(int i = 0; i < s.length(); i++){
    for(int j = i; j < s.length(); j++){
        String sub = s.substring(i, j+1);
        String rev = new StringBuilder(sub).reverse().toString();
        
        if(sub.equals(rev) && sub.length() > longest.length()){
            longest = sub;
        }
    }
}

System.out.println(longest);
```

Output:

```text id="a13"
bab
```

---

# 8. String Compression (Run Length Encoding)

```java id="a14"
String s = "aaabbc";
String result = "";

int count = 1;

for(int i = 0; i < s.length() - 1; i++){
    if(s.charAt(i) == s.charAt(i+1)){
        count++;
    } else {
        result += s.charAt(i) + "" + count;
        count = 1;
    }
}

result += s.charAt(s.length()-1) + "" + count;

System.out.println(result);
```

Output:

```text id="a15"
a3b2c1
```

---

# 9. Check Rotation Using StringBuilder

```java id="a16"
String s1 = "waterbottle";
String s2 = "erbottlewat";

System.out.println(
(s1 + s1).contains(s2)
);
```

---

# 10. Pattern Matching Basics

```java id="a17"
String text = "abababc";
String pattern = "ab";

int count = 0;

for(int i = 0; i <= text.length() - pattern.length(); i++){
    if(text.substring(i, i + pattern.length()).equals(pattern)){
        count++;
    }
}

System.out.println(count);
```

Output:

```text id="a18"
3
```

---

# 11. Group Anagrams (Basic Idea)

```java id="a19"
String[] arr = {"eat","tea","tan","ate"};

for(String s : arr){
    char[] c = s.toCharArray();
    Arrays.sort(c);
    System.out.println(new String(c));
}
```

Used for grouping logic.

---

# 12. Sliding Window Concept

Used for:

* Longest substring problems
* Pattern matching
* Optimization

Idea:

```text id="a20"
Expand window → Shrink window → Track result
```

---

# 13. Interview Tricky Case

```java id="a21"
String s = "abcabcbb";

System.out.println(s.substring(0,3));
System.out.println(s.substring(3,6));
```

Output:

```text id="a22"
abc
abc
```

---

# 14. Selenium Real Scenario

## Dynamic Locator Validation

```java id="a23"
String xpath =
"//div[text()='Login']";

if(driver.findElement(By.xpath(xpath)).isDisplayed()){
    System.out.println("Element Found");
}
```

---

## URL Pattern Check

```java id="a24"
String url = driver.getCurrentUrl();

if(url.contains("dashboard")){
    System.out.println("Logged in successfully");
}
```

---

# 15. API Real Scenario

## JSON Validation

```java id="a25"
String status =
response.jsonPath().getString("status");

if(status.equalsIgnoreCase("success")){
    System.out.println("API Passed");
}
```

---

# 16. Short Notes

✔ contains() used for search
✔ substring() used for pattern match
✔ String rotation uses s+s trick
✔ Sliding window used for optimization
✔ Hashing improves duplicate detection
✔ StringBuilder preferred in loops

---

# 17. Revision Sheet

```text id="a26"
Substring → nested loops

Rotation → s+s trick

Palindrome → reverse check

Compression → counting

Sliding Window → optimize substring

Pattern Match → substring + equals
```

---

# Interview Quick Summary

* Brute force → simple but slow
* Sliding window → optimized solution
* Hashing → fast lookup
* StringBuilder → performance improvement
* substring() → core building block

---

# Part 8 Completed

Next Part:

Part 9 - Advanced String Algorithms

Topics:

* KMP Algorithm
* Rabin-Karp
* Trie basics
* Advanced pattern matching
* String hashing
* Real-time system design usage
* Automation framework optimization
