---
title: "常用命令"
# image: 
  # path: /images/so-simple-sample-image-3.jpg
  # thumbnail: /images/so-simple-sample-image-3-400x200.jpg
  # caption: "Photo from [WeGraphics](http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/)"
categories:
  - Command
tags:
    - adb
    - fastboot
    - python
    - git
    - vim
    - Ubuntu
last_modified_at: 2020-03-23T14:28:50-05:00
---

# Pyhton
1. 更新pip: 

	`python -m pip install --upgrade pip`
	
2. 更新所有包: 
	
	`pip freeze --local | grep -v '^\-e' | cut -d = -f 1  | xargs pip install -U`
	
# adb
1. 下载地址: [Google 官方下载地址](https://developer.android.com/studio/releases/platform-tools)
2. 批量pull文件: `adb shell ls data/media/0/app*.txt | tr "\n\r" " " | xargs -n1 adb pull`
3. 保留数据卸载app: `adb uninstall -k <package> //卸载app但保留数据和缓存文件`
4. 
	
# Git
1. 丢弃本地更改, 强制同步远端仓库:

	```
	git fetch --all
	git reset --hard origin/master
	```
2. 断点续传:

	```
	git fetch git://…..git
		即使断掉了，可以继续
	git fetch git://…..git
		等到fetch完会出现以下字样
	From git://….
	*branch           HEAD                -> FETCH_HEAD
		意思是把最新的数据fetch到了本地的FETCH_HEAD分支上去了
		然后用git checkout FETCH_HEAD
		或者也等同于git fetch git://…..git HEAD：FETCH_HEAD(没测试）
	例如：
	(1): git fetch git://repo.or.cz/tomato.git
		如果中途掉线，继续执行上面(1)命令
	(2): git checkout FETCH_HEAD 或者 git fetch git://repo.or.cz/tomato.git HEAD 
	```
	
3. 把Git Bash Here添加到右键菜单(针对Portable):

	```
	打开注册表，进入 HKEY_CLASSES_ROOT\Directory\Background\shell，在shell下新建项并命名为 Git Bash Here；再在“Git Bash Here”目录下新建项并命名为 Command，其值为 "D:\Program Files (x86)\PortableGit\git-bash.exe"，即git-bash.exe所在的完整路径，注意加引号。
	```
# Ubuntu
1. 配置语言环境:
	
	`dpkg-reconfigure locales`
	