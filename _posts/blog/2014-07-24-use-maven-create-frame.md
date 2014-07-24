---
layout: post
category: blog
categories: blog
title: 使用Maven建立分布式工程骨架
published: true
sticky: false
---

### 使用Maven建立分布式工程骨架

>[下载分布式工程框架 https://github.com/sarins/distributed_service](https://github.com/sarins/distributed_service)

>[Maven参考文档](http://maven.apache.org/archetype/maven-archetype-plugin/examples/create-multi-module-project.html)

- - -

> 1 step: cd current_project_folder

> 2 step: mvn archetype:create-from-project -Darchetype.filteredExtensions=java

> 3 step: cd target/generated-sources/archetype/

> 4 step: mvn install

> 5 step: cd new_project_base_folder

> 6 step: mvn archetype:generate -DarchetypeCatalog=local
  [list local archetypes]
  
> 7 step: choose archetype


