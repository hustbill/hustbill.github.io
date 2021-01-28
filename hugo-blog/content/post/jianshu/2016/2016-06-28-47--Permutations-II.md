---
title: "47. Permutations II"
date: "2016-06-28 01:28:39"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
47- Permutations II
Total Accepted: **75673** Total Submissions: **264907** Difficulty: **Medium**

Given a collection of numbers that might contain duplicates, return all possible unique permutations.
For example,
[1,1,2] have the following unique permutations:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]

Hide Company Tags LinkedIn Microsoft
Hide Tags Backtracking
Hide Similar Problems (M) Next Permutation (M) Permutations (M) Palindrome Permutation II
```java
public class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        /*https://leetcode.com/discuss/73856/really-easy-solution-easier-than-solutions-with-very-high-vote
        Use an extra boolean array " boolean[] used" to indicate whether the value is added to list.
        Sort the array "int[] nums" to make sure we can skip the same value.
        when a number has the same value with its previous, we can use this number only if his previous is used*/
        
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> cur = new ArrayList<>();
        
        if (nums == null || nums.length == 0) {
            return res;
        }
        
        boolean[] visited = new boolean[nums.length];
        Arrays.sort(nums); // 
        backtrack(nums, visited, cur, res);
        return res;
    }
    
    public void backtrack(int[] nums, boolean[] visited, List<Integer> cur, List<List<Integer>> res) {
        if (cur.size() == nums.length ) {
            res.add( new ArrayList<Integer>(cur));
            return;
        }
        
        for (int i = 0; i < nums.length; i++) {
            if (!visited[i]) {
                if (i > 0 && nums[i] == nums[i-1] && visited[i-1]) {
                    return;
                }
                cur.add(nums[i]);
                visited[i] = true;
                backtrack(nums, visited, cur, res);
                visited[i] = false;
                cur.remove(cur.size() - 1);
                    
            }
          
     
        }
    }
}
```
