---
title: "如何用Hugo命令生成新Post，Typora编写，自动提交与部署"
date: 2021-01-27T15:43:22-08:00
draft: false
keywords: []
description: ""
tags: 
  - "Hugo"
  - "Bash"
  - "Typora"
categories: 
  - "个人笔记"
---

撰写新的文章需要几个步骤：

1. 用Hugo 命令生成新的文章，hugo new content/post/blog_2021/2021-01-27-new-post.md
2. 打开Typora Markdown编辑工具编辑这个文章
3. 编写完毕以后，保存并提交这个文章到 hustbill.github.io repo的master branch，需要用Git 命令：git add. && git commit -m "add post ..."
4. 用depoly.sh 来提交到source branch。

为了节省时间，尝试把这四个步骤用bash alias命令串联起来，最后用一个writeblog命令就能完成1和2步骤，用另外一个命令完成步骤3和4。

以后每次写作，就只需要打开Mac Termial，敲入writeblog后，就能跳入Typora界面愉快的写作。写完以后，用deployblog提交并且自动部署到GitHub Pages。

修改了MacBook的.bash_profile，具体操作如下：


- 添加了cdblog命令， 进入到hugo-blog目录

- 添加了newblog命令，自动生成新的文章。文章的命名是用日期加时间，例如 2021-01-27-15-40-26-post.md

- 添加了typeblog命令 ，打开Typora来编辑新生成的文章

- 用writeblog命令把上述三个命令串联起来执行：``` cdblog && newblog && typeblog```。编辑时，可添加标签Tags或分类Categories

- 用deployblog命令包含了步骤3 和步骤4： 


  - 先提交2021-01-27-15-40-26-post.md 到master branch；
  - 再用deploy.sh 来提交public文件夹中的静态html文件到source branch。

  请记住，在hustbill.github.io repo的setting中，需要把Github Pages绑定到 source branch。这样source branch的文件就部署到Github Pages上。‘’Your GitHub Pages site is currently being built from the `source` branch.‘

*Note*

​	如何需要再次修改同一个文章，只需要在同一个terminal，敲入tyeblog 即可打开刚刚保存的文章。

  

```bash
#.bash_profle

export YEAR=`date +%Y`
export USER=`id -un`
export DATETIME=`date +%Y-%m-%d-%H-%M-%S`
export HUGO_BLOG="/Users/$USER/git/hustbill.github.io/"
export CONTENT_PATH="content/post/$YEAR"
export POST_PATH="$HUGO_BLOG/$CONTENT_PATH"
export POST_NAME="$DATETIME-post.md"

alias typora="open -a typora"
alias cdblog="cd $HUGO_BLOG"
alias newblog="hugo new $POST_PATH/$POST_NAME"
alias typeblog="typora $POST_PATH/$POST_NAME"
alias writeblog="cdblog && newblog && typeblog"  #  && 前面的命令执行成功，才会执行后面的命令
# Deploy to Github Pages
alias dpblog="cd $HUGO_BLOG && hugo -D && git add . && git commit -m 'add a new post $POST_NAME' && git push && ./deploy.sh"
alias gitpush="cd $HUGO_BLOG && hugo -D && git add . && git commit -m 'add a new post $POST_NAME' && git push"

```
## 更新记录
- 2021-01-30 更新了blog中的目录名称，添加了本地图片


祝好！

Hua



