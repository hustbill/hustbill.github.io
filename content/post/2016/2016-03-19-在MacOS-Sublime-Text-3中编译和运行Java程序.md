---
title: "在MacOS Sublime Text 3中编译和运行Java程序"
date: "2016-03-19 09:09:36"
draft: false
categories: [日记本]
hiddenFromHomePage: true
---
修改JavaC.sublime-build 或者创建新的编译系统－Java.sublime-build
<pre><code>/Users/$username/Library/Application Support/Sublime Text 3/Packages/Java/JavaC.sublime-build   </code>

为：

`
{
     "cmd": ["javac \"$file\" && java \"$file_base_name\""],
    "shell":true,
    "file_regex": "^(...*?):([0-9]*):?([0-9]*)",
    "selector": "source.java"
}
`
