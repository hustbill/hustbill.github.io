---
title: "309. Best Time to Buy and Sell Stock with Cooldown"
date: "2016-06-13 23:38:00"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
Total Accepted: **17241** Total Submissions: **46340** Difficulty: **Medium**

Say you have an array for which the *i*th element is the price of a given stock on day *i*.
Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times) with the following restrictions:
You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).
After you sell your stock, you cannot buy stock on next day. (ie, cooldown 1 day)

**Example:**
prices = [1, 2, 3, 0, 2]
maxProfit = 3
transactions = [buy, sell, cooldown, buy, sell]
**Credits:**
Special thanks to @dietpepsi for adding this problem and creating all test cases.

Hide Company Tags Google
Hide Tags Dynamic Programming
Hide Similar Problems (E) Best Time to Buy and Sell Stock (M) Best Time to Buy and Sell Stock II
```java
public class Solution {
    public int maxProfit(int[] prices) {
        /* https://leetcode.com/discuss/71391/easiest-java-solution-with-explanations
         because of cooldown, after sell, we need cool down one day
         buy[i] = Math.max(buy[i - 1] ,  sell[i - 1] - prices[i]);  两种情况：在第i天可以不买不卖（cooldown） 维持第i-1的profit；或者i-1 卖掉，在i天买入。取两种情况的profit
         sell[i] = Math.max(sell[i - 1],  buy [i - 1] + prices[i]); 也是两种情况：不买不卖； 或者卖掉prices[i], profit 为buy [i - 1] + prices[i]。 取两种情况最大值
         */
        
        if (prices == null || prices.length <= 1) {
            return 0;
        }
        
        int[] buy = new int[prices.length]; // the profit after buy a price[i] or cooldown
        int[] sell = new int[prices.length];
        
        buy[0] = -prices[0];
        sell[0] = 0; 
        buy[1] = Math.max(buy[0], -prices[1]);
        sell[1] = Math.max(sell[0], buy[0] + prices[1]);
          
        for (int i = 2; i < prices.length; i++) {
            buy[i] = Math.max(buy[i - 1] ,  sell[i - 2] - prices[i]);
            sell[i] = Math.max(sell[i - 1], buy[i - 1] + prices[i]);
        }
        
        return sell[prices.length - 1];
        
    }
}
```
