---
title: "okhttp3 用certificate 和token来访问kubernnetes APIServer"
date: "2017-03-23 14:42:22"
draft: false
categories: [技术笔记]
hiddenFromHomePage: true
---
okhttp3 用certificate 和token来访问kubernnetes APIServer

token 位于 /etc/kubernetes/pki/路径下， token.csv

可以通过curl command来访问
curl -k -v  GET -h "Authorization : Bearer   <token>"    https://apiserver-ip:6443

也可以通过java代码来访问。
client = new httpClient ()
            .header("Authorization", StringCpy(" Bearer :%s", token)
             .builder()

备注：
上面的文字需要订正。
