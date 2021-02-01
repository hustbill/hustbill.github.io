---
title: "93. Restore IP Addresses"
date: "2016-06-14 07:40:25"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
93 Restore IP Addresses

Total Accepted: **58138** Total Submissions: **243785** Difficulty: **Medium**

Given a string containing only digits, restore it by returning all possible valid IP address combinations.
For example:
Given "25525511135",
return ["255.255.11.135", "255.255.111.35"]. (Order does not matter)

Hide Tags Backtracking String
```java
public class Solution {
    public List<String> restoreIpAddresses(String s) {
        // use backtrack, divides the string s into 4 substring: s1, s2, s3, s4. 
        // for each part (xxx), we have three options (1, 2, 3)
        // https://leetcode.com/discuss/15098/very-simple-dfs-solution
        List<String> res = new ArrayList<>();
        backtrack(res, s, "", 0, 0);
        return res;
    }
    
    public void backtrack(List<String> res, String s, String ip, int pos, int count) {
        if (count > 4) return ;
        if (count == 4 && pos == s.length())  res.add(ip);
        
        for( int i = 1; i <= 3; i++) {
            if (pos + i > s.length()) return;
            
            String str = s.substring(pos, pos + i);
            
            if ((str.startsWith("0") && str.length() > 1)  || (Integer.parseInt(str) >= 256)) return;
            backtrack(res, s, ip + str + (count ==3 ? "" : "."), pos + i, count + 1);
        }
    }
}
```
