---
title: "209--Minimum-Size-Subarray-Sum"
date: "2017-04-26"
draft: false
categories: [leetcode]
hiddenFromHomePage: true
---
Given an array of **n** positive integers and a positive integer **s**, find the minimal length of a **contiguous** subarray of which the sum ≥ **s**. If there isn't one, return 0 instead.
For example, given the array [2,3,1,2,4,3]
 and s = 7,   
the subarray [4,3] has the minimal length under the problem constraint.

[click to show more practice.](https://leetcode.com/problems/minimum-size-subarray-sum/#)
**More practice:**If you have figured out the *O*(*n*) solution, try coding another solution of which the time complexity is *O*(*n* log *n*).

**Credits:**Special thanks to [@Freezen](https://oj.leetcode.com/discuss/user/Freezen) for adding this problem and creating all test cases.

Hide Company Tags
 [Facebook](https://leetcode.com/company/facebook/)
Hide Tags
 [Array](https://leetcode.com/tag/array/) [Two Pointers](https://leetcode.com/tag/two-pointers/) [Binary Search](https://leetcode.com/tag/binary-search/)
Hide Similar Problems
 [(H) Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/) [(M) Maximum Size Subarray Sum Equals k](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/)   

** 解题思路 **
Two pointers, O(n) Time complexity  

```java 
/**
     * @param nums: an array of integers
     * @param s: an integer
     * @return: an integer representing the minimum size of subarray
     */
    public int minimumSize(int[] nums, int s) {
        if (nums == null || nums.length == 0) return -1;
        
        int i = 0, j = 0, sum = 0, min = Integer.MAX_VALUE;
        
        while (j < nums.length) {
            if (sum < s && j < nums.length) {        
              sum += nums[j++];
            }
            while (sum >=s ) {
                min = Math.min(min, j - i);
                sum -= nums[i++];
            }
        }
        return min == Integer.MAX_VALUE ? -1 : min;
    }
```
