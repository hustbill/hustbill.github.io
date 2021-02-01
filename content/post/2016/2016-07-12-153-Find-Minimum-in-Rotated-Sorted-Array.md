---
title: "153. Find Minimum in Rotated Sorted Array"
date: "2016-07-12 13:29:26"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
153- Find Minimum in Rotated Sorted Array
 **Question
Editorial Solution

 [My Submissions](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/submissions/)

Total Accepted: **100021**
Total Submissions: **270435**
Difficulty: **Medium**

Suppose a sorted array is rotated at some pivot unknown to you beforehand.
(i.e., 0 1 2 4 5 6 7
 might become 4 5 6 7 0 1 2
).
Find the minimum element.
You may assume no duplicate exists in the array.

Hide Company Tags
 [Microsoft](https://leetcode.com/company/microsoft/)
Hide Tags
 [Array](https://leetcode.com/tag/array/) [Binary Search](https://leetcode.com/tag/binary-search/)
Hide Similar Problems
 [(H) Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) [(H) Find Minimum in Rotated Sorted Array II](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)
```java
 public int findMin(int[] nums) {
        /*
        https://discuss.leetcode.com/topic/5170/java-solution-with-binary-search
        The minimum element must satisfy one of two conditions: 1) If rotate, A[min] < A[min - 1]; 2) If not, A[0]. Therefore, we can use binary search: check the middle element, if it is less than previous one, then it is minimum. If not, there are 2 conditions as well: If it is greater than both left and right element, then minimum element should be on its right, otherwise on its left.
        */


  int start = 0, end = nums.length - 1;

  while (start < end) {
   int mid = start + (end - start) / 2;
   if (nums[end] < nums[mid]) {
    start = mid + 1; // 转折点在mid 的右侧
   } else {
    end = mid;
   }
  }
  return nums[start];
  // start == end is the smallest value and also the number of places
  }

```
