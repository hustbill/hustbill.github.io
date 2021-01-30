---
title: "247. Strobogrammatic Number II"
date: "2016-08-06 15:08:19"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

 [My Submissions](https://leetcode.com/problems/strobogrammatic-number-ii/submissions/)

Total Accepted: **10689**
Total Submissions: **30073**
Difficulty: **Medium**

A strobogrammatic number is a number that looks the same when rotated 180 degrees (looked at upside down).
Find all strobogrammatic numbers that are of length = n.
For example,Given n = 2, return ["11","69","88","96"]
.
**Hint:**
Try to use recursion and notice that it should recurse with *n* - 2 instead of *n* - 1.

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [Math](https://leetcode.com/tag/math/) [Recursion](https://leetcode.com/tag/recursion/)
Hide Similar Problems
 [(E) Strobogrammatic Number](https://leetcode.com/problems/strobogrammatic-number/) [(H) Strobogrammatic Number III](https://leetcode.com/problems/strobogrammatic-number-iii/)
```java
public class Solution {
    // https://discuss.leetcode.com/topic/20753/ac-clean-java-solution
    public List<String> findStrobogrammatic(int n) {
        return helper(n, n);
    }
    
    private List<String> helper(int n, int m) {
        if (n == 0) return new ArrayList<String>(Arrays.asList(""));
        if (n == 1) return new ArrayList<String>(Arrays.asList("0", "1", "8"));
        
        List<String> list = helper(n - 2, m);
        
        List<String> res = new ArrayList<String>();
        for (int i = 0; i < list.size(); i++) {
            String s = list.get(i);
            if (n != m) res.add("0" + s + "0");
              
            res.add("1" + s + "1");
            res.add("6" + s + "9");
            res.add("8" + s + "8");
            res.add("9" + s + "6");
        }
        return res;
    }
}
```
