---
layout: post
title: "Avoid assigning negative numbers to unsigned int|short"
date: 2012-06-25 11:57
comments: true
categories: [cplusplus, tech] 
---

###问题
	// 定义了一个int变量i，i存在为负数的情况
	int i = -1; 
	// 又定义了一个unsigned short or int的变量j
	unsigned short j;
	// 如果把i的值赋给j
	j = i; 

	// 会发生什么？j为65535
	std::cout << j << std::endl;

###结论

这是一个简单的赋值，但由于前后未注意，导致这种bug发生，试想如果后面使用下面语句进行判断的话：
	if(j > 0) {
	  // 这里，j本应该是-1，但由于65535>0，导致错误
	}

看到一句很有意思的话，You're lying to the compiler.



