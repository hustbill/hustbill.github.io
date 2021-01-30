---
title: "154. Find Minimum in Rotated Sorted Array II"
date: "2017-06-11 00:29:19"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
[**Description](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/#/description)[**Hints](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/#/hints)[**Submissions](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/#/submissions)[**Solutions](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/#/solutions)

Total Accepted: **77016**
Total Submissions: **209191**
Difficulty: **Hard**
Contributor: **LeetCode**

*Follow up* for "Find Minimum in Rotated Sorted Array":  
**What if *duplicates* are allowed?  
Would this affect the run-time complexity? How and why?  **

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.  
(i.e., 0 1 2 4 5 6 7
 might become 4 5 6 7 0 1 2).  
Find the minimum element.   
The array may contain duplicates.   

Hide Tags
 [Array](https://leetcode.com/tag/array/) [Binary Search](https://leetcode.com/tag/binary-search/)
Hide Similar Problems
 [(M) Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

**解题思路 **
    Binary Search   
    The minimum element must satisfy one of two conditions: 1) If rotate, A[min] < A[min - 1]; 2) If not, A[0].   
       Therefore, we can use binary search:   
          check the middle element, if it is less than previous one, then it is minimum.   
          If not, there are 2 conditions as well:  
             If it is greater than both left and right element, then minimum element should be on its right,   
             otherwise  if it is less than right element,  then minimum element should be on its left.   
               ** when num[mid] == num[right], we couldn't sure the position of minimum in mid's left or right, so just let right reduce one. **
```java
    /*
    using binary search 
    When num[mid] == num[end], we couldn't sure the position of minimum in mid's left or right, so just let end reduce one.
    https://leetcode.com/discuss/19746/my-pretty-simple-code-to-solve-it
    */
    
    public int findMin(int[] nums) {
      if (nums == null || nums.length == 0) {
          return 0;
      }
      if (nums.length == 1) return nums[0];
      
      int start = 0, end = nums.length - 1;
      while (start < end) {
          int mid = start + (end - start) / 2;
          if (mid > 0 && nums[mid] < nums[mid - 1]) {
              return nums[mid];
          }
          
          if (nums[start] <= nums[mid] && nums[mid] > nums[end]) {
              start  = mid + 1; // pivot point is on right of the mid 
          } else if (nums[end] > nums[mid]) {
              end = mid;
          } else {  // when num[mid] and num[end] are same
            end--;
          }
      }
      return nums[start]; // start == end is the samllest value and also the number of places
    }
```
