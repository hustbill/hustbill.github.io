---
title: "Find-your-forgotten-join-token-for-kubeadm"
date: "2017-04-26"
draft: false
categories: [技术笔记]
hiddenFromHomePage: true
---
```code
kubectl -n kube-system get secret clusterinfo -o yaml | grep token-map | awk '{print $2}' | base64 -d | sed "s|{||g;s|}||g;s|:|.|g;s/\"//g;" | xargs echo
```

[Reference](http://www.webscalability.com/blog/2016/10/forgotten-lost-your-join-token-for-kubeadm/)
