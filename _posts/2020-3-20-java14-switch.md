---
layout : post
title : "java14 switch 新语法"
date : 2020-3-20 +0800
categories: java
---

java14 前几天发布了, 就是3月17日  
一个比较值得期待的就是`switch`新语法的正式版  
官方doc在[这里](https://docs.oracle.com/javase/specs/jls/se14/html/jls-14.html#jls-14.11)  
想体验的也可以下载[ocaclejdk](https://www.oracle.com/java/technologies/javase-jdk14-downloads.html)或者[openjdk](http://jdk.java.net/14/)玩一玩    
<br>
这个改进对于一向保守的java社区来说还是比较激进的, 当然, java14可能...还要好几年才能正常在工程里面用到  
下面就介绍一下语法吧:  
```
SwitchBlock:
  { SwitchRule {SwitchRule} } 
  { {SwitchBlockStatementGroup} {SwitchLabel :} }

SwitchRule:
  SwitchLabel -> Expression ; 
  SwitchLabel -> Block 
  SwitchLabel -> ThrowStatement

SwitchBlockStatementGroup:
  SwitchLabel : {SwitchLabel :} BlockStatements

SwitchLabel:
  case CaseConstant {, CaseConstant} 
  default

CaseConstant:
  ConditionalExpression
```

首先第一点就是case可以选择的项多了, 就是上面的`CaseConstant`  
可以像这样用逗号连接:

```java
switch (day) {
    ...
    case SATURDAY, SUNDAY :
        System.out.println("It's the weekend!");
        break;
    ...
}
```

顺带一提, 在看doc的时候看到了一个有趣的c hack代码, 是可以正常编译通过的:  
```c
int q = (n+7)/8;
switch (n%8) {
    case 0: do { foo();    // Great C hack, Tom,
    case 7:      foo();    // but it's not valid here.
    case 6:      foo();
    case 5:      foo();
    case 4:      foo();
    case 3:      foo();
    case 2:      foo();
    case 1:      foo();
            } while (--q > 0);
}
```
这个东西叫做`Duff's device`, 有兴趣的可以自行搜索了解一下

然后就是这个`->`了  
大家都知道这玩意就是java里面的`lamdba`的意思  
可以理解为能直接在case后面套一个函数了, 而且还有返回值  
注意两种case类型不能混用  

```java
var k = 1;
var s = switch(k) {
    case 1, 2 -> "abc";
    case 3 -> null;
    // 可以直接返回null值
    //case 4 -> { return "happy 4"; } 
    // 错误, 尝试从 switch表达式返回, 其实这挺蛋疼的, 只能是表达式或者块, 不能是一个真正的函数
    //case 5 -> {}
    // 可以空函数, 但是返回值必须相同
    default -> { throw new RuntimeException(); }
    // 直接抛出错误
}
```
输出是`abc`, 硬性要求返回类型一致, 与普通方法同理 



