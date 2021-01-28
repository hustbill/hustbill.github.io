---
title: "375. Guess Number Higher or Lower II"
date: "2017-01-03 09:04:10"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

 [My Submissions](https://leetcode.com/problems/guess-number-higher-or-lower-ii/submissions/)

Total Accepted: **14213**
Total Submissions: **40773**
Difficulty: **Medium**
Contributors: **Admin**

We are playing the Guess Game. The game is as follows:

I pick a number from **1** to **n**. You have to guess which number I picked.
Every time you guess wrong, I'll tell you whether the number I picked is higher or lower.
However, when you guess a particular number x, and you guess wrong, you pay **$x**. You win the game when you guess the number I picked.
**Example:**
n = 10, I pick 8.First round: You guess 5, I tell you that it's higher. You pay $5.Second round: You guess 7, I tell you that it's higher. You pay $7.Third round: You guess 9, I tell you that it's lower. You pay $9.Game over. 8 is the number I picked.You end up paying $5 + $7 + $9 = $21.

Given a particular **n ≥ 1**, find out how much money you need to have to guarantee a **win**.
**Hint:**
The best strategy to play the game is to minimize the maximum loss you could possibly face. Another strategy is to minimize the expected loss. Here, we are interested in the **first** scenario.
Take a small example (n = 3). What do you end up paying in the worst case?
Check out [this article](https://en.wikipedia.org/wiki/Minimax) if you're still stuck.
The purely recursive implementation of minimax would be worthless for even a small n. You MUST use dynamic programming.
As a follow-up, how would you modify your code to solve the problem of minimizing the expected loss, instead of the worst-case loss?

**Credits:**Special thanks to [@agave](https://leetcode.com/agave/) and [@StefanPochmann](https://leetcode.com/stefanpochmann/) for adding this problem and creating all test cases.

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/)
Hide Similar Problems
 [(M) Flip Game II](https://leetcode.com/problems/flip-game-ii/) [(E) Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/) [(M) Can I Win](https://leetcode.com/problems/can-i-win/)

```java

    /*
     For each number x in range[i~j]
    we do: result_when_pick_x = x + max{DP([i~x-1]), DP([x+1, j])}
    --> // the max means whenever you choose a number, the feedback is always bad and therefore leads you to a worse branch.
    then we get DP([i~j]) = min{xi, ... ,xj}
    --> // this min makes sure that you are minimizing your cost.
    */
    public int getMoneyAmount(int n) {
      int[][] table = new int[n+1][n+1];
      for (int j = 2; j <=n; j++) {
          for (int i=j-1; i > 0; i--) {
              int globalMin = Integer.MAX_VALUE;
              for (int k = i + 1; k < j; k++) {
                  int localMax = k + Math.max(table[i][k-1], table[k+1][j]);
                  globalMin = Math.min(globalMin, localMax);
              }
              table[i][j] = i+1 == j? i: globalMin;
          }
      }
      return table[1][n];
    }
```
