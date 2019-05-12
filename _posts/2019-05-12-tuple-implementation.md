---
layout : post
title : "tuple从具体实现到光速劝退"
date : 2019-5-12 00:28:29 +0800
categories: cpp
---

我其实也就比较感兴趣模板不定参是怎么做到的  
在c里面是依赖于`va_list`和同在一个头文件`vadef.h`的一些预定义宏  
  
在 <a href = "https://zh.cppreference.com/w/cpp/utility/tuple">cppreference.com</a> 可以看到，tuple使用了`template<class... Types>`，但是在具体实现中有所不同，先来看VC++的实现  

首先看到的是一个空的tuple，里面放了一大堆空的玩意。
```cpp
template<>
class tuple<> {	// empty tuple
public:
	constexpr tuple() noexcept
		{	// default construct
		}

	constexpr tuple(const tuple&) noexcept	// TRANSITION, for binary compatibility
		{	// copy construct
		}
};
// 删除了容器，Tag，测试代码以及一大堆分离重载和特化
```
关注一开始的几行和注释
```cpp
template<class This, class... Rest>
class tuple<This, Rest...> : private tuple<Rest...> // recursive tuple definition
// 也就是说tuple其实是递归实现的
```
然后是一段长达1000多行的实现，emmmmm  
哦豁劝退



