---
title: Hexo 安装部署配置详解
date: 2018-07-25 02:39:17
tags: [Hexo]
categories: [Hexo]
---

# hexo API 一站安装
https://blog.csdn.net/erchowyo/article/details/54407601

# 安装 hexo
$ npm install -g hexo
# 初始化 hexo
$ hexo init
# 安装 hexo 依赖
$ npm install
# 生成 hexo 资源
$ hexo generate
# hexo 服务
$ hexo server 

# hiker: hexo-theme API
https://github.com/iTimeTraveler/hexo-theme-hiker

# 创建SSH密钥
ssh-keygen -t rsa -C "adcc_ajiu_2013qc@163.com"
# 开启 ssh-add
eval `ssh-agent -s`
# 添加密钥
ssh-add github

#
ssh-keygen -t rsa -C "adcc_ajiu_2013qc@163.com"
#
eval `ssh-agent -s`
#
ssh-add github
#
git remote add origin git@github.com:AJiu-Blog/Ajiu-Blog.github.io.git
# 安装 全局 Hexo
npm install -g hexo
# 初始化 Hexo
hexo init
# 安装更新
npm install hexo --save
# 安装 Hexo Server
npm install hexo-server
# 运行 Hexo 服务
hexo s / hexo server
# 安装 Hexo 提交方式为 Git
npm install hexo-deployer-git --save

# Hexo 环境配置

	1.手动初始化 Hexo init
 
	2.覆盖 public，source，tag_config，themes，_config.yml 文件/夹
	
	2.使用搜索功能前必须在Hexo目录下使用以下命令安装 hexo-generator-json-content 插件.

		npm install -S hexo-generator-json-content
		
# Hexo 常用语句
 
	创建文件
	$ hexo new [layout] <title>

	创建文件
	$ hexo new page [layout] <title>
	
# Hexo 使用填坑记录
> 填坑记录API https://blog.csdn.net/hosea1008/article/details/53404632
> > 添加node_modules文件目录太深
node_modules/****: Filename too long
在Stackoverflow上面找到了答案，这是由于Windows API限制了文件名长度为260字符造成的
执行以下指令
git config --system core.longpaths true
