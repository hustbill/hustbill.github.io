---
title: "88. Merge Sorted Array"
date: "2017-06-10 11:42:18"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
88. Merge Sorted Array
 **Question
Editorial Solution

 [My Submissions](https://leetcode.com/problems/merge-sorted-array/submissions/)

Total Accepted: **131111**
Total Submissions: **420896**
Difficulty: **Easy**
Contributors: **Admin**

Given two sorted integer arrays *nums1* and *nums2*, merge *nums2* into *nums1* as one sorted array.
**Note:**You may assume that *nums1* has enough space (size that is greater or equal to *m* + *n*) to hold additional elements from *nums2*. The number of elements initialized in *nums1* and *nums2* are *m* and *n* respectively.

Hide Company Tags
 [Microsoft](https://leetcode.com/company/microsoft/) [Bloomberg](https://leetcode.com/company/bloomberg/) [Facebook](https://leetcode.com/company/facebook/)
Hide Tags
 [Array](https://leetcode.com/tag/array/) [Two Pointers](https://leetcode.com/tag/two-pointers/)
Hide Similar Problems
 [(E) Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

```java
 /*
     Test case:
     [1, 4, 7, 0, 0, 0, 0]
    3
    [2, 5]
    2
    result: [1,2,4,5,7,0,0]
    思路： 将两个sorted array 从后往前比较，大的数插在尾部。记住，总共有效元素是m + n个。 数组nums1 其他元素用0来替代。 
          需要用两个while loop。 第一个loop是将两个数组比较与调整。 第二个loop 将nums2 漏网之鱼继续放入nums1中。 例如 上面的测试用例
    */
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int len = m + n - 1;
        int i = m - 1;
        int j = n - 1;
        while (i >= 0 && j >= 0) {
            if (nums1[i] < nums2[j]) {
                nums1[len--] = nums2[j--];
            } else {
                nums1[len--] = nums1[i--];
            } 
        }
        while (j >= 0)  nums1[len--] = nums2[j--];
    
    }
```end
