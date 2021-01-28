---
title: "88--Merge-Sorted-Array-1"
date: "2017-04-26"
draft: false
categories: [user-1647554-1611798760]
hiddenFromHomePage: true
---
[**Description](https://leetcode.com/problems/merge-sorted-array/#/description)[**Hints](https://leetcode.com/problems/merge-sorted-array/#/hints)[**Submissions](https://leetcode.com/problems/merge-sorted-array/#/submissions)[**Solutions](https://leetcode.com/problems/merge-sorted-array/#/solutions)

Total Accepted: **162541**
Total Submissions: **510745**
Difficulty: **Easy**
Contributor: **LeetCode**

Given two sorted integer arrays *nums1* and *nums2*, merge *nums2* into *nums1* as one sorted array.
**Note:**You may assume that *nums1* has enough space (size that is greater or equal to *m* + *n*) to hold additional elements from *nums2*. The number of elements initialized in *nums1* and *nums2* are *m* and *n* respectively.

Hide Company Tags
 [Microsoft](https://leetcode.com/company/microsoft/) [Bloomberg](https://leetcode.com/company/bloomberg/) [Facebook](https://leetcode.com/company/facebook/)
Hide Tags
 [Array](https://leetcode.com/tag/array/) [Two Pointers](https://leetcode.com/tag/two-pointers/)
Hide Similar Problems
 [(E) Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

** 解题思路 **  
use two pointers , 从两个array 最后面开始merge
 
```java
    // use two pointers , 从两个array 最后面开始merge
    public void merge(int[] nums1, int m, int[] nums2, int n) {
      int i = m - 1;
      int j = n - 1;
      int k = m + n - 1;
      while (i >= 0  && j >= 0) {
          nums1[k--] = (nums1[i] > nums2[j]) ? nums1[i--] : nums2[j--];
      }
      
      while (j >= 0 ) {
          nums1[k--] = nums2[j--];
      }
    }
```
