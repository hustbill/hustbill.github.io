---
title: "2021 02 05 Function_in_bash_profile"
date: 2021-02-05T17:12:42-08:00
draft: false
keywords: []
description: ""
tags: ["bash"]
categories: 
    - "个人笔记"
---



改进了之前的脚本，把writeblog从Alias改成了function，可以接受从命令行传入的文件名，而不是用datetime加post生成一个文件名。

使用方式是``` writeblog 新的博文```

会生成一篇博文 2021-02-06-新的博文.md



更新后的.bash_profile 如下

```bash
export YEAR=`date +%Y`
export DATE=`date +%Y-%m-%d`
export DATETIME=`date +%Y-%m-%d-%H-%M-%S`
export HUGO_BLOG="/Users/zhahua/git/hustbill.github.io"
export CONTENT_PATH="content/post/$YEAR"
export POST_PATH="$HUGO_BLOG/$CONTENT_PATH"
export postname="$DATETIME-post.md"

alias typora="open -a typora"
alias cdblog="cd $HUGO_BLOG"
alias newblog="hugo new $POST_PATH/$postname"
alias typeblog="typora $POST_PATH/$postname"
alias dpblog="cd $HUGO_BLOG && git add . && git commit -m 'add or update the post $DATETIME'  && git push && ./deploy.sh"
alias ll="ls -alth"

function writeblog () {
  post="$DATE-$1.md"
  echo "Blog name: $post"
  cdblog && hugo new $POST_PATH/$post && typora $POST_PATH/$post
  #  && 前面的命令执行成功，才会执行后面的命令
}

```

