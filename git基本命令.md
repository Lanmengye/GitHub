# git名词解释
- workspace:工作区
- Index/Stage:暂存区
- Repository:仓库（本地）
- Remote:远程仓库
![常用git命令图示](images/图解git基本命令.png)

## 一、git全局配置
git的配置文件.gitconfig 一般放在用户主目录下，对其可以进行全局配置或项目配置 
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
在仓库中可以添加.gitignore文件，忽略对某些文件或某些类型的文件的跟踪

## 二、git仓库初始化
``` bash
# 将当前目录初始化成git仓库
$ git init
# 克隆一个git仓库
$ git clone url(仓库地址)
```
## 三、增加/提交/删除










参考文档：
[常用 Git 命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)