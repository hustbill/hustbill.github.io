---
title: "162. Find Peak Element"
date: "2016-11-02 14:42:50"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/find-peak-element/submissions/)

Total Accepted: **87974**
Total Submissions: **250083**
Difficulty: **Medium**
Contributors: **Admin**

A peak element is an element that is greater than its neighbors.
Given an input array where num[i] ≠ num[i+1]
, find a peak element and return its index.
The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.
You may imagine that num[-1] = num[n] = -∞
.
For example, in array [1, 2, 3, 1]
, 3 is a peak element and your function should return the index number 2.
[click to show spoilers.](https://leetcode.com/problems/find-peak-element/#)
**Note:**Your solution should be in logarithmic complexity.

```java
// binary search iterative
    public int findPeakElement(int[] nums) {
        int low = 0;
        int high = nums.length - 1;
        while (low < high) {
            int mid1 = low + (high - low) /2 ;
            int mid2 = mid1 + 1;
            if (nums[mid1] < nums[mid2]) {
                low = mid2;
            } else {
                high = mid1;
            }
        }
        return low;
    }
    
    // https://discuss.leetcode.com/topic/5724/find-the-maximum-by-binary-search-recursion-and-iteration/2
    // Sequential Search:
    public int findPeakElement2(int[] nums) {
         for(int i = 1; i < nums.length; i ++){
            if(nums[i] < nums[i-1]) {
                return i-1;
            }
        } 
        return nums.length - 1;
    }

```
