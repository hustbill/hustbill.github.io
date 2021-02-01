---
title: "influxdb-grafana"
date: "2020-03-03 07:15:23"
draft: false
categories: [DevOps]
hiddenFromHomePage: true
---
在MacBook上启动了InfluxDB 和 Grafana，做监控指标的存储和监控主面板。Grafana的监控模版可以去Grafana官网上去下载所需要的json文件，然后导入到自己的Grafana实例中。需要注意JSON模版对应的Grafana 版本。

```
~ brew services list
Name              Status  User     Plist
grafana           started huazhang /Users/huazhang/Library/LaunchAgents/homebrew.mxcl.grafana.plist
influxdb          started huazhang /Users/huazhang/Library/LaunchAgents/homebrew.mxcl.influxdb.plist
mongodb-community stopped
redis             stopped
telegraf          stopped
~ brew services stop influxdb
Stopping `influxdb`... (might take a while)
==> Successfully stopped `influxdb` (label: homebrew.mxcl.influxdb)
~/git/submit_portal/opera_portal(feature/alert-handling-procedure ✗) brew services stop grafana
Stopping `grafana`... (might take a while)
==> Successfully stopped `grafana` (label: homebrew.mxcl.grafana)
```
