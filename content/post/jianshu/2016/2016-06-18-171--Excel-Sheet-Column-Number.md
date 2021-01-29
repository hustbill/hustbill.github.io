---
title: "171. Excel Sheet Column Number"
date: "2016-06-18 05:26:21"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

171 - Excel Sheet Column Number

Total Accepted: **84177** Total Submissions: **198174** Difficulty: **Easy**

Related to question Excel Sheet Column Title
Given a column title as appear in an Excel sheet, return its corresponding column number.
For example:
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
**Credits:**
Special thanks to @ts for adding this problem and creating all test cases.

Hide Company Tags Microsoft Uber
Hide Tags Math
Hide Similar Problems (E) Excel Sheet Column Title

```java
public class Solution {
    public int titleToNumber(String s) {
        int res = 0;
        for(int i = 0; i < s.length(); i++) {
            res = 26 * res +  (s.charAt(i) - 'A' + 1);
        }
        
        return res;
    }
}
```
