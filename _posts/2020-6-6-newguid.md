---
layout : post
title : "生成GUID Windwos"
date : 2020-6-6 +0800
categories: other
---

太长不读版: 
```PowerShell
New-Guid
# New-Guid []
# Description
# The New-Guid cmdlet creates a random globally unique identifier (GUID). If you need a unique ID in a script, you can create a GUID, as needed.
```

在很久很久以前, 第一次听说Windows里面的GUID, 我也就只是知道这玩意是个全局标识符`(globally unique identifier)`  
其实猜也猜的到, 挺好拼的, 但是查了半天资料没有人告诉我怎么生成这个玩意, 还以为是什么重要的东西, 结果自己瞎写一个, 也能过  
也..行吧  
结果! 我有一天闲的蛋疼, 打开powershell, 输入new-, 然后一直tab, 神tm有个`New-Guid`, 微软你牛逼  
`Get-Help -Online New-Guid`

