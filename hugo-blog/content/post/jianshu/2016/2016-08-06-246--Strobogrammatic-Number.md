---
title: "246. Strobogrammatic Number"
date: "2016-08-06 14:48:11"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
246- Strobogrammatic Number
 **Question
Editorial Solution

 [My Submissions](https://leetcode.com/problems/strobogrammatic-number/submissions/)

Total Accepted: **12358**
Total Submissions: **33099**
Difficulty: **Easy**

A strobogrammatic number is a number that looks the same when rotated 180 degrees (looked at upside down).
Write a function to determine if a number is strobogrammatic. The number is represented as a string.
For example, the numbers "69", "88", and "818" are all strobogrammatic.

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [Hash Table](https://leetcode.com/tag/hash-table/) [Math](https://leetcode.com/tag/math/)
Hide Similar Problems
 [(M) Strobogrammatic Number II](https://leetcode.com/problems/strobogrammatic-number-ii/) [(H) Strobogrammatic Number III](https://leetcode.com/problems/strobogrammatic-number-iii/)

```java
import java.util.*;

public class Solution {
    public boolean isStrobogrammatic1(String num) {
       // ref: https://leetcode.com/discuss/50594/4-lines-in-java
       // idea: Just checking the pairs, going inwards from the ends.
       for (int i=0, j= num.length()-1; i<=j ; i++, j--) 
           if(!"00 11 88 969".contains(num.charAt(i) + "" + num.charAt(j)))
               return false;
        return true;
    }
    
    // https://discuss.leetcode.com/topic/21576/accepted-java-solution
    public boolean isStrobogrammatic(String num) {
        Map<Character, Character> map = new HashMap<Character, Character>();
        map.put('0', '0');
        map.put('1', '1');
        map.put('6', '9');
        map.put('8', '8');
        map.put('9', '6');
        
        int l = 0, r = num.length() - 1; 
        while (l <= r) {
            if (!map.containsKey(num.charAt(l))) return false;
            if (map.get(num.charAt(l)) != num.charAt(r)) return false;
            l++;
            r--;
        }
        return true;
       
    }
}
```
