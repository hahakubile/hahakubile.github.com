---
layout: post
title: "Problem-SSH Permissions denied: This private key are too open"
date: 2012-06-11 10:32
comments: true
categories: [tech, github, id_rsa, problem]
author: hahakubile 
---

###问题:
	$ ssh -T git@github.com     
	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	Permissions 0766 for '***/.ssh/id_rsa' are too open.
	It is recommended that your private key files are NOT accessible by others.
	This private key will be ignored.
	bad permissions: ignore key: ***/.ssh/id_rsa
	Permission denied (publickey).

###解决方法:
	cd ~/.ssh
	chmod 700 id_rsa

###参考：[1]、[2]
[1]: http://stackoverflow.com/questions/1556119/ssh-private-key-permissions-using-git-gui-or-ssh-keygen-are-too-open ""
[2]: http://www.thinkplexx.com/learn/howto/security/ssh/fix-permissions-are-too-open-private-key-will-be-ignored ""
