---
title: "Win7 VirtualBox5.1 Ubuntu15.0.4 调整屏幕大小"
date: "2016-11-03 06:56:10"
draft: false
categories: [开源学习]
hiddenFromHomePage: true
---
调整ubuntu的 分辨率1920 * 1080  
by Hua Zhang  2016.11.02

在windows7 下用VirtualBox5.1.8 导入Ubuntu虚拟镜像15.0.4，显示的分辨率和窗口大小只有800×600，那么怎么调整为1920 * 1080  尺寸呢？

经过一番搜索，终于按照下面的步骤搞定了。

## 首先安装 virtualBox package pack  来支持1920*1080  
安装[VirtualBox 5.1.8 Oracle VM VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads)

VirtualBox extension packages have a .vbox-extpack file name extension. To install an extension, simply double-click on the package file and a Network Operations Manager window will appear, guiding you through the required steps.

To view the extension packs that are currently installed, please start the VirtualBox Manager (see the next section). From the "File" menu, please select "Preferences". In the window that shows up, go to the "Extensions" category which shows you the extensions which are currently installed and allows you to remove a package or add a new one.


## 第二 在Ubuntu系统中“Insert Guest Addtions CD Image”
 在VirtualBox内启动Ubuntu，启动完毕后，点击Ubuntu顶部的菜单“Device”，选择“Insert Guest Addtions CD Image” 加载到光盘到Ubuntu中
一段构造过程完毕后，重启VirtualBox


![ubuntu-virtualBox-setting.png](/images/开源技术/1647554-dc0da2e44703b635.png)
