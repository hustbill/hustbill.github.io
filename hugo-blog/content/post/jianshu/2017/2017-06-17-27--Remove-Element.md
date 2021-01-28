---
title: "27. Remove Element"
date: "2017-06-17 09:41:31"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given an array and a value, remove all instances of that value in place and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

Example:
Given input array nums = [3,2,2,3], val = 3

Your function should return length = 2, with the first two elements of nums being 2.
**解题思路 **
basic idea:  when elem is found at index i, let nums[i] = the last elment in the modifying array, then repeat searching until elem is not found.  
  
```java
    public int removeElement(int[] nums, int val) {
      int len = nums.length;
      for (int i = 0; i < len; ++i) {
          while (nums[i] == val && i < len) {
              nums[i] = nums[--len];
          }
      }
      return len;
    }
```
