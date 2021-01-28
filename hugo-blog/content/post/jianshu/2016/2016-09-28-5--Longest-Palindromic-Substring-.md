---
title: "5. Longest Palindromic Substring "
date: "2016-09-28 06:20:14"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given a string S, find the longest palindromic substring in S. You may assume that the maximum length of S is 1000, and there exists one unique longest palindromic substring.
```java

// 思路： 从中间向两边扩展。分两个case ： (i, i) 和（i, i+1) 
// Time O(n^2), Space O(1)
//http://www.programcreek.com/2013/12/leetcode-solution-of-longest-palindromic-substring-java/
 public String longestPalindrome(String s) {
  String longest = s.substring(0,1); 
  if (s.isEmpty()) {
   return null;
  }
  if (s.length() == 1) return s;
  
  for (int i = 0; i < s.length(); i++) {
   // get longest palindomr with center of i, i ,  abcba
   String tmp = helper(s, i, i);
   if (tmp.length() > longest.length()) {
    longest = tmp;
   }
   // get longest palindomr with center of i, i+1  abba
   tmp = helper(s, i, i + 1);
   if (tmp.length() > longest.length()) {
    longest = tmp;
   }
  }
  return longest;
    }
  
 public String helper(String s, int start, int end) {
  while (start >= 0 && end < s.length() && s.charAt(start) == s.charAt(end)) {
   start--;
   end++;
  }
  return s.substring(start + 1, end);
 } 
**
```
