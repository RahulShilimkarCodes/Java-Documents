# Java String Master Guide

# Part 9 - Advanced String Algorithms

---

# Table of Contents

1. Introduction to Advanced String Algorithms
2. Why Advanced Algorithms Matter
3. Pattern Matching Overview
4. KMP Algorithm (Knuth–Morris–Pratt)
5. LPS Array Concept (Longest Prefix Suffix)
6. KMP Implementation (Simplified Java)
7. Rabin-Karp Algorithm
8. Rolling Hash Concept
9. Trie Data Structure Basics
10. String Hashing Concept
11. Advanced Use Cases in Frameworks
12. Performance Comparison of Algorithms
13. Interview Tricky Questions
14. Selenium & API Real Use Cases
15. Short Notes
16. Revision Sheet

---

# 1. Introduction to Advanced String Algorithms

Advanced string algorithms are used to solve:

* Pattern matching problems
* Large-scale text searching
* Search engines
* Automation frameworks (log analysis, reporting)
* API payload validation

---

# 2. Why Advanced Algorithms Matter

Brute force string matching:

```text id="b1"
O(n × m)
```

Advanced algorithms:

```text id="b2"
O(n + m)
```

Huge performance improvement for large data.

---

# 3. Pattern Matching Overview

Goal:

Find pattern inside text efficiently.

Example:

```text id="b3"
Text:    "ababcabcabababd"
Pattern: "ababd"
```

---

# 4. KMP Algorithm

KMP avoids rechecking characters.

Key idea:

```text id="b4"
Do not re-match already matched characters
```

Uses LPS array.

---

# 5. LPS Array (Longest Prefix Suffix)

Example:

Pattern:

```text id="b5"
ababd
```

LPS:

```text id="b6"
0 0 1 2 0
```

Meaning:

* Prefix = suffix match length

---

# 6. KMP Algorithm (Simplified Java)

```java id="c1"
public class KMP {

    static int[] buildLPS(String pat) {
        int[] lps = new int[pat.length()];
        int len = 0;
        int i = 1;

        while(i < pat.length()) {
            if(pat.charAt(i) == pat.charAt(len)) {
                len++;
                lps[i] = len;
                i++;
            } else {
                if(len != 0) {
                    len = lps[len - 1];
                } else {
                    lps[i] = 0;
                    i++;
                }
            }
        }
        return lps;
    }

    static boolean kmpSearch(String text, String pat) {
        int[] lps = buildLPS(pat);

        int i = 0, j = 0;

        while(i < text.length()) {
            if(text.charAt(i) == pat.charAt(j)) {
                i++; j++;
            }

            if(j == pat.length()) {
                return true;
            }

            else if(i < text.length() && text.charAt(i) != pat.charAt(j)) {
                if(j != 0) {
                    j = lps[j - 1];
                } else {
                    i++;
                }
            }
        }

        return false;
    }
}
```

---

# 7. Rabin-Karp Algorithm

Uses hashing instead of character comparison.

Idea:

```text id="c2"
Compare hash values first → then confirm match
```

---

# 8. Rolling Hash Concept

Example:

```text id="c3"
"abc" → hash value
```

Next window:

```text id="c4"
"bcd" → updated hash (not recomputed fully)
```

Efficiency:

```text id="c5"
O(1) update per shift
```

---

# 9. Rabin-Karp Example (Simplified)

```java id="c6"
public class RabinKarp {

    static final int d = 256;
    static final int q = 101;

    static boolean search(String text, String pat) {

        int m = pat.length();
        int n = text.length();

        int p = 0, t = 0, h = 1;

        for(int i = 0; i < m-1; i++)
            h = (h * d) % q;

        for(int i = 0; i < m; i++) {
            p = (d * p + pat.charAt(i)) % q;
            t = (d * t + text.charAt(i)) % q;
        }

        for(int i = 0; i <= n - m; i++) {

            if(p == t) {
                if(text.substring(i, i+m).equals(pat))
                    return true;
            }

            if(i < n-m) {
                t = (d*(t - text.charAt(i)*h) + text.charAt(i+m)) % q;

                if(t < 0)
                    t += q;
            }
        }

        return false;
    }
}
```

---

# 10. Trie Data Structure (Basics)

Used for:

* Auto-suggestions
* Search engines
* Dictionary matching

Structure:

```text id="c7"
Root
 ├── a
 │    ├── p
 │    └── r
 └── b
```

---

# 11. Trie Node Example

```java id="c8"
class TrieNode {
    TrieNode[] children = new TrieNode[26];
    boolean isEnd;
}
```

---

# 12. String Hashing Concept

Used in:

* Fast comparisons
* Duplicate detection
* Large dataset validation

Idea:

```text id="c9"
String → numeric hash
```

Example:

```java id="c10"
int hash = "Java".hashCode();
```

---

# 13. Performance Comparison

| Algorithm   | Complexity | Use Case                |
| ----------- | ---------- | ----------------------- |
| Brute Force | O(n×m)     | Small input             |
| KMP         | O(n+m)     | Fast pattern matching   |
| Rabin-Karp  | O(n+m) avg | Multiple pattern search |
| Trie        | O(m)       | Prefix search           |

---

# 14. Selenium Real Use Case

## Dynamic Element Search

```java id="c11"
String xpath = "//div[text()='Login']";

driver.findElement(By.xpath(xpath));
```

KMP-like logic used internally in search engines.

---

## Log Parsing

```java id="c12"
if(log.contains("ERROR")){
    System.out.println("Failure detected");
}
```

---

# 15. API Real Use Case

## Payload Validation

```java id="c13"
String response = responseBody.asString();

if(response.contains("\"status\":\"success\"")){
    System.out.println("API Passed");
}
```

---

# 16. Short Notes

✔ KMP avoids rechecking characters
✔ LPS stores prefix-suffix info
✔ Rabin-Karp uses hashing
✔ Rolling hash improves performance
✔ Trie used for prefix search
✔ hashCode() used for quick compare
✔ Brute force is slow for large data

---

# 17. Revision Sheet

```text id="c14"
KMP → O(n+m) pattern match

LPS → Prefix-Suffix table

Rabin-Karp → Hash-based matching

Trie → Prefix search structure

Hashing → Fast comparison

Brute Force → O(n×m)
```

---

# Interview Quick Summary

* KMP is fastest deterministic pattern matching
* Rabin-Karp uses hashing + collision check
* Trie used in autocomplete systems
* Hashing improves performance significantly
* Used in search engines + frameworks

---

# Part 9 Completed

Next Part:

Part 10 - String Performance Optimization

Topics:

* Memory tuning for Strings
* GC optimization
* String pooling strategies
* Framework-level performance improvements
* Real Selenium/API bottlenecks
* Advanced interview questions
