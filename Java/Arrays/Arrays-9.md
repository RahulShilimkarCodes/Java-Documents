**# Java Arrays Master Guide**



**# Part 9 - Advanced Array Problems (Product Company Level)**



**---**



**# Table of Contents**



**1. Introduction**

**2. Product Company Interview Strategy**

**3. Two Sum Problem**

**4. Three Sum Problem**

**5. Majority Element**

**6. Dutch National Flag Algorithm**

**7. Best Time to Buy and Sell Stock**

**8. Trapping Rain Water**

**9. Longest Consecutive Sequence**

**10. Maximum Product Subarray**

**11. Maximum Sum Circular Subarray**

**12. Merge Intervals**

**13. Subarray Sum Equals K**

**14. Longest Subarray with Given Sum**

**15. Monotonic Arrays**

**16. Common Optimization Techniques**

**17. Time Complexity Analysis**

**18. Real Selenium Framework Applications**

**19. Real API Testing Applications**

**20. Advanced Interview Questions \& Answers**

**21. Quick Revision Notes**

**22. Final Revision Sheet**



**---**



**# 1. Introduction**



**These questions are commonly asked in:**



**\* Barclays**

**\* Amazon**

**\* Microsoft**

**\* Google**

**\* Oracle**

**\* Goldman Sachs**

**\* JPMorgan**

**\* Adobe**

**\* Walmart Global Tech**



**and many product-based companies.**



**These questions test:**



**```text**

**✔ Data Structures Knowledge**



**✔ Algorithm Skills**



**✔ Optimization Thinking**



**✔ Complexity Analysis**



**✔ Coding Ability**

**```**



**---**



**# 2. Product Company Interview Strategy**



**Always discuss:**



**```text**

**Brute Force Solution**



**↓**



**Better Solution**



**↓**



**Optimal Solution**

**```**



**Interviewers are often more interested in:**



**```text**

**Your thinking process**

**```**



**than memorized code.**



**---**



**# 3. Two Sum Problem**



**Most Famous Interview Question.**



**---**



**## Problem**



**Input:**



**```java**

**int\[] arr = {2,7,11,15};**



**target = 9;**

**```**



**Output:**



**```text**

**2 + 7 = 9**

**```**



**Indexes:**



**```text**

**0,1**

**```**



**---**



**## Brute Force**



**```java**

**for(int i=0;i<arr.length;i++){**



&#x20;   **for(int j=i+1;j<arr.length;j++){**



&#x20;       **if(arr\[i]+arr\[j]==target){**



&#x20;           **System.out.println(i+" "+j);**

&#x20;       **}**

&#x20;   **}**

**}**

**```**



**Complexity:**



**```text**

**O(n²)**

**```**



**---**



**## Optimized Solution**



**HashMap**



**```java**

**Map<Integer,Integer> map =**

**new HashMap<>();**



**for(int i=0;i<arr.length;i++){**



&#x20;   **int diff = target-arr\[i];**



&#x20;   **if(map.containsKey(diff)){**



&#x20;       **System.out.println(**

&#x20;       **map.get(diff)+" "+i);**

&#x20;   **}**



&#x20;   **map.put(arr\[i],i);**

**}**

**```**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**---**



**Interview Favorite.**



**---**



**# 4. Three Sum Problem**



**Input:**



**```java**

**{-1,0,1,2,-1,-4}**

**```**



**Output:**



**```text**

**\[-1,-1,2]**



**\[-1,0,1]**

**```**



**---**



**## Approach**



**Step 1**



**Sort array.**



**Step 2**



**Fix one element.**



**Step 3**



**Apply Two Pointer Technique.**



**---**



**Complexity:**



**```text**

**O(n²)**

**```**



**---**



**Important Product Company Question.**



**---**



**# 5. Majority Element**



**Question:**



**Find element appearing more than:**



**```text**

**n/2 times**

**```**



**Input:**



**```java**

**{2,2,1,1,1,2,2}**

**```**



**Output:**



**```text**

**2**

**```**



**---**



**## Optimal Solution**



**Moore's Voting Algorithm**



**```java**

**int count = 0;**



**int candidate = 0;**



**for(int num : arr){**



&#x20;   **if(count == 0){**



&#x20;       **candidate = num;**

&#x20;   **}**



&#x20;   **count +=**

&#x20;   **(num == candidate) ? 1 : -1;**

**}**

**```**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**Space:**



**```text**

**O(1)**

**```**



**---**



**Interview Favorite.**



**---**



**# 6. Dutch National Flag Algorithm**



**Problem:**



**Sort array containing:**



**```text**

**0**



**1**



**2**

**```**



**Input:**



**```java**

**{2,0,2,1,1,0}**

**```**



**Output:**



**```java**

**{0,0,1,1,2,2}**

**```**



**---**



**Optimal Solution**



**Three Pointers:**



**```java**

**low**



**mid**



**high**

**```**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**Space:**



**```text**

**O(1)**

**```**



**---**



**Asked frequently in product companies.**



**---**



