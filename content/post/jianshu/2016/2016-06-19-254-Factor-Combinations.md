---
title: "254. Factor Combinations"
date: "2016-06-19 13:23:00"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
254 - Factor Combinations

Total Accepted: **9165** Total Submissions: **25833** Difficulty: **Medium**

Numbers can be regarded as product of its factors. For example,
8 = 2 x 2 x 2;
  = 2 x 4.
Write a function that takes an integer *n* and return all possible combinations of its factors.
**Note:** 
You may assume that *n* is always positive.
Factors should be greater than 1 and less than *n*.

**Examples: **
input: 1
output: 
[]
input: 37
output: 
[]
input: 12
output:
[
  [2, 6],
  [2, 2, 3],
  [3, 4]
]
input: 32
output:
[
  [2, 16],
  [2, 2, 8],
  [2, 2, 2, 4],
  [2, 2, 2, 2, 2],
  [2, 4, 4],
  [4, 8]
]

Hide Company Tags LinkedIn Uber
Hide Tags Backtracking
Hide Similar Problems (M) Combination Sum

## 思路 ##
这题和combination sum 比较类似。还是用backtrack方法来做。
factor的范围是 从 [2, 3, 4, ...,  n] ，我们用一个变量pos，来记录每次起始factor。然后在backtrack里面递归执行。最后把验证过的factor加入result里面。  

```java
public class Solution {
    public List<List<Integer>> getFactors(int n) {
         List<List<Integer>> res = new ArrayList<List<Integer>>();
         if (n < 2) return res;
         backtrack(n, 2, new ArrayList<Integer>(), res);
         return res;
    }
    
    public void backtrack(int n, int pos,  List<Integer> cur, List<List<Integer>> res) {
        if ( n == 1) {
            if (cur.size() > 1 ) {
                res.add(new ArrayList<Integer>(cur));
            }
            
        }
        
        for (int i = pos; i <= n; i++) {
            if (n % i == 0) {
                cur.add(i);
                backtrack(n/i,  i ,cur, res);
                cur.remove(cur.size() - 1); 
            }
           
        }
     }
}
```
