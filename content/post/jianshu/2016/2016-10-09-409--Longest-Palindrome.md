---
title: "409. Longest Palindrome"
date: "2016-10-09 15:16:27"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

 [My Submissions](https://leetcode.com/problems/longest-palindrome/submissions/)

Total Accepted: **5510**
 Total Submissions: **12152**
 Difficulty: **Easy**

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.
This is case sensitive, for example "Aa"
 is not considered a palindrome here.
**Note:**Assume the length of given string will not exceed 1,010.
**Example:**
Input:"abccccdd"Output:7Explanation:One longest palindrome that can be built is "dccaccd", whose length is 7.

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [Hash Table](https://leetcode.com/tag/hash-table/)
Hide Similar Problems
 [(E) Palindrome Permutation](https://leetcode.com/problems/palindrome-permutation/)

```java
  public int longestPalindrome(String s) {
        if(s == null || s.length() == 0 ) return 0;

        int count = 0;
        HashSet<Character> set = new HashSet<>();
        for (int i = 0; i < s.length(); i++) {
            if (set.contains(s.charAt(i))) {
                set.remove(s.charAt(i));
                count++;
            }  else {
                set.add(s.charAt(i));
            }
        }
        
        if (!set.isEmpty()) return count*2  + 1;
        return count * 2;
    }
    // ref: https://discuss.leetcode.com/topic/61300/simple-hashset-solution-java
```
