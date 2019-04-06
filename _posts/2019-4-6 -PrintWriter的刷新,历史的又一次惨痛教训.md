---
layout : post
title : "PrintWriter flush"
date : 2019-4-6 17:35:56 +0800
categories: java
---

今儿跑去写cf的一道交互题，反复提交都容易遇到一个eof错误  
我心想我已经写了
```java
out.flush();
```
搞毛线？  
后来实在搞不清楚，只好换回老法子  
```java
out.printf("");
```
<font color = "RED"> ACCEPTED </font>
