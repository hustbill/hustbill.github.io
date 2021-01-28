---
title: "168. Excel Sheet Column Title"
date: "2016-06-18 05:24:47"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
168- Excel Sheet Column Title
My Submissions
Question
Editorial Solution
Total Accepted: **64257** Total Submissions: **288620** Difficulty: **Easy**

Given a positive integer, return its corresponding column title as appear in an Excel sheet.
For example:
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
**Credits:**
Special thanks to @ifanchu for adding this problem and creating all test cases.

Hide Company Tags Microsoft Facebook Zenefits
Hide Tags Math
Hide Similar Problems (E) Excel Sheet Column Number
```java
public class Solution {
    
    public static void main(String[] args) {
        Solution sl = new Solution();
        int[] nums = { -1, 0, 1, 26, 27, 28, 731};
        for (int n: nums) {
            System.out.print(sl.convertToTitle(n) + " \t ");
        }
        
    }
   
    
    public String convertToTitle(int n) {
        
        StringBuilder res = new StringBuilder();
        while (n > 0) {
            n--;
            res.insert(0, (char) ('A' + (n %26) ));
            n /= 26;
        }
        return res.toString();
    }
}
```
