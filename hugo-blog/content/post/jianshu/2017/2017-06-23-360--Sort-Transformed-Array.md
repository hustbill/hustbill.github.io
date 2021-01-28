---
title: "360. Sort Transformed Array"
date: "2017-06-23 12:14:18"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

Given a sorted array of integers nums and integer values a, b and c. Apply a function of the form f(x) = ax2 + bx + c to each element x in the array.

The returned array must be in sorted order.

Expected time complexity: O(n)

Example:
nums = [-4, -2, 2, 4], a = 1, b = 3, c = 5,

Result: [3, 9, 15, 33]

nums = [-4, -2, 2, 4], a = -1, b = 3, c = 5

Result: [-23, -5, 1, 7]  
**解题思路 **  
use two pointers i, j and do a merge-sort like process. depending on sign of a, you may want to start from the beginning or end of the transformed array. 
    - if a > 0   是U型的抛物线， 左右两端大，中间底部小
    - if a < 0   是 n 型的， 左右两端小，中间顶部高
    
```java

    public int[] sortTransformedArray(int[] nums, int a, int b, int c) {
      int n = nums.length;
      int[] res = new int[n];
      int i = 0, j = n - 1;
      int index = a >= 0 ? n - 1 : 0;
      while (i <= j) {
          if (a >= 0) {
              res[index--] = quad(nums[i], a, b, c) >= quad(nums[j], a, b, c) ? quad(nums[i++], a, b, c) : quad(nums[j--], a, b,c);
          } else {
              res[index++] = quad(nums[i], a, b, c) >= quad(nums[j], a, b, c) ? quad(nums[j--], a, b, c) : quad(nums[i++], a, b, c);
          }
      }
      return res;
    }
    
    private int quad(int x, int a, int b, int c) {
        return a * x * x  + b * x + c;
    }
```
