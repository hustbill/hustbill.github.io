---
title: "两个电面Agilent和GenaSys，表现不佳"
date: "2016-04-14 07:54:09"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
## 10:32－10: 56 AM  Agilent , Roci, software development manager
c# /Java 开发职位  

先是Steven给我电话，然后切换到roci，他迟到了三分钟。然后问了一些问题。他现在手下有两个team： 
- 第一个team 主要是做c# , 主要是维护以前的老代码，例如User Management ，Report UI；
- 第二个team 是负责第三方的API和需求开发，利用新的技术，新的infrastructure来满足第三方的需求。

他明显对C#比较感兴趣。我因为好久不用C#写程序，有点手生，也心虚，所以讲了不少java的东西。最后让我选职位，我告诉他还是做java的职位。

他让我问他问题，我随后问了他三个问题：
1. 你们team现在多少人，工程师各自负责什么职能？
2. 你们开发模型是什么样的？ TDD， Agile？
3. 你们team现在最大的challenge 是什么？  

他说主要是客户需求没能得到较快地满足。例如，如何用新技术来满足客户需求，比如用nosql database, elasticsearch 等等来更新就有的系统，达到并且超过旧有系统的性能，从而更好地服务客户。

## 4:00-4:15 PM GenapSys, Sambit Basu, VP Software Engineering
他是个很有资历的老印，完全没口音。他打电话来的时候，我还在用Java和Spring写程序。把面试时间记错了，这是我对他的不尊重。我仓促之中拔掉手机充电线，然后用耳机接了电话。寒暄两下，步入正题。他问了几个问题：
 1. 你当前在做啥工作，还有你想从事什么样的工作 ？ 这是你更换工作的原因吗？
 2. 用过Cloud software 没有？  我说用过AWS。 他接着问用了哪些AWS的第三方工具， 我提到了EC2。 他继续追问，具体是什么第三方工具？ 我被逼急了，只好直接Google ，混乱中报了几个第三方开源工具名字给他
 3. 你做过Java MultiThread 编程没？ 我给他说我用过concurrency 库 。他又继续追问用过什么方法？我有点抓瞎了。只好改口说，我后来用过Actor model和AKKA Toolkit，也可以做Multi threading 和message passing 多线程编程的。 
 他也就没继续问了， 感觉对我不是很有兴趣了。

结束以后，我问了他三个问题，
1. 他们现在有多少人，有多少是做后端的。
2. 监控工具是怎样的，他说 他们用aws自己的监控工具。
3. 另外，开发的模型是什么样的。 他说现在是agile development。以后要采用TDD

另外，我听出来他有挂我的意思。 我急切地告诉他，希望他给我一个机会，我可以在电话面试中展现自己的能力和coding skills。 不管怎样。能有technical phone interview 机会总是好的。

## 总结
1. 应该做好充分准备，至少在电话五分钟前ready。直接告诉他，i am ready for the interview
2. 概念性的问题一定要准备好。 否则第一关都过不去
3. 因为不清楚职位要求 可能猎头给过我，可能猎头只是在电话里面说过了。我隐约记得是做后端的。 等他告诉我职位是后端Pipeline的时候，已经有点晚了。下次要厚着脸皮问猎头，具体是啥职位，有啥要求。
4. 还是要用录像和录音的方式，训练自己的口语。讲得流利和清晰才可以。做题和表达同样重要。

## 参考
- [Amazon-Web-Services-AWS](http://whatis.techtarget.com/definition/Amazon-Web-Services-AWS)
- [EC2 instance managing tools](http://searchaws.techtarget.com/definition/Amazon-Elastic-Compute-Cloud-Amazon-EC2) Front-end management panel
- [CloudWatch for monitoring](http://searchaws.techtarget.com/answer/What-Amazon-CloudWatch-Logs-can-and-cant-do)
- [AWS Elastic Beanstalk](http://searchcloudcomputing.techtarget.com/photostory/2240174129/Snapshots-of-AWS-reInvent-2012/10/Amazon-Web-Services-Elastic-Beanstalk-feeds-into-enterprise-development-fears) for deploying and scaling Web applications and services
- [AWS CloudFormation](http://searchaws.techtarget.com/tip/How-AWS-CloudFormation-helps-streamline-cloud-resources) for creating a collection of related AWS resources and provisioning them
- [AWS Data Pipeline](http://searchaws.techtarget.com/tip/Manage-cloud-workflows-with-AWS-Data-Pipeline) for processing and moving data between different AWS compute and storage services and on-premises data sources
