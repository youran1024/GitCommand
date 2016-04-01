


## git 命令

##### 远程仓库的操作
1. 关联远程仓库	
	
	`$git remote add [name] [url]`
	
	
2. 修改关联仓库
	
	`$git remote set-url --push[name][newUrl]`
	
3. 删除关联仓库

	`$git remote rm [name]`
	
4. 克隆远程仓库
	
	`$git clone https://github.com/youran1024/GitTest.git`
	
	`$git clone git@github.com:youran1024/GitTest.git`
 
5. 创建本地仓库

	`$git init`

6. 关联远程仓库 (创建好本地的仓库后，通过此命令跟远程仓库做关联)

	`$git remote add origin git@server-name:path/#remoteRepository#.git`
	
7. 查看远程相关信息

	`$git remote -v`
	
8.	查看本地分支对应的远程分支
	
	`$git branch -vv`
	
9.	产看系统配置的文件

	`$git config --list`
	
8. 提交修改

	`$git push  #remote# #branch#`
	
9. 获取服务器上的最新版本，并自动合并

	`$git pull #remote# #branch#`

10. 获取服务器上的最新版本,不做合并

	`$git fetch`
	
11. 删除文件
	`$git rm #file#`


#### 分支的操作
1. 查看分支

	`$git branch`
	
2. 查看远程分支

	`$git branch -a`
	
3. 创建本地分支

	`$git branch #newBranch#`
	
4. 建立本地分支和远程分支的关联

	`$git branch --set-upstream #localBranch# origin/#remoteBranch#`
	
	本地的分支跟踪线上的分支
	
	`$git branch --track #newBranch# #remoteBranch#`

3. 创建远程分支到本地

	`$ git checkout -b #localBranch# origin/#remoteBranch#`
	
2. 创建分支 (把本地分支推送到远程，或者把本地的代码更新到远程对应的分支)

	`$git push origin #localBranchName#`

3. 切换分支

	`$git checkout #branchName#	`
	
4. 创建并切换分支

	`$git checkout -b #branchName#`

5. 删除分支

	`$git branch -d #branchName#`

6. 强制删除分支（如果有没有提交的代码，需要强制删除，才能删掉分支，否则要首先撤掉修改过的代码）

	`$git branch -D #branchName#`
	
6. 删除远程分支

	`$git push origin --delete #remoteBranchName#`		
7. 合并其它分支到当前分支

	`$git merge #branchName#`
	
	git rebase #branchName# 是把branch里的每一次提交生成一个补丁，然后跟当前的分支做合并。
	
	`$git rebase #branchName#`
	
	git rebase 的过程中会有冲突，冲突解决过后要用
	
	`$git rebase --continue`
	
10. 同步本地远程分支

	`$git checkout --track origin/develop`
	
11. 删除文件
	`$git rm #file#`

12. 添加文件
	`$git add .`
	
	
##### 解决冲突

	`$git merge`
	
	git rebase #branchName# 是把branch里的每一次提交生成一个补丁，然后跟当前的分支做合并。
	
	`$git rebase`

##### 版本比较
1.	和当前库里最新的作比较

	`$git diff HEAD -- #fileName#`
	
##### 撤销操作

1.	没`$git add .`之前

	`$git checkout -- #file#`
	
	单独撤销某个文件的修改
	
	`$git checkout HEAD #file#`

2. 撤销Commit 之前的操作 (版本指针做了重新的指向)
	如果是--hard 撤销的话，则存储区内没有变化
	如果是--soft（默认），则存储区将commit id 之前所有的commit发生的变化，放到了存储区。 

	`$git reset HEAD #commit id#`
	
	先用Git Log 查看CommitID，根据Id做版本回退

3. 撤销某个版本，但不影响其它的版本

	`$git revert #commitid#`

4.	回到当前版本（HEAD）的上一版本

	--hard 撤销版本，不保留修改
	
	`$git reset --hard HEAD^`		
	
	上上版本
	
	`$git reset --hard HEAD^^`
	
	上N个版本
	
	`$git reset --hard HEAD^~N`
	
	撤销版本，并保留修改
	
	`$git reset #commit id#`

5.	根据Commit ID 做回退
	
	`$git reset --hard #Commit id#`
	
6.	回退到某个版本，并保留当前的修改

	`$git reset --keep #commit id#`
	

6.	(往后回退了，又想往前回退)需要以前的Commit 记录

	`$git reflog`


##### 保存工作状态
1.	保存
	`$git stash`
	
2.	列表
	`$git stash list`
	
3.	恢复
	`$git stash apply`
	
4.	删除
	`$git stash drop`
	
5.	恢复并删除
	`$git stash pop`


##### 标签的操作

1. 查看标签

	 `$git tag`
	 
2. 创建标签：

	`$git tag #tagName#`
	
3. 创建标签并添加标签信息

	`$git tag -a #tagname# -m "blablabla...`
	
4. 查看标签的信息

	`$git show #tagName#`

5. 提交Tag到远程 (提交操作同分支)

	`$git push origin #tagName#`
	
6. 提交本地所有的Tag (提交本地所有的分支那？？)

	`$git push origin --tags`


6. 删除标签

	`$git tag -d #tagName#`

7. 删除远程tag
	
	`$git push origin :refs/tags/#tagname#`



#####查看历史

1. 那个文件都发生过哪些变化

	`$git log -p #file#`
	
2. 查看最近两次的更新内容
	
	`$git log -p -2`
	
3. 产看某次提交Commit的内容

	`$git show #commit-hash-id#`

4. 看看那个文件被谁改变过
	
	`$git blame #file#`
	
5.	酷炫的Git log 查看方式 [个性化你的Log](https://ruby-china.org/topics/939)
 	
 	[1]
 	`git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative`
 	
 	[2]
 	`git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)#%an#%Creset' --abbrev-commit"`
 
#####其它
 
1.	git 配置别名 (以后可以用 git lg 代替 git log --graph)

	[git lg]显示图形化的Log
	
	`$git config --global alias.lg "log --graph"`

	[git last]查看看最后一次提交信息
	
	`$git config --global alias.last 'log -1'`
	
	
2. 忽略某些文件 

	GitHub已经为我们准备了各种配置文件[gitHub](https://github.com/github/gitignore)

##### 鸣谢

个性化你的Log

* 传送门：[biu ~](https://ruby-china.org/topics/939)

关于git的详细介绍请参照#RED#廖雪峰#/RED#老师的讲解。

* 传送门：[biu ~](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
* 传送门（远程操作篇）：[biu ~](http://www.ruanyifeng.com/blog/2014/06/git_remote.html)

##### 注意事项

1.	你要知道，工作区，暂存区，和版本库
	工作区修改文件后，通过`git add .`添加到暂存区，如果没有问题，则通过`git commit -m "#message#"`提交到版本库
	
2. 在操作员称仓库前请注意你是否具有某远程仓库的操作权限

3. 在熟练使用前请不要在线上分支上做练习

##### The Last 

有失误之处欢迎修改

如果你需要补充这个文档，欢迎ForkMe并提交你的修改

* 传送门：[Mr.Yang@github](https://github.com/youran1024)

2015 Copy right @Mr.Yang  v1.0.1

