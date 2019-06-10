---
layout : post
title : "cpp预处理器自定义名称pair工厂"
date : 2019-6-10 14:18:21 +0800
categories: cpp
---

<font color = "green">updata at 2019-6-10</font>

平时看着`first`和`second`烦<del>(其实是闲着蛋疼)</del>弄了这么个玩意， 挺简单的， 注意后面没有加分号（因为看起来比较舒服 <del>但是在vs会被报无函数定义</del>  
支持`pair`拷贝只是因为比较方便  
如果觉得加`<typename, typename>`麻烦的话， 就把模板去掉， 宏参数加上`Type1`和`Type2`, 下面拷贝函数返回值去掉`<...>`即可
想要别名还是自行 `typedef`  
或者加一个别名，然后在下面typedef
```cpp
// or MAKE_NODE(name, Type1, c1_name, Type2, c2_name)
#define MAKE_NODE(name, c1_name, c2_name) template<class Type1, class Type2> \
struct name { \
    Type1 c1_name; Type2 c2_name; \
    name() : c1_name(), c2_name() {} \
    name(const Type1 & c1, const Type2 & c2) : c1_name(c1), c2_name(c2) {} \
    name<Type1, Type2> & operator=(const name<Type1, Type2> & right_c) { \
        c1_name = right_c.c1_name; \
        c2_name = right_c.c2_name; \
        return (*this); \
    } \
    name<Type1, Type2> & operator=(const pair<Type1, Type2> & p) { \
        c1_name = p.first; \
        c2_name = p.second; \
        return (*this); \
    } \
    operator pair<Type1, Type2>() { return make_pair(Type1(c1_name), Type2(c2_name)); }
}
MAKE_NODE(P, x, y);
#undef MAKE_NODE
int main() {
    P<int, int> test1(1, 2);
    cout << test1.x << " " << test1.y << endl;
    return 0;
}
// output :
// 1 2
```