---
title: "Lending-club-onsite-interview"
date: "2016-05-18"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
5/5 phone interview  
5/18 onsite interview  

## 第一轮 （Core Java）
本来是一个senior engineer来面的，结果因为两个building之间衔接问题。耽误了十分钟。来了一个比较年轻的印度裔工程师。他问了一下大致情况，就开始做题了。leetcode 原题[121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)   
Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.
下面是我七个月前写的方法。可惜在现场没想起来这个解法。只给出了用two pointer的解法。肯定不是优化解法了。  

```java

    public int maxProfit(int[] prices) {
        // The logic to solve this problem is same as "max subarray problem" using Kadane's Algorithm
        int maxCur=0, maxSofar =0;
        
        if(prices == null || prices.length ==0) return maxSofar;
        
        for (int i=1; i< prices.length; i++) {
            maxCur = Math.max(0, maxCur += prices[i] - prices[i-1]);
            maxSofar = Math.max(maxCur, maxSofar);
        }
        return maxSofar;
        // Reference 1 :  https://leetcode.com/discuss/48378/kadanes-algorithm-since-mentioned-about-interviewer-twists
        // Reference 2: https://en.wikipedia.org/wiki/Maximum_subarray_problem
    }
```

他接着问了HashMap的问题，如果两个key有相同的hashcode， 怎么处理，我当时没回答好，他说可以用tree来处理，可以将 (key, val1) 作为一个node，(key, val2) 作为另外一个node，同时挂在同一个hashcode下面，这样就可以找到不同的val。 

## 第二轮 白人 director of engineering
个子瘦小，胳膊上都有纹身，带着黑框眼镜，透着精干。给我讲了一下公司的盈利模式，问我是否知道竞争对手。我没记住名字。问了Agile / scrum 问题。
重点是一个behavior 问题。假设你的老板有一个很好的idea，要实施一个feature，他认为很有前景，给你一小时思考，你会怎么回答他。


## 第三轮 印度裔姑娘 　algorithms
一道题，将数字转换成string。题目不难。我最后给的方法不是最优解。应该是用recursive的方法来解决。我费了很大劲才解决。写了一黑板。 其实这个题目，我之前做的时候，好像使用recursive来解决的。 快结束的时候，我提了一下，可以用recursive来做。她就给我指出来，可以怎么recursive来做。真是汗颜。做过的题目既然不记得了。后来，面完以后，还带我吃点了零食、拿了瓶茶饮料。这是我见过最nice的印度裔面试官了。虽然她不见得让我过这一轮，但是还是很感谢她。

##  第四轮 印度裔姑娘 framework
她告诉我是under writing team。她让我简单介绍一下自己，然后问了一下framework的问题，我给她画了自己做的项目结构图，主要是MVC的pattern。访问数据库，我说我们可以用sql 还有就是hibernate来做。另外，她还问了我一下Spring mvc的问题。 如果有一个 getReview() 方法，怎么才能区别是get put or post? 我说我在node.js用router来进行选择的。她接着问，如果是java怎么做。我说我把get/ put/ post分成三个controller来做的。 她听我讲的不是想要的答案，主动告诉了我她怎么做的，她说spring 里面可以用@get ("/reviews/{reviewId}") 来处理的。我自作聪明地问，那是不是这些uri要hardcode在代码中。 她回答说是的。 我就讲我们需要维护五个客户，所以不能这么hardcode。 然后讲，我们代码里面有很多冗余。剩下来的时间，就是和她闲聊了片刻。后面一个面试官也到了。

## 第五轮 华裔工程师 design
他让我设计了一个library的services，具体内容一下  

1. Search a book by title  
2. put a book on hold
3. check out a book
4. return a book to dropbox

设计要求：

1. design servcie API
2. think about the user  visit the website , architecture
3. follow up:  if use A and user B want to checkout a book at same time, how do you handle this case?


我在白板上画自己设计思路期间，一边画一边讲，他也在旁边给我反馈。期间，我犯了几个错误，他给我更正了。整个流程还算顺利。   
 
- 他连续问了两次，有rest API 有update这个方法吗？ 我当时真是脑袋没转过来，写了一会儿才发觉自己的错误，说应该是put方法  
- 一开始只准备用book和user两个table，考虑到多个copies，后来想到了增加一个copies。copies表里面需要几个字段，status来表示"hold", "returned", "avaiable"等状态。 另外是否保存user name在copies表，我们两个一开始没达成共识。我觉得需要存这个信息。他后来也同意了。
- 做checkout a book时，我没考虑到book如果已经被某个读者hold的情况。在他提示下给出来了我的思路：如果这本书不是当前读者hold，该读者就不能checkout这本书  
- 两个用户同时checkout的情况，我说用kafka来做，event log里面，这两个用户还是有先后顺序的。还有一个方法就是，让数据库来返回错误。他觉得这个方法不好。我就请问他，他是怎么处理这个问题的，他说可以用hibernate 的transcation来做。这样就可以避免两个用户同时checkout同一本书的问题


面完以后，他让我问问题，我就问了两个问题，接着漂亮的hr 姐姐登场了。

## 第五轮 hr 白人姑娘 很pp
问了一下我期望的薪水，然后问了面试情况，接着就带我在公司兜了一圈。我面试的19楼会议室外面，就是一个吧台，每周有固定时间，给大家喝酒放松的地方。办公环境很好。就是办公室稍微有点空。估计不少人已经下班了。有用windows的也有用Mac电脑的。带我上到20楼，带我进到休息活动室，有各种各样的娱乐器材。另外同样有些零食和饮料。整个氛围都很好。还带我去一个会议室，可以俯瞰三藩市的街景。最后一直从电梯送我到一楼大堂。感觉很有礼貌。就算这家公司不给我offer，也推荐朋友们去尝试一下。

期待着接下来的一个月好运！
