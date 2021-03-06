---
title: "38. Count and Say"
date: "2016-12-20 15:45:36"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

 [My Submissions](https://leetcode.com/problems/count-and-say/submissions/)

Total Accepted: **110903**
Total Submissions: **343285**
Difficulty: **Easy**
Contributors: **Admin**

The count-and-say sequence is the sequence of integers beginning as follows:1, 11, 21, 1211, 111221, ...

1
 is read off as "one 1"
 or 11
.11
 is read off as "two 1s"
 or 21
.21
 is read off as "one 2
, then one 1"
 or 1211
.
Given an integer *n*, generate the *n*th
 sequence.
Note: The sequence of integers will be represented as a string.

Hide Company Tags
 [Facebook](https://leetcode.com/company/facebook/)
Hide Tags
 [String](https://leetcode.com/tag/string/)
Hide Similar Problems
 [(M) Encode and Decode Strings](https://leetcode.com/problems/encode-and-decode-strings/)
```java
    /*
     1.     1
     2.     11
     3.     21
     4.     1211
     5.     111221 
     6.     312211
     7.     13112221
     8.     1113213211
     9.     31131211131221
     10.   13211311123113112211
     https://discuss.leetcode.com/topic/2309/show-an-answer-in-java
    */
    public String countAndSay(int n) {
        StringBuilder curr = new StringBuilder("1");
        StringBuilder prev;
        
        int count;
        char say;
        
        for (int i= 1; i < n; i++) {
            prev = curr;
            curr = new StringBuilder();
            count = 1;
            say = prev.charAt(0);
            
            for (int j = 1, len = prev.length(); j < len;j++) {
                if (prev.charAt(j) != say) {
                    curr.append(count).append(say);
                    count = 1;
                    say = prev.charAt(j);
                } else count++;
            }
            curr.append(count).append(say);
        }
        return curr.toString();
    }
```
