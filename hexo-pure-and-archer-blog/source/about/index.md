---
title: about
date: 2021-01-25 12:16:43
layout: about
description: "Hey, this is Hua."
---
这是我的自我描述，待完成，谢谢！🙏

```html
<!-- Language Selector -->
<select onchange= "onLanChange(this.options[this.options.selectedIndex].value)">
    <option value="0" selected> 中文 Chinese </option>
    <option value="1"> 英文 English </option>
</select>

<!-- Chinese Version -->
<div class="zh post-container">

    <!--copied from markdown -->
    <blockquote><p>写写代码，读读书。<br>
    世界那么大，我想去看看。</p></blockquote>

    <p>Hey，我是<strong>张华</strong>，程序员 &amp; 写作者，<a href="http://www.hust.edu.cn/">华中科技大学</a> · 软件工程 2005 级；前阿尔卡特 · <a href="http://www.diebold.com/">迪堡</a>软件团队工程师；
    目前任职于Visa · 硅谷 ，负责<a href="http://hustbill.github.io">基础设施监控与告警平台</a>。</p>

    <p>一些作品和开源项目，👉 戳 <a href="/portfolio">Portfolio</a> 与 <a href="http://github.com/hustbill">Github</a></p>

    <!-- <h5>Talks</h5>

    <ul>
    <li><a href="http://huangxuan.me/2015/12/28/css-sucks-2015/">CSS Still Sucks 2015 · 2015</a></li>
    <li><a href="http://huangxuan.me/2015/07/09/js-module-7day/">JavaScript 模块化七日谈 · 2015</a></li>
    </ul>
 -->

    <h5>Resumes</h5>

    <ul>
        <li><a href="/attach/2019_10_21_Hua_Zhang_gg_resume.pdf">2019_Hua_en_SDE</a></li>
    <!-- <li><a href="/attach/2016_Hua_en_SE.pdf">2016_Hua_en_SE &amp; FE</a></li> -->
    <!-- <li><a href="attach/2016_Hua_en_PD.pdf">2016_Hua_en_PD &amp; UX</a></li> -->
    </ul>

</div>

<!-- English Version -->
<div class="en post-container">
    <blockquote><p>Yet another Frontend Engineer. <br>
    Yet another Lifelong Designer.</p></blockquote>

    <p>My name is <strong>Zhang Hua(张华)</strong>，you can call me nickname <strong>Bill</strong>. I studied Comptuer Science in <a href="http://www.wsu.edu">Washington State University</a>, parallel computing and distributed systems.</p>

    <p>As a engineer, I work at AboveGEM (<a href="http://www.abovegem.com">in CrunchBase</a>) as the dev lead of Back-End Infrastructure Team currently.</p>

    <p>As an open source developer, I am experienced in ElasticSearch, Logstash and Kibana, and familer with Splunk and Nagios.</p>

    <p>Some of my projects is put on my <a href="/portfolio">Portfolio 👉</a> and <a href="http://github.com/hustbill">Github 👉</a>.</p>

    <!-- <h5>Talks</h5>

    <ul>
    <li><a href="http://huangxuan.me/2015/12/28/css-sucks-2015/">CSS Still Sucks 2015 · 2015</a></li>
    <li><a href="http://huangxuan.me/2015/07/09/js-module-7day/">JavaScript Modularization Journey · 2015</a></li>
    </ul> -->


    <h5>Resumes</h5>

    <ul>
    <li><a href="/attach/2019_10_21_Hua_Zhang_gg_resume.pdf">2019_Hua_en_SDE</a></li>
    <!-- <li><a href="attach/2016_Hua_en_PD.pdf">2016_Hua_en_PD &amp; UX</a></li> -->
    </ul>
</div>

<!-- Handle Language Change -->
<script type="text/javascript">
    // get nodes
    var $zh = document.querySelector(".zh");
    var $en = document.querySelector(".en");
    var $select = document.querySelector("select");

    // bind hashchange event
    window.addEventListener('hashchange', _render);

    // handle render
    function _render(){
        var _hash = window.location.hash;
        // en
        if(_hash == "#en"){
            $select.selectedIndex = 1;
            $en.style.display = "block";
            $zh.style.display = "none";
        // zh by default
        }else{
            // not trigger onChange, otherwise cause a loop call.
            $select.selectedIndex = 0;
            $zh.style.display = "block";
            $en.style.display = "none";
        }
    }

    // handle select change
    function onLanChange(index){
        if(index == 0){
            window.location.hash = "#zh"
        }else{
            window.location.hash = "#en"
        }
    }

    // init
    _render();
</script>

{% if site.disqus_username %}
<!-- disqus 评论框 start -->
<div class="comment">
    <div id="disqus_thread" class="disqus-thread">

    </div>
</div>
<!-- disqus 评论框 end -->

<!-- disqus 公共JS代码 start (一个网页只需插入一次) -->
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES * * */
    var disqus_shortname = "{{site.disqus_username}}";
    var disqus_identifier = "{{site.disqus_username}}/{{page.url}}";
    var disqus_url = "{{site.url}}{{page.url}}";

    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<!-- disqus 公共JS代码 end -->
{% endif %}

```