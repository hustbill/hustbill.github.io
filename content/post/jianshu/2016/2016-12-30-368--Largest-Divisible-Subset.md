---
title: "368. Largest Divisible Subset"
date: "2016-12-30 11:46:44"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given a set of **distinct** positive integers, find the largest subset such that every pair (Si, Sj) of elements in this subset satisfies:  
Si % Sj  = 0 or Sj % Si = 0.  
If there are multiple solutions, return any subset is fine.
**Example 1:**
nums: [1,2,3]Result: [1,2] (of course, [1,3] will also be ok)

**Example 2:**
nums: [1,2,4,8]Result: [1,2,4,8]

**Credits:**Special thanks to [@Stomach_ache](https://leetcode.com/stomach_ache) for adding this problem and creating all test cases.

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/) [Math](https://leetcode.com/tag/math/)

```java
    /*
    1. Sort
    2. FInd the length of longest subset
    3. Record the largest element of it.
    4. DO a loop from the largest element to num[0], add every element belong to the logest subset.
    */
    public List<Integer> largestDivisibleSubset(int[] nums) {
        List<Integer> res = new ArrayList<Integer>();
        if (nums == null || nums.length == 0) return res;
        Arrays.sort(nums);
        
        int[] dp = new int[nums.length];
        dp[0] = 1;
        
        // for each element in nums; find the length of largest subset it has.
        for (int i = 1; i < nums.length; i++) {
            for (int j = i - 1; j >= 0; j--) {
                if (nums[i] % nums[j] == 0) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
        }
        
        // pick the index of the largest element in dp.
        int maxIndex = 0;
        for (int i = 1; i < nums.length; i++) {
            maxIndex = dp[i] > dp[maxIndex] ? i : maxIndex;
        }
        
        // from nums[maxIndex] to 0, add every element belongs to the largest subset
        int temp = nums[maxIndex];
        int curDp = dp[maxIndex];
        
        for (int i = maxIndex; i >= 0; i--) {
            if (temp % nums[i] == 0 && dp[i] == curDp) {
                res.add(nums[i]);
                temp = nums[i];
                curDp--;
            }
        }
        return res;
    }

```
