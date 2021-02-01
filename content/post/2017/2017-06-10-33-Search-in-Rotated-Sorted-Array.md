---
title: "33. Search in Rotated Sorted Array"
date: "2017-06-10 12:38:57"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
[**Description](https://leetcode.com/problems/search-in-rotated-sorted-array/#/description)[**Hints](https://leetcode.com/problems/search-in-rotated-sorted-array/#/hints)[**Submissions](https://leetcode.com/problems/search-in-rotated-sorted-array/#/submissions)[**Solutions](https://leetcode.com/problems/search-in-rotated-sorted-array/#/solutions)

Total Accepted: **168414**
Total Submissions: **524192**
Difficulty: **Medium**
Contributor: **LeetCode**

Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.
(i.e., 0 1 2 4 5 6 7
 might become 4 5 6 7 0 1 2
).
You are given a target value to search. If found in the array return its index, otherwise return -1.
You may assume no duplicate exists in the array.

Hide Company Tags
 [LinkedIn](https://leetcode.com/company/linkedin/) [Bloomberg](https://leetcode.com/company/bloomberg/) [Uber](https://leetcode.com/company/uber/) [Facebook](https://leetcode.com/company/facebook/) [Microsoft](https://leetcode.com/company/microsoft/)
Hide Tags
 [Binary Search](https://leetcode.com/tag/binary-search/) [Array](https://leetcode.com/tag/array/)
Hide Similar Problems
 [(M) Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/) [(M) Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

** 解题思路 **  
     Use Binary Search  
     The idea is that when rotating the array, there must be one half of the array that is still in sorted order.  
     For example, 6 7 1 2 3 4 5, the order is disrupted from the point between 7 and 1. So when doing binary search, we can make a judgement that which part is ordered and whether the target is in that range, if yes, continue the search in that half, if not continue in the other half.  

```java

    /*
     Use Binary Search
     The idea is that when rotating the array, there must be one half of the array that is still in sorted order.
     For example, 6 7 1 2 3 4 5, the order is disrupted from the point between 7 and 1. So when doing binary search, we can make a judgement that which part is ordered and whether the target is in that range, if yes, continue the search in that half, if not continue in the other half.
    */
    public int search(int[] nums, int target) {
      int start = 0, end = nums.length - 1;
      while (start <= end) {
          int mid = start + (end - start) /2 ;
          int val = nums[mid];
          if (val == target) {
              return mid;
          }
          
          if (nums[start] <= val) {
              if (target < val && target >= nums[start]) {
                  end = mid - 1;
              } else {
                  start = mid + 1;
              }
          } 
          
          if (val <= nums[end]) {
              if (target > val && target <= nums[end]) {
                  start = mid + 1;
              } else {
                  end = mid - 1;
              }
          }
      }
      return - 1;        
    }
```
