---
layout : post
title : "Java命令行工具使用utf-8编码的方法"
date :  2020-3-15 00:00:00 +0800
categories: java
---

## 起因

前端系统换成了utf-8编码, java命令行工具变成了一坨耙耙

## 解决方法

加一个系统全局变量 `JAVA_TOOL_OPTIONS`  
值是 `-Dfile.encoding=UTF-8`  

完  
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
找到的博客里面看半天没找到关键点的文档  
https://docs.oracle.com/en/java/javase/13/docs/specs/jvmti.html#tooloptions

