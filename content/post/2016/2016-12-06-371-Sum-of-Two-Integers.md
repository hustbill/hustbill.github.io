---
title: "371. Sum of Two Integers"
date: "2016-12-06 16:06:59"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/sum-of-two-integers/submissions/)
Difficulty: **Easy**
Contributors: **Admin**

Calculate the sum of two integers *a* and *b*, but you are **not allowed** to use the operator +
 and -
.
**Example:**Given *a* = 1 and *b* = 2, return 3.
**Credits:**Special thanks to [@fujiaozhu](https://discuss.leetcode.com/user/fujiaozhu) for adding this problem and creating all test cases.

Hide Company Tags
 [Hulu](https://leetcode.com/company/hulu/)
Hide Tags
 [Bit Manipulation](https://leetcode.com/tag/bit-manipulation/)
Hide Similar Problems
 [(M) Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)
```java
public class Solution {
    // https://discuss.leetcode.com/topic/49771/java-simple-easy-understand-solution-with-explanation/2
    /*
    "&" AND operation, for example, 2 (0010) & 7 (0111) => 2 (0010)
    
    "^" XOR operation, for example, 2 (0010) ^ 7 (0111) => 5 (0101)
    
    "~" NOT operation, for example, ~2(0010) => -3 (1101) what??? Don't get frustrated here. It's called two's complement.
        1111 is -1, in two's complement
        1110 is -2, which is ~2 + 1, ~0010 => 1101, 1101 + 1 = 1110 => 2
        1101 is -3, which is ~3 + 1
        so if you want to get a negative number, you can simply do ~x + 1
        
    Reference:

    https://en.wikipedia.org/wiki/Two%27s_complement
    
    https://www.cs.cornell.edu/~tomf/notes/cps104/twoscomp.html
    
    For this, problem, for example, we have a = 1, b = 3,
    
    In bit representation, a = 0001, b = 0011,
    
    First, we can use "and"("&") operation between a and b to find a carry.
    
    carry = a & b, then carry = 0001
    
    Second, we can use "xor" ("^") operation between a and b to find the different bit, and assign it to a,
    
    Then, we shift carry one position left and assign it to b, b = 0010.
    */
    public int getSum(int a, int b) {
      if (a == 0) return b;
      if (b == 0) return a;
      
      while (b != 0) {
          int carry = a & b ;
          a = a ^ b;
          b = carry << 1;
      }
      return a;
    }
}
```
