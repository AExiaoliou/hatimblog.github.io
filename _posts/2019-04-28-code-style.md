---
layout : post
title : "code style"
date : 2019-4-28 23:06:26 +0800
categories: post
---

## rouge
`rouge`  

## c/cpp
```cpp
#include <bits/stdc++.h>
#include "code.h"

#define ture true

using std::cin;
using namespace std;

const int const_val = -1234567;
int n;

template<typename T> 
inline T const& func (T * a, T & b) {
    //empty func
}
/*
* who is C?
*/
class TestClass {
    static long long static_val = 0;
    int a, b;
    int * arr;
    void __fool_code___style() const {}
    friend TestClass * sayABC(const & TestClass);
    TestClass() = default;
    TestClass(int arg1, int arg2) : a(arg1), b(arg2) {
        arr = new int[n];
    }
    ~TestClass() {
        for (int i = 0; i < n; i++) delete [] arr[i];
        delete [] arr;
    }
};
int main(int argc, char* arg[]) {
    cin >> n;
    cout << "abc" << endl;
    vector<short> vec(3);
    for (auto & i : vec) { i = 0x3f3f3f3f; }
    sort(vec.start(), vec.end(), greater<short>());
    if (1) if (0) cout << "???";
    while (ture) {
        noodle:
        TestClass _1_2(1, 2);
        _1_2.sayABC();
        break;
    }
    goto noodle;
    return 0;
}

error co
    de int / here ? :

namespace what_happened {
    int c;
    namespace where_are_we_from {
        #if __cplusplus >= 0
        string now(char *ctime(const time_t *time));
        #endif
    }
}
```

## JAVA
```java
import static java.lang.System.out;
import java.util.*;
import java.io.*;

error co
    de int / here ? :

public class Main {
    public static void main(String[] args) {
        out.printf("%d\n", 3);
    }
}
class TestClass {
    class A {
        int a;
        public A(int a) {
            this.a = a;
        }
    }
    static class B {
        int b, c;
    }
    static <T extends Comparable<? super T>> T mins(T.. e) {
        T minT = e[0];
        for (int i = 1; i < e.length; i++) minT = minT.comparaTo(e[i]) < 0 ? minT : e[i];
        return minT;
    } 
}
```