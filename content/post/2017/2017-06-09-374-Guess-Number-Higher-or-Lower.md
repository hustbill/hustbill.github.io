---
title: "374. Guess Number Higher or Lower"
date: "2017-06-09 10:13:28"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
[**Description](https://leetcode.com/problems/guess-number-higher-or-lower/#/description)[**Hints](https://leetcode.com/problems/guess-number-higher-or-lower/#/hints)[**Submissions](https://leetcode.com/problems/guess-number-higher-or-lower/#/submissions)[**Solutions](https://leetcode.com/problems/guess-number-higher-or-lower/#/solutions)

Total Accepted: **46483**
Total Submissions: **133710**
Difficulty: **Easy**
Contributor: **LeetCode**

We are playing the Guess Game. The game is as follows:

I pick a number from **1** to ***n***. You have to guess which number I picked.
Every time you guess wrong, I'll tell you whether the number is higher or lower.
You call a pre-defined API guess(int num)
 which returns 3 possible results (-1
, 1
, or 0
):
-1 : My number is lower 1 : My number is higher 0 : Congrats! You got it!
**Example:**
n = 10, I pick 6.Return 6.

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [Binary Search](https://leetcode.com/tag/binary-search/)
Hide Similar Problems
 [(E) First Bad Version](https://leetcode.com/problems/first-bad-version/) [(M) Guess Number Higher or Lower II](https://leetcode.com/problems/guess-number-higher-or-lower-ii/)

```java
/* The guess API is defined in the parent class GuessGame.
   @param num, your guess
   @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
      int guess(int num); */

public class Solution extends GuessGame {
    public int guessNumber(int n) {
      int start = 0, end = n;
      while (start <= end) {
          int mid = start + (end - start) / 2;
          int val = guess(mid);
          if (val == 0) {
              return mid;
          } else if (val == -1) {
              end = mid - 1;
          } else if (val == 1) {
              start = mid + 1;
          }
      }
       return start; 
    }
}
```
