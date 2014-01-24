---
layout: post
title: "About static_cast"
date: 2012-06-25 14:06
comments: true
categories: [cast, cplusplus, tech] 
---

###static_cast
	static_cast<type> (object);

The static_cast operator can be used for operations such as:

*   Converting a pointer of a base class to a pointer of a derived class,
*   Convert numeric data types such as enums to ints or ints to floats.

###示例
	int score = 1340;

	float scale = static_cast<float>(score) / MAX_SCORE + 1;
	
	// 如果这样呢？会有什么不同
	float scale = score / MAX_SCORE + 1;

需要注意的是，在基础类型转换时，并非进行四舍五入，而是直接舍去小数部分！
