---
layout: post
title: "problem-printf std string"
date: 2012-06-29 11:14
comments: true
categories: [cpluscplus, tech, problem] 
---

###问题

{% codeblock lang:c++ %}
#include <stdio.h>
#include <string>

using namespace std;

int main() {
   string a = "test";
   printf("%s/n", a);
}
{% endcodeblock %}

###编译错误
*    warning: cannot pass objects of non-POD type ‘struct std::string’ through ‘...’; callcall will abort at runtime
*    warning: format ‘%s’ expects type ‘char*’, but argument 2 has type ‘int’

###原因
*    printf只能输出C语言内置的数据，而string不是内置的，只是一个扩展的类
*    &a代表的是这个字符串的存储地址，并不是指向字符串的首地址

###解决
	printf("%s\n", a.c_str());

*   const char *c_str();
*   c_str()提供了这样一种方法，它返回const char*类型(可读不可改)的指向字符数组的指针
