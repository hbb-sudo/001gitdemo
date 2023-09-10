# git

## 版本控制 
	1.1集中式 svn 使用简单 网络故障或服务器出现问题 无法提交更新数据库
		1.1.1直接提交到服务器
	1.2分布式 git
		1.2.1分为服务器版本和本地历史记录
## git安装
	官网下载直接安装git  https://git-scm.com/
	cmd git -v 检查是否安装git和版本
	配置用户名和邮箱
	git config --global user.name "xql"  //用户名 global 整个仓库
	git config --global user.email "2088356901@qq.com" //邮箱
	git config --global credential.helper store //保存用户信息
	git config --global --list //查看用户信息

## 基本使用

###  创建仓库
	1创建方式 git init 和 git init
	2创建本地仓库git init， 拉去远程仓库 git clone  
	3文件夹目录 cmd git init
	4git clone 后面拼接地址 拉取远程仓库
###  介绍
    1本地数据管理 分为三个区域 工作区 暂存区 本地仓库
    1.1 工作区 本地电脑
    1.2 暂存区 保存即将要提交到git仓库的修改内容
    1.3 本地仓库 git init 创建的仓库
    规则： 工作区 （git add）==> 暂存区（git commit） ==> 本地仓库

    2状态 未跟踪 未修改 已修改  已暂存 
    2.1 未跟踪 新建文件
    2.2 未修改 git接手但未改变
    2.3 已修改 已修改还没进行暂存 
    2.4 已暂存 （git add）

    3.如果是空文件夹不会被git提交

### git reset 版本回退
    1三种模式 --soft --hard --mixed
        1.1git reset --soft 软的 回退某个版本 保留工作区和暂存区的所有内容
        1.2git reset --hard 硬的 回退某个版本 丢弃工作区和内存区的所有修改内容
        1.3git reset --mixed 混合 回退到个版本 只保留工作区的修改内容不要暂存
### git diff 比较版本差异
    1.默认比较 工作区和暂存区的差异
    2.git diff HEAD 比较暂存区和本地仓库的差异
### 删除文件 删除后要提交 commit
    1.直接删除 需要执行 add
    2.git rm file1.txt 不需要执行add
    3.git rm --cached 1.txt  //删除本地仓库，不删除工作区
### 忽略 .gitignore
    1.echo 1.txt >.gitignore
    2. *a //忽略所有.a文件
    3.!add.a //排除!add.a忽略所有.a文件
    4./todo //忽略当前目录下的todo文件
    5.bud/ //忽略任何目录下的bud文件
    6.doc/*.txt //或略doc下面.txt文件
    7.doc/**/*.pdf //忽略doc目录和子目录下的.pdf文件
### 创github仓库
    1.https://github.com/ 进入官网登录
    2.Top Repositories new 点击绿色按钮新建一个项目 
        2.1 Repository name // 输入项目的名称
        2.2Description (optional) 项目说明
        2.3Public 选择公共库
    3.Create repository 创建完成

    5.新建绑定密钥 
        5.1 cmd后执行 ssh-keygen -t rsa -b 4096
        5.2 如果第一次创建执行5.1后直接回车，如果之前有密钥，回车会覆盖之前的密钥且操作不可逆，可输入一个新的文件名后回车 text
        5.3 Enter passphrase (empty for no passphrase): 输入密码，这次执行的是双回车
        5.4 Your public key has been saved in test.pub. 密钥在text.pub 文件中，用vscode 打开
        5.4 github 右上角用户点开找到设置Settings => SSH and GPG keys => New SSH key 按钮 => Title 输入标题例如 text => key中填写密钥
    6.右击 Open Git Bash here
        6.1 git remote -v //查看当前有什么项目的别名
        6.2 git remote add 001git https://github.com/hbb-sudo/001newAddProject.git  //创建别名 001git 是别名
    7.推送 提交
        7.1 git push 001gitdemo master  推动数据到master分支
    8.拉取 更新
        8.1 git pull 001gitdemo master 
    9.克隆  git clone https://github.com/hbb-sudo/001newAddProject.git
        克隆会完成的操作：
            1.拉取代码 
            2.初始化本地仓库 
            3.创建别名








# 命令
## ？？=== 多个不指当前一个参数
## git init
创建仓库
## git status 
查看仓库的状态
## echo "这是" > file1.txt
添加/创建一个文件
## git add 
添加到暂存区 等待提交  使用：git add file1.txt
## git add .
所有文件保存到暂存区
## git commit
提交 只会提交暂存区的文件，提交后暂存区不在
进入 交互式界面 ： 方向键切换 i键备注提交信息， esc回到上一步， 输入:wq 保存退出 
## git commit -m "备注信息"
提交 -m 不进入交互页面 
## git log
查看提交记录 以及版本id
## git log --oneline
查看简介提交记录
## git ls-files 
git仓库中的所有文件
## git ls-tree -r HEAD
当前分支最新提交的所有文件
## git log --name-status
版本操作记录查看
## git reset
版本回退
### git reset --soft 5af9001 
5af9001 === 要回退的版本id 上个版本 === HEAD^
### git reset --hard HEAD^
回退上个版本 
### git reset --mixed HEAD^
回退上个版本
## git reflog 版本回溯 
找到id后在进行 --hard id 回到之前版本
## git diff 
### git diff HEAD
比较暂存区和本地仓库的差异
### git diff --cached
比较暂存区和版本库之间的差距
### git diff b391fce 8eb01d1 
比较两个版本的差距 
### git diff HEAD~ HEAD
比较和上一个版本差异
### git diff HEAD~2 HEAD
比较和2个版本差异
### git diff HEAD~ HEAD 3.txt
比较和1个版本差异 中 3.txt中的差异
## 删除文件 删除后要提交 commit
### 直接删除 
需要执行 add
### git rm file1.txt 
不需要执行add
### git rm -r* 
某个文件下所有字目录和文件 
### git rm --cached 1.txt 
 //删除本地仓库，不删除工作区
## 忽略 .gitignore //完成后提交
## echo 1.txt >.gitignore
已提交到本地仓库文件无法忽略，先执行删除后在忽略
## git remote -v
查看当前有什么项目的别名
## git remote add 001gitdemo https://github.com/hbb-sudo/001newAddProject.git
 //创建别名 001gitdemo 是别名
## git push 001gitdemo master 
推送/提交 到远程库 master === 分支
## git pull 001gitdemo master 
拉取/更新 到本地
## git clone https://github.com/hbb-sudo/001newAddProject.git
克隆代码到本地 不需要登录账号 
## cat 3.txt 
查看内容




# 流程
## git init
创建仓库
## git status 
查看仓库的状态
## git add 
添加到暂存区 等待提交  使用：git add file1.txt
## git add .
所有文件保存到暂存区
## git commit
提交 只会提交暂存区的文件，提交后暂存区不在
进入 交互式界面 ： 方向键切换 i键备注提交信息， esc回到上一步， 输入:wq 保存退出 
## git commit -m "备注信息"
提交 -m 不进入交互页面 
## 官网github 
创建一个新的远程库
##  git remote add 001gitdemo https://github.com/hbb-sudo/001newAddProject.git
创建别名
## git push 001gitdemo master 
推送/提交 到远程库
## git pull 001gitdemo master 
拉取/更新 

## 误删除
### git status
### git reset HEAD .
### git checkout .



	