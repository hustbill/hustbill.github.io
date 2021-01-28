---
title: "268. Missing Number"
date: "2016-10-10 13:41:20"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

 [My Submissions](https://leetcode.com/problems/missing-number/submissions/)

Total Accepted: **74080**
Total Submissions: **174115**
Difficulty: **Medium**

Given an array containing *n* distinct numbers taken from 0, 1, 2, ..., n
, find the one that is missing from the array.
For example,Given *nums* = [0, 1, 3]
 return 2
.
**Note**:Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?
```java
public int missingNumber(int[] nums) {
        /* Ref:
          1.https://leetcode.com/discuss/58647/line-simple-java-bit-manipulate-solution-with-explaination
          2. https://leetcode.com/discuss/56174/3-different-ideas-xor-sum-binary-search-java-code
          
         The basic idea is to use XOR operation. We all know that a^b^b =a, which means two xor operations with the same number will eliminate the number and reveal the original number. 
         
         In this solution, I apply XOR operation to both the index and value of the array. In a complete array with no missing numbers, the index and value should be perfectly corresponding( nums[index] = index), so in a missing array, what left finally is the missing number.

        */
        int xor = 0, i = 0;
        for (i=0; i<nums.length; i++) {
            xor = xor ^ i ^ nums[i];
        }
        return xor ^ i;
    }
```
