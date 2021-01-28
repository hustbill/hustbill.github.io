---
layout: post
title: "折腾Hexo和Jekyll"
date: 2021-01-24 1:45:00
tags: ["Jekyll", "博客搭建", "Hugo"]
mathjax: true
---

Hexo
=========================

尝试了Hexo，是用Nodejs的 比较容易生成博客，速度快，但是deploy到github pages 需要提交的文件比较多。异步问题

**2021-01-25 更新** 
修改 Deploy 到source branch，这样就不会和当前的master/dev branch产生冲突了。
我的理解是，hexo generate 生成的html和js文件，放在public目录，在.gitignore中忽略public目录，这样产生的文件可以用hexoserver 在local环境运行。 hexo deploy命令则把这些html和js文件 直接deploy到master branch。这样如果我们再修改master branch文件，就需要git pull 命令，把之前hexo deploy文件从 master branch pull下来。这样操作不胜其烦的。

于是，我按照提示，把deploy部分修改如下
```yml
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git
  repo: https://github.com/hustbill/hustbill.github.io.git
  branch: source
  message: "{{ now('YYYY-MM-DD HH:mm:ss') }}"
```

hexo deploy 直接把生成的文件push到source branch，不和现有的master branch 产生冲突。  
需要注意的是， 在Github pages设置setting中，选择source branch和 root / 目录，点击Save按钮  
```
Source
Your GitHub Pages site is currently being built from the source branch. 
[ source ] [ /(root)]  Button Save
```
现在我的博客用Hexo重新设置了： [张华的博客](http://hustbill.github.io/)



Jekyll
==========
参考了hux的jekyll模版
之前有一个小问题， 就是header前面总是多一个 “#” 。我尝试自己解决。但是没弄出来。
索性去hux的github里面，复制了所以的模版文件和html文件。
解决的这个问题。
