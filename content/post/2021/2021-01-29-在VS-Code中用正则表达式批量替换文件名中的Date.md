---
title: "在Visual-Code中用正则表达式批量替换文件名中的日期"
date: 2021-01-29T23:00:33-08:00
draft: false
keywords: []
description: ""
tags: [正则表达式]
categories: 
    - "工具技巧"
---

在Visual-Code中用正则表达式批量替换文件名中的日期。

2017-07-04 正则表达式为：

```
\d{4}-\d{2}-\d{2}
```



在Java 程序中验证正则表达式是否准确。

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



在VS Code中替换如图所示：

{{% center %}}

![image](/images/tools/vs-code-regular-express-replace.png)

{{% /center %}}

