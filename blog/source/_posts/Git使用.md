title: Git使用
date: 2015-6-08 12:22:15
categories: iOS
tags: [Git,技术]
---

### Git和SVN区别

最核心的区别Git是分布式的，而Svn不是分布的。

Git的特点版本控制可以不依赖网络做任何事情，对分支和合并有更好的支持(当然这是开发者最关心的地方)。

### 安装Git

```
$ git    //判断是否安装了git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git

```

### Git命令行

初始化

```
初始化Git：git init 
```

添加提交文件

```
添加文件：git add index.html    //告诉Git，把文件添加到仓库

添加多个文件：git add file2.txt file3.txt    //添加2个文件到仓库

提交代码：git commit -m "wrote a readme file"    //提交代码

查看仓库状态：git status

查看文件变化：git diff index.html 

```

日志

```
完整的日志：git log 

日志参数：git log --pretty=oneline  

查看之前每次命令：git reflog    

```
撤销

```
全部撤销工作区的修改：git checkout -- index.html       

回退到上一个版本：git reset --hard HEAD^  

回退到某个版本号，：git reset --hard 3628164

删除文件（可用checkout恢复）：rm index.html    

删除文件（可用git reset --hard HEAD恢复）：git rm index.html    //

```
远程Git

```
关联远程仓库：git remote add origin git@github.com:flyer012/ProName.git   
关联分支：git branch --set-upstream dev origin/dev
首次推送并关联分支：git push -u origin master   
推送最新修改：git push origin master
抓取远程Git：git pull    
克隆一个本地库：git clone git@github.com:flyer012/ProName.git 

```

分支

```
查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

删除分支：git branch -d <name>

强行删除分支：git branch -D <name>

合并某分支到当前分支（不保留分支信息）：git merge <name>

合并某分支到当前分支(保留分支信息): git merge --no-ff -m "merge with no-ff" dev

查看分支历史：git log --graph --pretty=oneline --abbrev-commit

查看远程库的信息：git remote

查看远程库详细的信息：git remote -v

```
临时存储

```
存储目前工作区：git stash
查看存储的列表：git stash list
恢复内容：git stash apply
删除内容：git stash drop
恢复并删除stash内容：git stash pop
恢复指定存储内容：git stash apply stash@{0}

```

标签

```
查看标签：git tag
创建标签：git tag <name>
创建标签：git tag <name>
历史提交的commit id：git log --pretty=oneline --abbrev-commit
指定标签信息：git tag -a <tagname> -m "blablabla..." <分支号>
显示标签信息： git show v0.1
删除标签：git tag -d v0.1

推送某个标签到远程：git push origin <tagname>
一次性推送全部尚未推送到远程的本地标签：git push origin --tags

```

多人合作

```
因此，多人协作的工作模式通常是这样：

首先，可以试图用git push origin branch-name推送自己的修改；

如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

如果合并有冲突，则解决冲突，并在本地提交；

没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！

如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name。

```


### 其他

参考：[廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)








