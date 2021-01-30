---
title: "2016-4-08-Paypal onsite 面试记录"
date: "2016-04-09 13:59:48"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
#round1 ： 和善的印度老头、经理

1. soap  vs  REST , follow up , 为什么soap会慢？ 如果rest 也用xml格式，和soap 它还会快吗？
2. 用过spring没， 说一下mvc ， 他让我说出 spring 里面的@Autowired 和 @Qualifier
3. 画了一个uml图， 假定你开发了一个calculator 类，里面有一个方法 addition(int num1, int num2)，编译成一个jar文件供客户调用， 另外，由两个第三方公司分别开发的类Subtraction类  和Multiplication类。 如果你的客户只装载了你的jar ，他想做减法和乘法怎么办？

#round2: 白人大哥，主管
1. 写一个函数判断给定的数是否为2的正整数阶乘
2. 写对应的corner case ， 最好让你写的程序，crash掉，他就比较happy
3. 问题查错分析， 客户端程序 调用 你的第一层函数 svf1（java开发的旧有接口）， 然后svf1 调用 第二层函数svf2，能够正常运行。如果用node.js重新开发了 svf1i，这时候发现客户调用svfi ，svf1i调用svf2，最终程序运行失败了，请你分析一下可能的原因和故障来源。

#round3: 态度超好的华人姐姐
一道简单的javascript，就是给你一张数据表，有三列数据，分别是name，color, count。 你可以用list来存放输入数据
var origArr = [
    {item: 'item1', color: 'RED', count: 10},
    {item: 'item2', color: 'RED', count: 5},
    {item: 'item3', color: 'BLUE', count: 3},
    {item: 'item4', color: 'GREEN', count: 4}
];
*问题*：
  a.  要求按照color 来实现group by。 例如输出是 [{color : ‘red’,  count : 15}, { color: ‘blue’, count :3}]  
  b.  如果输出要加一列 category ，怎么办： 例如
输出是 [{category: ‘A’, color : ‘red’,  count : 15}, {category: ‘B’, color: ‘blue’, count :3}]

#round4: 比较严肃的印度裔经理
因为前面花的时间过多，最后一轮时间不够了，不到三十分钟时间。这个经理一进来，就出了一道题。
给你一个string str = “paypal rockets” ,  要求你按照对角线对称展开，最后输出一个n*n 矩阵。例如：  {{p, y, l, k} ,  {a, a, c, ''},  {p, o, '', ''}, {r, s, '', ''}}， 有点像zigzag展开。

*我最后挂在这题上了。刷题不够！！！*

---- End -----
