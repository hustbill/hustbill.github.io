---
title: "thumbtack 面试经验"
date: "2016-02-25 08:47:39"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
面经一：
一共经过了三轮面试

1. Online code challenge :  实现一个in-memory数据库 上交之后会有人review code 大概3-5天后收到phon-screen通知. visit 1point3acres.com for more.

2. Phone screen : 和一般公司的phone screen没什么区别 问了valid sudoku 面完当天就收到消息让安排onsite

3. Onsite： 一共5轮 再加上跟co-founder聊了半小时 本来是要和CEO聊的 CEO临时开会 就和co-founder聊了聊 小哥是学政治了 很有意思

1 ) Manager : behavior question. 小公司比较注重culture fit 面试前大家多了解下公司背景. from: 1point3acres.com/bbs

2 ) 拓扑图找cycle

3 ) Serialize/deserialize binary tree

4 ) 给大量文件和一个搜索的query 用数学方法计算相关函数 返回相关率最高的10个文件

5 ) 设计一个statistic class 要求支持：add, getMean 和 getMedian 操作

面经二：
楼主cs ms毕业，工作一年骑驴找马中，拿到了thumbtack和uber的onsite，因为这两个厂的面经较少，这里来说说这两家的面试情况。

thumbtack:

这里要先感谢W大的引荐，然后我顺利拿到了thumbtack面试。

第一轮：code challenge

第二轮:电面，一个在thubmtack工作了三年的人面我的，题目简单，leetcode常见题型，说了说时间复杂度之类的后面试官就让我问问题。这里值得一提的是在codepair上写要能run,好像现在startup都是这种风格.

onsite:

我是周四下午电面的，周一拿到onsite.thumbtack onsite是我面过所有公司中时间最长的，但是也挺欢乐的体验。公司从外面看很不起眼，感觉破破烂烂的，进去后发现里面的装修别具一格，有fb的感觉。公司现在还不算大，总共才有30几个engineer.

onsite从上午10点半到下午4点半结束，有三轮coding，一轮systemdesign，一轮cultral fit,中间有跟ceo & co-founder一起吃饭。

第一轮和第二轮是coding,算法题很简单,都是常见题型.第一轮需要在电脑上coding(最好能run). 第二轮是直接白板. 这里值得一说的是这两轮的题目都不是原题,第二轮的面试官跟我说第一轮和他这轮的题目都是从他们实际工作中遇到的问题抽象提取出来的.这点还挺有意思的.

接下来跟ceo吃饭，问了我些behaivor问题，例如why thumbtack, what's ur passion等等, 我也问了些ceo的问题，聊的挺开心。

第三轮: vp cultralfit，vp刚从gg跳过来三个月，之前是gg的senior director，我们就聊了聊我现在的proj，遇到哪些问题我怎么解决的，然后聊了聊thumbtack的tech stack他们遇到什么问题之类，这轮聊的也挺开心。

第四轮：coding，两个面试官,一个主面一个感觉像是shallow, 比较有意思的是那个shallow的居然是HM. 主面官上来问了我很ML的问题，对我ML的proj很感兴趣, 后来居说这个面试官对ML一点不懂, 估计他就是纯粹感兴趣吧, 当然楼主我也ML的小学生,不知道他有没有懂我说的.然后他让我写一个很简单的算法题,leetcode 中等偏下的难度.我首先跟面试官司讨论了下题目的意思然后例了些examples,然后说了说解题的思路,面试官说思路是对的然后就让我写,写完后我解释了下我的代码,主面官说it works, 这个时候shallow的HM表示好像没怎么看懂, 我就稍微解释了下,然后他点了点头说make sense, 我当时其实并没有意识到这个shallow的原来是HM,我以为他是一个小兵,也就有些怠慢他没有进一步解释.然后就开始聊了聊他们工作的事情.

第五轮：systemdesign, design一个跟twitter差不多的类型的app。这一轮可能是我面的最出彩的一轮，我先上最经典的3tier架构,然后我自己不断的分析指出哪里会是瓶颈，如何优化，然后最后面试的小哥说我们thumbtack就是用这种模式，但是twitter可能会用更复杂点的架构，然后我们一起讨论，他也propose了一些idea，我们一起探讨最后弄出了一个完整的他满意的design。

面完system design就是安排跟hr聊天。HR很nice的送了我些纪念品文化衫，带我去天台看了看风景，然后我被送出了公司。

总结：thumbtack这家公司给我的感觉比较朝气蓬勃，人都很年轻，也很聪明，每个人都很nice，很有礼貌，我的所有面试中体验排第一。公司很土豪，刚融资了一个亿，office里全是27寸mac显示器。他们有一个chef在office做饭，很赞。公司ceo很有趣，人也很nice。我个人比较喜欢thumbtack，而且比较看好他们的前景。我个人也觉得面的挺不错,有些开始期待offer了. 不过最终拿到了人生中最长的一封拒信,hr的feedback写的很详细也很真诚,大概意思是说很多人给了我strong,也有人给了no hire,他们debreif了好几次最终还是把我给拒了. 给我no hire的似乎有一个是hm,他的feedback是coding还行,但是comunication不好,所以给no hire. 我想可能是他那面我没有对他很认真的解释他没明白的地方吧.还是挺遗憾的,挺好的机会.

转自一亩三分地