**# 7. Best Time to Buy and Sell Stock**



**Input:**



**```java**

**{7,1,5,3,6,4}**

**```**



**Output:**



**```text**

**5**

**```**



**Buy:**



**```text**

**1**

**```**



**Sell:**



**```text**

**6**

**```**



**Profit:**



**```text**

**5**

**```**



**---**



**Program**



**```java**

**int minPrice =**

**Integer.MAX\_VALUE;**



**int maxProfit = 0;**



**for(int price : prices){**



&#x20;   **minPrice =**

&#x20;   **Math.min(minPrice, price);**



&#x20;   **maxProfit =**

&#x20;   **Math.max(maxProfit,**

&#x20;            **price-minPrice);**

**}**

**```**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**---**



**Extremely common question.**



**---**



**# 8. Trapping Rain Water**



**Advanced Interview Question.**



**Input:**



**```java**

**{4,2,0,3,2,5}**

**```**



**Output:**



**```text**

**9 Units**

**```**



**---**



**Concept:**



**```text**

**Water stored at index**



**=**



**Minimum**



**(leftMax,rightMax)**



**-**



**currentHeight**

**```**



**---**



**Optimal Complexity:**



**```text**

**O(n)**

**```**



**using two pointers.**



**---**



**Very common in Amazon.**



**---**



**# 9. Longest Consecutive Sequence**



**Input:**



**```java**

**{100,4,200,1,3,2}**

**```**



**Output:**



**```text**

**4**

**```**



**Sequence:**



**```text**

**1,2,3,4**

**```**



**---**



**Optimal Solution**



**HashSet**



**```java**

**Set<Integer> set =**

**new HashSet<>();**

**```**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**---**



**Interview Favorite.**



**---**



**# 10. Maximum Product Subarray**



**Input:**



**```java**

**{2,3,-2,4}**

**```**



**Output:**



**```text**

**6**

**```**



**---**



**Why difficult?**



**Because:**



**```text**

**Negative × Negative**



**=**



**Positive**

**```**



**---**



**Track:**



**```text**

**Maximum Product**



**Minimum Product**

**```**



**at each step.**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**---**



**Frequently asked.**



**---**



**# 11. Maximum Sum Circular Subarray**



**Input:**



**```java**

**{5,-3,5}**

**```**



**Output:**



**```text**

**10**

**```**



**Circular:**



**```text**

**5 + 5**

**```**



**---**



**Uses:**



**```text**

**Kadane Algorithm**



**+**



**Total Sum**

**```**



**---**



**Advanced question.**



**---**



**# 12. Merge Intervals**



**Input:**



**```java**

**\[\[1,3],\[2,6],\[8,10],\[15,18]]**

**```**



**Output:**



**```java**

**\[\[1,6],\[8,10],\[15,18]]**

**```**



**---**



**Approach:**



**```text**

**Sort**



**↓**



**Merge Overlaps**

**```**



**---**



**Complexity:**



**```text**

**O(n log n)**

**```**



**---**



**Asked in:**



**\* Amazon**

**\* Google**

**\* Microsoft**



**---**



**# 13. Subarray Sum Equals K**



**Input:**



**```java**

**{1,1,1}**



**k = 2**

**```**



**Output:**



**```text**

**2**

**```**



**---**



**Optimal Solution**



**Prefix Sum + HashMap**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**---**



**Important Interview Problem.**



**---**



**# 14. Longest Subarray with Given Sum**



**Input:**



**```java**

**{1,2,3,1,1,1,1}**



**Target = 6**

**```**



**Output:**



**```text**

**Length = 4**

**```**



**---**



**Techniques:**



**```text**

**Prefix Sum**



**HashMap**



**Sliding Window**

**```**



**depending on array type.**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**---**



**# 15. Monotonic Arrays**



**Definition:**



**Array entirely:**



**```text**

**Increasing**

**```**



**or**



**```text**

**Decreasing**

**```**



**---**



**Example:**



**```java**

**{1,2,3,4,5}**

**```**



**Monotonic.**



**---**



**Example:**



**```java**

**{5,4,3,2}**

**```**



**Monotonic.**



**---**



**Complexity:**



**```text**

**O(n)**

**```**



**---**



**Interview Concept Question.**



**---**



**# 16. Common Optimization Techniques**



**---**



**## Technique 1**



**HashMap**



**Used in:**



**```text**

**Two Sum**



**Prefix Sum**

**```**



**---**



**## Technique 2**



**HashSet**



**Used in:**



**```text**

**Longest Consecutive Sequence**



**Union**



**Intersection**

**```**



**---**



**## Technique 3**



**Two Pointers**



**Used in:**



**```text**

**Three Sum**



**Rain Water**



**Sorted Arrays**

**```**



**---**



**## Technique 4**



**Sliding Window**



**Used in:**



**```text**

**Subarray Problems**

**```**



**---**



**## Technique 5**



**Kadane Algorithm**



**Used in:**



**```text**

**Maximum Sum Problems**

**```**



**---**



