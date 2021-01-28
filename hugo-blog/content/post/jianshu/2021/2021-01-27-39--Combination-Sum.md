---
title: "39--Combination-Sum"
date: "2017-04-26"
draft: false
categories: [leetcode]
hiddenFromHomePage: true
---
Given a set of candidate numbers (C) (without duplicates) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

Note:
All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
For example, given candidate set [2, 3, 6, 7] and target 7, 
A solution set is: 
[
  [7],
  [2, 2, 3]
]  

**解题思路 ** 
用回溯算法
```java
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
      List<List<Integer>> res = new ArrayList<>();
      if (candidates == null || candidates.length == 0) return res;
      List<Integer> cur = new ArrayList<>();
      Arrays.sort(candidates);
      backtrack(res, cur, candidates, target, 0);
      return res;
    }
    
    private void backtrack(List<List<Integer>> res, List<Integer> cur, int[] nums, int remain, int start) {
        if (remain < 0) { // 要有退出机制
            return;
        } else if (remain == 0) {
            res.add(new ArrayList<Integer>(cur)); // 不能在此终止，还需要继续寻找可行解
        } else {
            for (int i = start; i < nums.length; i++) {
                cur.add(nums[i]);
                backtrack(res, cur, nums, remain - nums[i], i);  // not i + 1 because we can reuse same elements
                cur.remove(cur.size() - 1);
            }
        }
    }
```
