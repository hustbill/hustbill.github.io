---
title: "278. First Bad Version"
date: "2017-01-03 08:34:55"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/first-bad-version/submissions/)

Total Accepted: **77480**
Total Submissions: **319521**
Difficulty: **Easy**
Contributors: **Admin**

You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.
Suppose you have n
 versions [1, 2, ..., n]
 and you want to find out the first bad one, which causes all the following ones to be bad.
You are given an API bool isBadVersion(version)
 which will return whether version
 is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.
**Credits:**Special thanks to [@jianchao.li.fighter](https://leetcode.com/discuss/user/jianchao.li.fighter) for adding this problem and creating all test cases.

Hide Company Tags
 [Facebook](https://leetcode.com/company/facebook/)
Hide Tags
 [Binary Search](https://leetcode.com/tag/binary-search/)
Hide Similar Problems
 [(M) Search for a Range](https://leetcode.com/problems/search-for-a-range/) [(M) Search Insert Position](https://leetcode.com/problems/search-insert-position/) [(E) Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/)


```java
// update 6/8/2017
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); 
      */
/*
 O(lgN) simple Java solution
  The binary search code:
*/
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int start = 1, end = n ;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (isBadVersion(mid)) {
                end = mid -1;
            } else {
                start = mid + 1;
            }
        }
        return start;
    }
}

/* 
374.
The guess API is defined in the parent class GuessGame.
   @param num, your guess
   @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
      int guess(int num); */

public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int start = 1, end = n;
        // int res = -1;
        while (start < end) {
            int mid = start + (end - start) / 2;
            if (guess(mid) == 0) {
                return mid;
            } else if ( guess(mid) == 1) {
                start = mid + 1;
            } else {
                end = mid ;
            }
        }
       return start;
        
    }
}
```
