---
title: "Pocket-Gems-OA"
date: "2017-04-26"
draft: false
categories: [面试题]
hiddenFromHomePage: false
---
```
题：

\1. 有向图 找所有start node到end node之间的路径

输入是一个txt 形式如下：

A E

A : B C D

B : C

C : E

D : B

A-> B -> C-> E

A-> C->E

A-> D ->B->C->E

输出一个List 是从A到E所有的path

2.输入一个log file 每一行是一个log 形式如下：

(01/01/2000-01:00:00) :: START

log file有很多行 有这些关键字：START, CONNECTED, DISCONNECTED, END （记得不是很清楚了 貌似其中一两个有出入）
```

需要做的是：读入文件 求用户链接时间占总时间的百分比

所谓的总时间就是START – END 连接时间就是CONNECTED – DISCONNECTED

当然logs中有不止一个CONNECTED – DISCONNECTED的pair 并且末尾有可能出现CONNECTED – END

其实也不难，command line码的甚是不爽，跟单纯的算法题还是有一定的区别 因为先要parse file

不熟悉环境导致第一题用了很久才写出来 第二题没写完