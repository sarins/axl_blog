---
layout: post
category: blog
categories: blog
title: Dubbo服务学习笔记 (Dubbo service framework)
author: Axl Zhao
tags: [Dubbo, RMI, Distribution service, Grid computing]
published: true
sticky: false
---

### Dubbo服务学习笔记 (Dubbo service framework)

#### 1. 分布式远程方法调用(RMI)介绍

##### 1.1. 技术背景

随着这个计算机在各个领域中的应用的不断深入，在用户纬度、数据量纬度、描述深度、广度方面均越来越大，因而从整体计算量上来讲，存在单一主机，垂直结构无法满足大量计算的问题，且问题级别逐渐升级，亟待解决。分布式计算技术将逐渐膨胀升级的问题用分化的方式进行处理，因此在各类大型/大规模项目中分布式计算有着较为广泛的应用。Dubbo就是这个领域中新兴的一种。

- - -

##### 1.2. 远程方法调用(RMI)

以下是常见的几种RMI技术

| RMI/RPC service |
|------------------|
| SOAP web service |
| REST service |
| CORBA(Common Object Request Broker Architecture) |
| Any database |

- - -

##### 1.3. 分布式计算技术

以下是与分布式计算相关的几种概念

| Around distribution calc |
|--------------------------|
| 网格计算 Grid computing |
| 负载均衡 Load blance |
| 失效转移 Failover |
| 数据库切分 |

- - -

#### 2. 远程方法调用(RMI)与I/O的关系

##### 2.1. 远程方法调用(RMI)通用模型

![](/images/dubbo_study/1.jpg)

* 服务器在哪？ 如何找到服务器？
* 请求和回复中包含哪些内容？ 

- - -

##### 2.2. 网络I/O与本地I/O的区别

- - -

#### 3. Dubbo服务开发框架

##### 3.1. Dubbo服务的结构

![](/images/dubbo_study/dubbo-architecture.jpg)

- - -

##### 3.2. 如何使用Dubbo服务

###### 声明与定义（Declare）

本地一般性的Spring服务声明如下：

> **Std loacal:**

```xml
<bean id=“xxxService” class=“com.xxx.XxxServiceImpl” />

<bean id=“xxxAction” class=“com.xxx.XxxAction”>
    <property name=“xxxService” ref=“xxxService” />
</bean>
```

- - -

Dubbo服务在Spring环境中的声明：

> **Provider:**

```xml
<bean id=“xxxService” class=“com.xxx.XxxServiceImpl” /> <!-- 和本地服务一样实现远程服务 -->

<dubbo:service interface=“com.xxx.XxxService” ref=“xxxService” /> <!-- 增加暴露远程服务配置 -->
```

- - -

###### 调用（Invoke）

> **Consumer:**

```xml
<dubbo:reference id=“xxxService” interface=“com.xxx.XxxService” /> <!-- 增加引用远程服务配置 -->

<bean id=“xxxAction” class=“com.xxx.XxxAction”> <!-- 和本地服务一样使用远程服务 -->
    <property name=“xxxService” ref=“xxxService” />
</bean>
```

- - -

###### 调试（Debug）

由于Dubbo服务启动后为独立的java进程，调试需要建立在java远程调试的方式上。

> **启动进程**

将以下启动参数加入被启动的java命令中:

```bash
-Xdebug -Xnoagent -Djava.compiler=NONE -Xrunjdwp:transport=dt_socket,address=8000,server=y,suspend=n
```

> **附着调试**

以Eclipse为例，以下介绍如何完成远程调试，该调试方法适用于大多数java程序的远程调试。

```bash
此处假设被调式进程宿主主机IP为：111.111.111.111, 端口为：8000
```

> **启动Eclipse，打开Debug配置界面，并选择“Remote Java Application”， 然后点击“New”新建一个远程调式配置。**

![](/images/dubbo_study/e_select_debug_rmt_app.png)

> **打开远程调试配置界面，选择“Connect”选项卡，填写基本信息。**

![](/images/dubbo_study/e_type_debug_info.png)

> **选择“Source”选项卡，选配置目源码攫取路径。**

![](/images/dubbo_study/e_select_debug_src.png)

> **选择“Connect”选项卡，查看配置信息并点击“Apply”保存，点击“Debug”启动附着调试（这里假设被调试程序已经于前边步骤启动完毕）**

![](/images/dubbo_study/e_type_debug_info.png)




#### 工具与资源 (Tools & Resources)

>[1] [Alibaba dubbo service framework](https://github.com/alibaba/dubbo)

>[2] [Eclipse](http://www.eclipse.org)

>[3] [Java](http://java.sun.com)

>[4] [Apache maven](http://maven.apache.org)

>[5] [Linux any LSB release](http://kernel.org)

