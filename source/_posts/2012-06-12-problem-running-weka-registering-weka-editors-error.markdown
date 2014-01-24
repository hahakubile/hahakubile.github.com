---
layout: post
title: "Problem-Running Weka-Registering Weka Editors Error"
date: 2012-06-12 14:10
comments: true
categories: [weka, problem, tech]
author: hahakubile 
---
###ubuntu下安装weka
	sudo apt-get install weka

###启动weka，控制台打印warning如下：
	---Registering Weka Editors---
	Trying to add JDBC driver: RmiJdbc.RJDriver - Error, not in CLASSPATH?
	Trying to add JDBC driver: jdbc.idbDriver - Error, not in CLASSPATH?
	Trying to add JDBC driver: org.gjt.mm.mysql.Driver - Error, not in CLASSPATH?
	Trying to add JDBC driver: com.mckoi.JDBCDriver - Error, not in CLASSPATH?
	Trying to add JDBC driver: org.hsqldb.jdbcDriver - Error, not in CLASSPATH?

###问题原因
> These are actually just warnings rather than true errors. 
> The system has some default connection strings for various common databases and 
> Weka does a quick check to see if the appropriate JDBC drivers are available to the system at startup. 
> If you are not planning to connect to MySQL, Hypersonic, instantdb etc. then these messages can safely be ignored.

也就是说，这是weka的例行检查，如果不打算连接数据库，完全可以忽略这些warning信息。

###解决办法
*   下载对应的jar包（上面这些都是用于连接不同数据库）
*   修改/usr/bin/weka启动脚本，添加JAVA_CLASSPTH（也可添加在~/.bashrc中）

###参考[1]、[2]、[3]
[1](http://www.cnblogs.com/luffylee/archive/2012/02/23/2365416.html)
[2](http://www.blogjava.net/honeybee/articles/193605.html)
[3](http://forums.pentaho.com/showthread.php?82144-quot-Trying-to-add-database-driver-quot-issue)
