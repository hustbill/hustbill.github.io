---
layout:	post
title:	"优化Hexo Theme Pure 正文字体CSS写法 "
date:	2015-04-11 11:49:00
categories: jekyll update
---

[Hexo theme pure](https://github.com/cofess/hexo-theme-pure) 主题很棒，符合我的大部分需求。美中不足的是字体设置有些偏小，字间距有些紧凑。  

为了优化阅读体验，重新设置了CSS 中的 font-family、字体大小、颜色、行距，让文字看起来更美观。参考这篇文章-[优化阅读体验，网站预设字体的CSS最佳写法](https://www.shejidaren.com/the-best-css-font-in-web-design.html)

```CSS
.main .content {
    /* min-height: 85vh; */
    
    /* Ref: https://www.shejidaren.com/the-best-css-font-in-web-design.html */
    /*  字体  */
    font-family: -apple-system, BlinkMacSystemFont, 'Microsoft YaHei', sans-serif;
  
    /*  字号 */
    font-size: 16px;
    
    /*  字体颜色  */
    color: #333;
    
    /* 行距 */
    line-height: 1.75em;
}

```