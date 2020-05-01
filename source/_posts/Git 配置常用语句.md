---
title: Git 配置常用语句
date: 2019-03-05 02:39:17
tags: [Git]
categories: [Git]
---

------------------------------

git add ., git add -u, git add -A 区别

·  git add -A  提交所有变化

·  git add -u  提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)

·  git add .  提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件

------------------------------

新建分支
$ git branch newbranch  

检查分支
$ git branch 

切换分支
$ git checkout newbranch

更新至新分支
$ git add . 
$ git commit -m "18.03.01"

检查分支状态
$ git status

切换至主分支
$ git checkout master 

合并至主分支
$ git merge newbranch  

提交代码
$ git push -u origin master

删除分支
$ git branch -D newbranch

-------------------------------

删除远程仓库
$ git remote rm origin

添加远程仓库
$ git remote add origin git@github.com:FBing/java-code-generator

-------------------------------

配置 Git user [name/email]：
$ git config --global user.name "xuhaiyan"
$ git config --global user.email "haiyan.xu.vip@gmail.com"

$ git config user.name "Your Name Here"
$ git config user.email "your@email.com"

-------------------------------

生成SSH密钥
$ ssh-keygen -t rsa -C “可选,这里标注密钥使用指向” ### 生成两个文件，id_rsa和id_rsa.pub(这里是我们需要的密钥)，将密钥添加到对应的Git服务，例如：GitHub，GitEE...

添加SSH密钥
$ ssh-add 文件名

提示无法打开身份验证 Could not open a connection to your authentication agent.
ssh-agent bash

测试SSH密钥
$ ssh -T git@github.com

--------------------------------

推送代码至服务器
$ git push origin master

服务器代码下载至本地
$ git pull origin master

--------------------------------

Git忽略规则：
	
	在git中如果想忽略掉某个文件，不让这个文件提交到版本库中，可以使用修改根目录中 .gitignore 文件的方法（如果没有这个文件，则需自己手工建立此文件）。这个文件每一行保存了一个匹配的规则例如：

	# 此为注释 – 将被 Git 忽略

	*.sample 　　 # 忽略所有 .sample 结尾的文件
	!lib.sample 　　 # 但 lib.sample 除外
	/TODO 　　 # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
	build/ 　　 # 忽略 build/ 目录下的所有文件
	doc/*.txt 　　# 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt

　　.gitignore规则不生效的解决办法

	把某些目录或文件加入忽略规则，按照上述方法定义后发现并未生效，原因是.gitignore只能忽略那些原来没有被追踪的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。那么解决方法就是先把本地缓存删除（改变成未被追踪状态），然后再提交：

	git rm -r --cached .
	git add .
	git commit -m 'update .gitignore'

--------------------------------

git rollback -- 放弃本地修改

	1.未使用 git add 缓存代码时。
		可以使用 git checkout -- filepathname (比如： git checkout -- readme.md  ，不要忘记中间的 “--” ，不写就成了检出分支了！！)。放弃所有的文件修改可以使用 git checkout .  命令
		相当于 git add 命令，对于新创建文件手动删除即可，因为它不在git管理系统中
	
	2.已经使用了 git add 缓存了代码。
		可以使用  git reset HEAD filepathname （比如： git reset HEAD readme.md）来放弃指定文件的缓存，放弃所以的缓存可以使用 git reset HEAD . 命令。
		此命令用来清除 git 对于文件修改的缓存。相当于撤销 git add 命令所在的工作；本地的修改并不会消失，只是回到了状态(一)继续智行状态(一)的操作即可
		
	3.已经用 git commit  提交了代码。
		可以使用 git reset --hard HEAD^ 来回退到上一次commit的状态。此命令可以用来回退到任意版本：git reset --hard  commitid 
		可以使用 git log 命令来查看git的提交历史。git log 的输出如下,之一这里可以看到第一行就是 commitid：
		commit cf0d692e982d8e372a07aaa6901c395eec73e356 (这里就是commitid)

--------------------------------

## [解决Windows下git需要每次都要ssh-add的问题](https://blog.csdn.net/xianhenyuan/article/details/92397894)
``` bash
git\etc\bash.bashrc
# ssh-add
eval "$(ssh-agent -s)"
ssh-add ~/sshKey文件名 可添加多个
```

## 更新.gitignore后忽略不起作用的解决办法
>进入项目目录，先把本地缓存删除，然后再提交。
git rm -r --cached . //删除所有文件缓存
git add . //本地添加
git commit -m '这里写提交日志' //本地提交
删除指定文件目录的缓存,比如说根目录下有log目录:
git rm --cached log/

## git 重新输入账号密码
` git config --system --unset credential.helper `

## Git 新增子模块
`git submodule add 子模块Git地址 子模块路径`

`例：git submodule add https://github.com/AJiu-Blog/Ajiu-Blog.github.io.git publicSrc`

## 更新 git 子模块为最新提交版本
`git submodule update --remote --merge`

