# git名词解释
- workspace：工作区
- Index/Stage：暂存区
- Repository：仓库（本地）
- Remote：远程仓库
![常用git命令图示](images/图解git基本命令.png)

## 一、git全局配置
- git的配置文件.gitconfig 一般放在用户主目录下，对其可以进行全局配置或项目配置 
```  bash
# 进入用户主目录
$ cd ~
#使用vim编辑.gitconfig配置文件
$ vim .gitconfig
# 显示当前的Git配置
$ git config --list
# 设置用户名
$ git config --global user.name username  
# 设置用户邮箱          
$ git config --global user.email useremailaddress
```
- 在仓库中可以添加.gitignore文件，忽略对某些文件或某些类型的文件的跟踪
```bash
# 使用vim创建并编辑.gitignore文件
$ vim .gitignore
```

## 二、git仓库初始化
``` bash
# 将当前目录初始化成git仓库
$ git init
# 克隆一个git仓库
$ git clone url(仓库地址)
```
## 三、添加/提交/删除
- 工作区文件添加到暂存区
```bash
# 添加指定文件到暂存区
$ git add [filename]
# 将工作区所有文件添加到暂存区
$ git add .
# 一个文件多次添加
$ git add -p
```
- 暂存区文件提交到仓库
 
```bash
# 将暂存区所有文件提交到仓库
$ git commit -m "message"
# 将暂存区指定文件提交到仓库
$ git commit [filename] -m "message"
# 将工作区变动直接提交到仓库（已添加到暂存区的文件）
$ git commit -a -m "message"
$ git commit -am "message"
# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]
# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
```

	注意事项：每次提交要保证适当的颗粒度、相关性和独立性
	 message 格式规范
	<type>(&lt;scope>):<subject>
	//空一行
	<body>
	//空一行
	<footer>


- 删除文件

```bash
# 删除工作区文件，并且将这次删除放入暂存区 
$ git rm [filename]
# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [filename]
# 重命名文件,加入暂存区
$ git rm [filename1] [filename2]
# 移动文件,加入暂存区
$ git rm [filename] [directory]
```
## 四、标签操作
```bash
# 列出所有标签
$ git tag
# 查看指定标签信息
$ git show [tagname]
# 在当前提交上新增标签
$ git tag [tagname]
# 在当前提交上新增标签并给出message提示
$ git tag [tagname] -m "message"
# 在当前提交开始的第n个提交上新增标签
$ git tag [tagname] HEAD~n
# 删除本地tag
$ git tag -d [tagname]
# 删除远程tag
$ git push origin :refs/tags/[tagname]
# 将指定tag推送到远程
$ git push [remote] [tag]
# 将所有tag推送到远程
$ git push [remote] --tags
# 从远程拉取所有tag
$ git pull --tags
```










参考文档：
[常用 Git 命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)
