---
title: "在Visual-Code中用正则表达式批量替换文件中的日期"
date: 2021-01-29T23:00:33-08:00
draft: false
keywords: []
description: ""
tags: [正则表达式]
categories: 
    - "工具技巧"
---

2016年的日记是在简书里面写的，日记的标题都是带日期的，例如2016-03-30。现在导入Hugo的post以后，在存档页面的list中标题显示日期，就有点太长了，有时候长标题需要换行，显得不美观。于是想把日记里的标题日期都批量删除掉。尝试在VS Code的替换框用正则表达式来批量修改标题中的日期。
<!--more-->

日期字符串“2017-07-04”的正则表达式为：

```
\d{4}-\d{2}-\d{2}
```

先在Java 程序中验证正则表达式是否准确。

```java
public class RegularExpressExample {
    public static void main(String[] args) {
        matchDateString("2017-4-30"); //false
        matchDateString("2017-04-30"); //true
        matchDateString("2017-02-20"); //true
    }

    private static void matchDateString(String string) {
        Pattern pattern = Pattern.compile("(\\d){4}-(\\d){2}-(\\d){2}");
        Matcher matcher = pattern.matcher(string);
        System.out.println(matcher.find());
    }
}
```


然后在VS Code中替换如图所示：

{{% center %}}

![image](/images/tools/vs-code-regular-express-replace.png)

{{% /center %}}

