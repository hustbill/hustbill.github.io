---
layout: post
title: "Pluribus Networks onsite interview"
date: 2016-05-17 08:00:00
categories: onsite interview
---

Address:  2455 Faber Place, Suite 100, Palo Alto, CA
办公环境蛮好的，前台华裔姐姐也很好，给我弄了一杯咖啡，还弄了一些糖。很贴心的做法。对公司的好感立马上去了。原定是下午三点开始，我打uber早到了，两点半就到了。

**1-华裔工程师 Jamie Li， 很友好，问题不尖锐**
  主要是elk stack 相关问题，有一个关于elasticsearch 内部文件存放，我回答不好。我居然把elasticsearch的数据存放和 ejabberd弄混淆了
出了一个java 题，我用自己电脑写的，他在旁边看
write a class,   add (1) add(9) add(7) add(6)  => 6 , 7 , 9, 1  without stack

2- 亚裔工程师－Brain
```java
/*给定一个文件，和解析文件的函数parseFile( String Filename)， 返回
List<String, List<String>>  lists， 也就是 <Author,  List<bookName>>
要找出最多的作者名。 我说可以用hashmap<Author, count>来做，然后开始写代码，在返回结果的时候，我居然不记得 set 没有get 操作的。*/

Set<Integer> set = map.keySet();
String  maxAuthor ＝ null; 
for (String key : set) {
  if (map.get(key) > count) {
     count = map.get(key);
     maxAuthor = key;
  }
}
return maxAuthor
```

3- 亚裔工程师, 很资深，让我做下面的题 二选一
1)- print the node numbers of binary tree
2)- hello - > olleo  using recursive