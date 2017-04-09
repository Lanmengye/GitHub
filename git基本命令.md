# git名词解释
- workspace：工作区
- Index/Stage：暂存区
- Repository：仓库（本地）
- Remote：远程仓库
![常用git命令图示](images/图解git基本命令.png)

## 一、git配置
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
# 设置git命令的别名
$ git config --global alias.[commamdRename] [commandOriginal]
# 存储凭证
$ git config --global credential.helper wincred
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
	type:
		feat:新功能 feature
		fix: 修补bug
		docs:文档 documentation
		style:格式（不影响代码运行的变动）
		refactor:重构（既不是新增功能，也不是修改bug的代码变动）
		test:增加测试
		chore:构建过程或辅助工具的变动


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
## 五、查看信息
```bash
# 显示有变更的文件
$ git status
# 以短形式显示有变更的文件
$ git status -sb (short and branch)

# 显示某个提交信息
$ git show HEAD~n

# 显示当前分支的版本历史
$ git log
# 显示当前分支的前n条提交
$ git log -n

# 单行显示当前分支的每一次版本历史
$ git log --oneline
# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s
# 以图形的方式显示提交日志
$ git log --pretty=format:'%h %ad | %s%d' -graph -data=short

# 搜索提交历史，根据关键词
$ git log -S [keyword]
# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep [feature]

# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat
# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]
# 显示指定文件相关的每一次diff
$ git log -p [file]
# 显示指定文件是什么人在什么时间修改过
$ git blame [file]
# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn

# 查看工作区与暂存区的差异
$ git diff
# 查看暂存区与仓库的差异
$ git diff --cached
# 查看工作区与仓库的差异
$ git diff HEAD
# 查看两个版本之间的差异
$ git diff version1 version2
# 查看工作区与版本version1之间的差异
$ git diff version1
```
## 六、回撤操作
```bash
# 恢复暂存区的指定文件到工作区
$ git checkout [file]
# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]
# 恢复暂存区的所有文件到工作区
$ git checkout .
# 将暂存区文件回撤到工作区（重置暂存区）
$ git reset HEAD
# 将提交回撤到暂存区
$ git reset HEAD --soft
# 回撤提交，放弃变更
$ git reset HEAD --hard
# 回撤远程仓库 -f即--force
$ git push -f
# 变基操作，改变历史提交
$ git rebase -i HEAD~n
```
## 七、分支操作
```bash
# 列出所有本地分支
$ git branch
# 查看分支及其提交信息
$ git branch -v
# 列出所有远程分支
$ git branch -r
# 列出所有本地分支和远程分支
$ git branch -a
# 查看已合并的分支
$ git branch --merged
# 查看未合并的分支
$ git branch --no-merged

# 新建分支(不切换到该新建分支)
$ git branch [branchname]
# 切换分支
$ git checkout branchname
#新建分支并切换到该分支
$ git checkout-b branchname
# 新建一个分支，指向指定commit
$ git branch [branch] [commit]
# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]
# 修改分支名字
$ git branch -m old_name new_name (发生冲突时修改名字失败)
$ git branch -M old_name new_name (发生冲突时强制执行修改)


# 删除分支
$ git branch -d branchname (对未合并的分支执行该操作时发生错误)
$ git branch -D branchname (强制删除)
# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
$ git push origin  :<remote branch>
# 取出远程分支
$ git checkout -t origin/branchname

# 保存进度
$ git stash
# 弹出进度
$ git stash pop
# 查看进度列表
$ git stash list
# 删除stash列表
$ git stash clear

# 合并分支(前向快速合并、合并提交)
$ git merge branchname
```

## 八、冲突解决
冲突产生的原因：
    1. 在不同分支上，修改了同一个文件
    2. 不同的人，修改了同一个文件
	3. 不同的仓库，修改了同一个文件
冲突产生的时间：冲突只在合并分支的时候才会发生
发生冲突并不可怕，冲突的代码不会丢失，解决冲突，重新提交，commit时不要给message
冲突信息的格式：
```bash
<<<<<<< HEAD
context -master
================
context -branch
>>>>>>> branch
```

## 九、远程同步
```bash
# 下载远程仓库的所有变动
$ git fetch [remote]
# 显示所有远程仓库
$ git remote -v
# 显示某个远程仓库的信息
$ git remote show [remote]
# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]
# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]
# 上传本地指定分支到远程仓库
$ git push [remote] [branch]
# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force
# 推送所有分支到远程仓库
$ git push [remote] --all
```







参考文档：
[常用 Git 命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)
