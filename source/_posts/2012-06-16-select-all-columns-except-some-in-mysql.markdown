---
layout: post
title: "Select all columns except some in MySQL"
date: 2012-06-16 13:58
comments: true
categories: [mysql, sql, tech]
author: hahakubile 
---

###问题

如果一个表有多列，要想不查询指定列（其余列都要），该如何实现？

在stackoverflow上有类似的问题，[Select all columns except one in MySQL?](http://stackoverflow.com/questions/9122/select-all-columns-except-one-in-mysql/11060861#11060861)

###实现

	SET @database    = 'database_name';
	SET @tablename   = 'table_name';
	SET @cols2delete = 'col1,col2,col3';

	#If you do have a lots of cols, use this sql to change group_concat_max_len
	SET @@group_concat_max_len = 2048;	
	
	SET @sql = CONCAT(
	'SELECT ', 
	(
	    SELECT GROUP_CONCAT( IF(FIND_IN_SET(COLUMN_NAME, @cols2delete), NULL, COLUMN_NAME ) )
	    FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME = @tablename AND TABLE_SCHEMA = @database
	), 
	' FROM ',
	@tablename);

	SELECT @sql;

	PREPARE stmt1 FROM @sql;
	EXECUTE stmt1;

###说明
涉及到以下内容：

*   从INFORMATION_SCHEMA.COLUMNS表中获取COLUMNS名称
*   GROUP_CONCAT拼接在一起
*   FIND_IN_SET判断是否在排除的列当中
*   IF语句使用
*   Mysql prepare...execute用法
