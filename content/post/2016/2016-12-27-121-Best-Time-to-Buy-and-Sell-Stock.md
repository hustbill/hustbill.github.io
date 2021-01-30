---
title: "121. Best Time to Buy and Sell Stock"
date: "2016-12-27 00:18:29"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/submissions/)

Total Accepted: **152541**
Total Submissions: **391716**
Difficulty: **Easy**
Contributors: **Admin**

Say you have an array for which the *i*th
 element is the price of a given stock on day *i*.
If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.
**Example 1:**
Input: [7, 1, 5, 3, 6, 4]Output: 5max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)

**Example 2:**
Input: [7, 6, 4, 3, 1]Output: 0In this case, no transaction is done, i.e. max profit = 0.


Hide Company Tags
 [Amazon](https://leetcode.com/company/amazon/) [Microsoft](https://leetcode.com/company/microsoft/) [Bloomberg](https://leetcode.com/company/bloomberg/) [Uber](https://leetcode.com/company/uber/) [Facebook](https://leetcode.com/company/facebook/)
Hide Tags
 [Array](https://leetcode.com/tag/array/) [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/)
Hide Similar Problems
 [(M) Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) [(M) Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/) [(H) Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/) [(H) Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)[(M) Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)


```java
 public int maxProfit(int[] prices) {
        if (prices.length == 0) {
            return 0;
        }
        
        int max = 0;
        int sofarMin =  prices[0];
        
        for (int i = 0; i < prices.length; i++) {
            if (prices[i] > sofarMin ) {
                max = Math.max(max, prices[i] - sofarMin); 
            } else {
                sofarMin = prices[i];
            }
        }
        return max;
    }
```
