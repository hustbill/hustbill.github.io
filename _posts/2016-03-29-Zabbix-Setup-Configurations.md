---
layout: post
title: "Zabbix Installation and Configurations"
date: 2016-03-29 14:39:00
categories: jekyll update
---

Note:  
Zabbix is LAMP based monitoring tool, which include sever, client, proxy (for different IDC without public IP). We only use server/client.  

#Installation  
1) zabbix official has its own repository, load the zabbix repo for centos6 first.  
\# rpm -ivh http://repo.zabbix.com/zabbix/2.0/rhel/6/x86_64/zabbix-release-2.0-1.el6.no…

2) install zabbix server and packages needs, it will auto install httpd and some php extensions, also mysql server.  
\# yum install zabbix-server-mysql zabbix-web-mysql

3) start zabbix server  
\# service zabbix-server start  

4) start zabbix client on zabbix-server  
\# service zabbix-client start  

5) load zabbix repo and install zabbix agent on all the servers need to be monitored  
\# yum install zabbix-agent  

6) config each agent server for zabbix-server ip.  
\# vim /etc/zabbix/zabbix_agentd.conf  
<change "Server=127.0.0.1"  to  "Server=127.0.0.1,192.1.199.123" (zabbix_server IP)>  

7) go to webpage config host and add template  
 - create host:  
   Configuration -> Host -> Create host -> fill in the host name, ip address -> Templates -> Add "template os linux", this is the based monitoring  
   
##History
Created by Billy Zhang on Aug 17, 2015 