---
layout: post
category: blog
categories: blog
title: Ubuntu创建程序快捷方式
author: Axl Zhao
tags: [linux, Ubuntu, Shortcut]
published: true
sticky: false
---

# Ubuntu创建程序快捷方式

###### 默认的应用程序快捷方式存储在/usr/share/applications/*.desktop

###### 按以下代码建立.desktop文件，并编辑程序启动路径以及参数。

```
[Desktop Entry]
Encoding=UTF-8
# 应用程序显示/查找名称
Name=Violet UML
Comment=Violet UML editor

# 应用程序执行命令行以及参数
Exec=java -jar /opt/devtools/violetUML/violetumleditor-2.0.1.jar

# 应用程序图标
Icon=/usr/share/icons/HighContrast/scalable/emotes/face-cool.svg
Terminal=false
StartupNotify=true
Type=Application

# 应用程序归类属性
Categories=Application;Development;
```