**# 17. Time Complexity Analysis**



**| Problem             | Complexity |**

**| ------------------- | ---------- |**

**| Two Sum             | O(n)       |**

**| Three Sum           | O(n²)      |**

**| Majority Element    | O(n)       |**

**| Stock Buy Sell      | O(n)       |**

**| Rain Water          | O(n)       |**

**| Longest Consecutive | O(n)       |**

**| Merge Intervals     | O(n log n) |**

**| Kadane              | O(n)       |**



**---**



**# 18. Real Selenium Framework Applications**



**Although these algorithms appear academic, similar concepts exist in automation frameworks.**



**---**



**## Duplicate Test Data Detection**



**Uses:**



**```text**

**HashSet**

**```**



**---**



**## Dynamic Data Validation**



**Uses:**



**```text**

**Search Algorithms**

**```**



**---**



**## Parallel Execution Tracking**



**Uses:**



**```text**

**HashMap**

**```**



**---**



**## Environment Configuration Validation**



**Uses:**



**```text**

**Array Traversal**

**```**



**---**



**# 19. Real API Testing Applications**



**---**



**## Response Validation**



**Example:**



**```json**

**\[**

&#x20; **{"id":1},**

&#x20; **{"id":2},**

&#x20; **{"id":3}**

**]**

**```**



**Need:**



**```text**

**Duplicate Detection**



**Missing Data Detection**

**```**



**---**



**## Analytics APIs**



**Use:**



**```text**

**Prefix Sum**



**Sliding Window**



**Aggregation Logic**

**```**



**---**



**## Log Analysis**



**Uses:**



**```text**

**HashMap Frequency Counting**

**```**



**---**



**# 20. Advanced Interview Questions \& Answers**



**---**



**## Q1 Why HashMap in Two Sum?**



**Provides:**



**```text**

**O(1)**

**```**



**average lookup.**



**---**



**## Q2 Why Moore's Voting Algorithm?**



**Finds majority element in:**



**```text**

**O(n)**

**```**



**and**



**```text**

**O(1)**

**```**



**space.**



**---**



**## Q3 Why Three Sum is O(n²)?**



**Because:**



**```text**

**Outer Loop**



**+**



**Two Pointer Traversal**

**```**



**---**



**## Q4 Best solution for Maximum Subarray?**



**```text**

**Kadane Algorithm**

**```**



**---**



**## Q5 Best solution for Longest Consecutive Sequence?**



**```text**

**HashSet**

**```**



**---**



**## Q6 Why Merge Intervals needs sorting?**



**To efficiently identify overlaps.**



**---**



**# 21. Quick Revision Notes**



**✔ Two Sum → HashMap**



**✔ Three Sum → Sorting + Two Pointers**



**✔ Majority Element → Moore Voting**



**✔ Stock Buy Sell → Track Minimum**



**✔ Rain Water → Left Max / Right Max**



**✔ Longest Consecutive → HashSet**



**✔ Merge Intervals → Sort + Merge**



**✔ Subarray Sum → Prefix Sum**



**✔ Sliding Window → Fixed Range Optimization**



**✔ Kadane → Maximum Sum**



**---**



**# 22. Final Revision Sheet**



**```text**

**Two Sum**

**→ HashMap**



**Three Sum**

**→ Sort + Two Pointers**



**Majority Element**

**→ Moore Voting**



**DNF Algorithm**

**→ 0,1,2 Sorting**



**Stock Profit**

**→ Track Minimum Price**



**Rain Water**

**→ Two Pointers**



**Longest Consecutive**

**→ HashSet**



**Merge Intervals**

**→ Sorting**



**Subarray Sum K**

**→ Prefix Sum + HashMap**



**Maximum Subarray**

**→ Kadane**



**Sliding Window**

**→ O(n) Optimization**

**```**



**---**



**# Product Company Interview Takeaway**



**If interviewer asks:**



**```text**

**What are the most important advanced array algorithms?**

**```**



**Answer:**



**```text**

**1. Two Sum**

**2. Three Sum**

**3. Kadane Algorithm**

**4. Sliding Window**

**5. Prefix Sum**

**6. Merge Intervals**

**7. Majority Element**

**8. Longest Consecutive Sequence**

**9. Trapping Rain Water**

**10. Stock Buy \& Sell**



**These problems test optimization,**

**data structures,**

**and algorithmic thinking,**

**which are heavily evaluated in**

**product-based company interviews.**

**```**



**---**



**# End of Part 9**



**## Next Part**



**### Part 10 – Arrays in Selenium Automation, TestNG, Framework Design \& API Testing**



**Topics:**



**\* Arrays in Selenium Frameworks**

**\* Arrays in TestNG**

**\* Arrays in Data Providers**

**\* Arrays in API Testing**

**\* Arrays vs Collections in Framework Design**

**\* Real Project Scenarios**

**\* Interview Questions from Automation Projects**

**\* Framework Architecture Examples**

**\* Arrays in Reporting \& Logging**

**\* Enterprise-Level Usage**

