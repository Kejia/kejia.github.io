    Title: 在github.io上部署frog博客引擎
    Date: 2015-06-15T22:54:40
    Tags: 教程, racket, frog, 博客

[frog](http://github.com/greghendershott/frog)是基于[racket](http://racket-lang.org/)的博客引擎，本文介绍了如何在[github.io](http://help.github.com/articles/user-organization-and-project-pages/)上部署该博客引擎。

0. 制作用于访问github的ssh密钥

	参考：[配置github密钥](http://help.github.com/articles/generating-ssh-keys/)。

	0. 查看.ssh已有密钥

		```bash
		$ ls -al ~/.ssh
		```
		若使用已有密钥，则忽略下一步。

	0. 制作新ssh密钥

		```bash
		$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
		Enter file in which to save the key (/Users/you/.ssh/id_rsa): [press enter]
		Enter passphrase (empty for no passphrase): [type a passphrase]
		# Enter same passphrase again: [type passphrase again]
		```

	0. 检测ssh-agent是否运行

		```bash
		$ eval "$(ssh-agent -s)"
		# Agent pid 59566
		```

	0. 公钥交由ssh-agent

		```bash
		$ ssh-add ~/.ssh/id_rsa
		```

	0. 复制公钥到剪贴板

		```bash
		$ xclip -sel clip < ~/.ssh/id_rsa.pub
		```

	0. 公钥交由github

		settings > add ssh key

	0. 测试

		```bash
		$ ssh -T git@github.com
		```

0. 设置github用户页

	参考：[github主页指南](http://www.thinkful.com/learn/a-guide-to-using-github-pages/)。

    要使用username.github.io的域名，则需要创建github用户页作业，作业仓库名必须是：username.github.io。

0. 创建frog作业

    参考：[frog指南](http://github.com/greghendershott/frog)。

    0. 克隆github用户页作业

		```bash
		 $ mkdir frog
		 $ cd frog
		 $ git clone https://github.com/username/username.github.io.git
		 ```

    0. 安装frog

		```bash
		$ raco pkg install frog
		$ raco pkg update --update-deps frog
		$ aptitude install python-pygments
		$ aptitude install python3-pygments
		```

	0. 建立作业

		```bash
		$ cd username.github.io
		$ raco frog --init
		```

0. 发布文章

    参考：[frog指南](http://github.com/greghendershott/frog)。

	0. 创建文章

		```bash
		$ raco frog -n "My Post Title"
		```

	0. 编译并预览

		```bash
		$ raco frog -bp
		```

	0. 部署至github

		```bash
		$ raco frog -b
		$ git add .
		$ git commit -m 'post my blog'
		$ git push origin master
		```
