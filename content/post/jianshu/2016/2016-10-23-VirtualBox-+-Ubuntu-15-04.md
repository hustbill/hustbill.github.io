---
title: "VirtualBox + Ubuntu 15.04"
date: "2016-10-23 01:53:32"
draft: false
categories: [开源学习]
hiddenFromHomePage: true
---
Setup the develop environment for Ubuntu 15.04 on my Mac 

start to use Ubuntu again.

Kubernetes, docker, continuous integration, continuous delivery.


调整ubuntu的 分辨率1920 * 1080  by Hua Zhang  2016.11.02

用VirtualBox虚拟Ubuntu，分辨率只有800×600
首先需要安装 virtualBox package pack 
安装 .vbox-extpack （支持高清显示 1920 *1080）
VirtualBox 5.1.8 Oracle VM VirtualBox Extension Pack  All supported platforms 
https://www.virtualbox.org/wiki/Downloads

VirtualBox extension packages have a .vbox-extpack file name extension. To install an extension, simply double-click on the package file and a Network Operations Manager window will appear, guiding you through the required steps.

To view the extension packs that are currently installed, please start the VirtualBox Manager (see the next section). From the "File" menu, please select "Preferences". In the window that shows up, go to the "Extensions" category which shows you the extensions which are currently installed and allows you to remove a package or add a new one.


第二， 在VirtualBox内启动Ubuntu，启动完毕后，点击Ubuntu顶部的菜单“Device”，选择“Insert Guest Addtions CD Image” 加载到光盘到Ubuntu中
一段构造过程完毕后，重启VirtualBox
