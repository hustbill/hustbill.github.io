---
title: " 260. Single Number III"
date: "2016-10-10 14:29:33"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/single-number-iii/submissions/)

Total Accepted: **49927**
Total Submissions: **104463**
Difficulty: **Medium**

Given an array of numbers nums
, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.
For example:
Given nums = [1, 2, 1, 3, 2, 5]
, return [3, 5]
.
**Note**:
The order of the result is not important. So in the above example, [5, 3]
 is also correct.
Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?

```java
**/*
  * 假定这两数为a和b。做法分两步走，第一步用xor 求出a和b的xor －diff，然后求diff & 它的二补数，得到a和b的不同位。
  接着把数组根据 diff & num == 0 分成两个group，分别对两个group进行xor，得到最终a和b
  
  * In the first pass, we XOR all elements in the array, and get the XOR of
  * the two numbers we need to find. Note that since the two numbers are
  * distinct, so there must be a set bit (that is, the bit with value '1') in
  * the XOR result. Find out an arbitrary set bit (for example, the rightmost
  * set bit).
  * 
  * In the second pass, we divide all numbers into two groups, one with the
  * aforementioned bit set, another with the aforementinoed bit unset. Two
  * different numbers we need to find must fall into the two distrinct
  * groups. XOR numbers in each group, we can find a number in either group.
  * 
  * Complexity:
  * 
  * Time: O (n)
  * 
  * Space: O (1)
  * 
  * A Corner Case:
  * 
  * When diff == numeric_limits<int>::min(), -diff is also
  * numeric_limits<int>::min(). Therefore, the value of diff after executing
  * diff &= -diff is still numeric_limits<int>::min(). The answer is still
  * correct.
  * https://discuss.leetcode.com/topic/21605/accepted-c-java-o-n-time-o-1-space-easy-solution-with-detail-explanations
  */
 public int[] singleNumber(int[] nums) {
  // Pass 1 :
  // Get the XOR of the two numbers we need to find
  int diff = 0;
  for (int num : nums) {
   diff ^= num;
  }
  // System.out.println(diff);  // ( diff = 8 ^ 4 = 12,  1100)
  // Get its last set bit
  diff &= -diff;     // -diff  是diff的二补数    0011 + 1 = 0100 = 4;   12 &=4  -> 4
  // https://en.wikipedia.org/wiki/Two%27s_complement
  //System.out.println(diff);
  // Pass 2 :
  int[] rets = { 0, 0 }; // this array stores the two numbers we will
        // return
  for (int num : nums) {
   if ((num & diff) == 0) // the bit is not set
   {
    rets[0] ^= num;
   } else // the bit is set
   {
    rets[1] ^= num;
   }
  }
  return rets;
 }
```
