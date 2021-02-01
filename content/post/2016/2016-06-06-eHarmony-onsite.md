---
title: "eHarmony onsite"
date: "2016-06-06 01:56:38"
draft: false
categories: [面试题]
hiddenFromHomePage: true
---
五月下旬去了一趟LA 面试。 这家公司位于UCLA附近，内部的氛围很好，出手也很大方，报销来回机票和酒店，餐费也给的足。闲话少叙，直接上题目

## 2D matrix   
几个公司工程师好像对2D matrix 很感兴趣，类似于 leetcode 原题 number of islands的变种，就是将一个2d matrix 里面某个cell从白色改为黑色，相邻的白色也要改变成黑色。

## Map reduce 实现  
另外，一道题是 实现 map reduce方法，并且复用自己的方法来实现其他的方法。 要求边写边用junit run test case

## isPalindrom string with speical characters
给你一个string  :  "You're Welcome emoc lewer ouy"  返回一个boolean

## 设计题如何设计Facebook 朋友圈  
假如你是名人，你有百万级的粉丝，怎么把你消息推送到好友的朋友圈？
建议： 可以分步来做，先push message 或者post 到在线好友，然后把剩余的好友放在一个queue里面，分批次进行更新消息。等下好友在线时，就可以拉取到更新的动态消息



