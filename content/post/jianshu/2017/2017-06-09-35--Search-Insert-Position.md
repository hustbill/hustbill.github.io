---
title: "35. Search Insert Position"
date: "2017-06-09 09:34:55"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Search Insert Position
===================

[**Description](https://leetcode.com/problems/search-insert-position/#/description)[**Hints](https://leetcode.com/problems/search-insert-position/#/hints)[**Submissions](https://leetcode.com/problems/search-insert-position/#/submissions)[**Solutions](https://leetcode.com/problems/search-insert-position/#/solutions)

Total Accepted: **171574**
Total Submissions: **434381**
Difficulty: **Easy**
Contributor: **LeetCode**

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
You may assume no duplicates in the array.
Here are few examples.
[1,3,5,6], 5 → 2  
[1,3,5,6], 2 → 1  
[1,3,5,6], 7 → 4  
[1,3,5,6], 0 → 0
```java
    public int searchInsert(int[] nums, int target) {
      int start = 0, end = nums.length - 1;
      // [1, 3, 5, 6]  target = 2, 
      // A[start] = A[end] = A[0] = 1 < Target,  start = mid + 1 = 1 > end , out of loop, Then  return start = 1;
      while (start <= end) {
          int mid = start + (end - start) / 2;
          if (nums[mid] == target) {
              return mid;
          } else if (nums[mid] < target) {
              start = mid + 1;
          } else {
              end = mid - 1;
          }
      }
      return start;
    }
```
