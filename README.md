# GitCommand



## git 命令

##### 远程仓库的操作
1. 添加远程仓库	
	
	`$git remote add [name] [url]`
	
	
2. 修改远程仓库
	
	`$git remote set-url --push[name][newUrl]`
	
3. 删除远程仓库

	`$git remote rm [name]`
	
4. 克隆远程仓库
	(2种协议，一种是https协议, 一种是ssh协议)
	
	`$git clone https://github.com/youran1024/GitTest.git`
	
	`$git clone git@github.com:youran1024/GitTest.git`
 
5. 创建本地仓库

	`$git init`

6. 关联远程仓库 (创建好本地的仓库后，通过此命令跟远程仓库做关联)

	`$git remote add origin git@server-name:path/<remoteRepository>.git`
	
7. 查看远程相关信息

	`$git remote -v`
	

	
##### 分支的操作
1. 查看分支

	`$git branch`
	
2. 查看远程分支

	`$git branch -a`
	
3. 创建本地分支

	`$git branch <newBranch>`
	
4. 建立本地分支和远程分支的关联

	`$git branch --set-upstream <localBranch> origin/<remoteBranch>`

3. 创建远程分支到本地

	`$ git checkout -b <localBranch> origin/<remoteBranch>`
	
2. 创建分支 (把本地分支推送到远程，或者把本地的代码更新到远程对应的分支)

	`$git push origin <localBranchName>`

3. 切换分支

	`$git checkout <branchName>	`
	
4. 创建并切换分支

	`$git checkout -b <branchName>`

5. 删除分支

	`$git branch -d <branchName>`

6. 强制删除分支（如果有没有提交的代码，需要强制删除，才能删掉分支，否则要首先撤掉修改过的代码）

	`$git branch -D <branchName>`
	
6. 删除远程分支

	`$git push origin --delete <remoteBranchName>`		
7. 合并其它分支到当前分支

	`$git merge <branchName>`
	
10. 同步本地远程分支

	`$git checkout --track origin/develop`
	
11. *添加某个分支的某个Commit*
	
	` git cherry-pick #commitID#`
	
	通过cherry-pick 命令取出某个CommitID， 然后同步到某个分支上
	
12. *合并分支，但是不合并分支上的Commit*

	`$ git merge --squash #branch#`
	
	 #branch#上的Commits 会被当成一个 修改 提交到#当前分支#， 但并没有Commit，所以完成后需要Commit 一下
	
13. 通过补丁的方式，执行合并。[详解](http://gitbook.liuhui998.com/4_2.html)

	首先把分支里的每个提交(commit)取消掉，然后把它们临时保存为补丁(patch)(这些补丁放到".git/rebase"目录	中),最后把#当前分支#更新到最新的#branch#分支，最后把保存的这些补丁应用到#当前分支#分支上
	
	` $ git rebase #branch#`
	
	碰到冲突后，修改冲突
	
	`$ git rebase --continue`
	
	终止
	
	`$ git abort`
	
14. 

##### 解决冲突

1.	手动解决


##### 版本比较
1.	和当前库里最新的作比较

	`$git diff HEAD -- #fileName#`
	
##### 版本撤销

1.	没`git add .`之前

	`$git checkout -- #file#`

2. 撤销Commit 之前的操作

	`git reset HEAD #fileName#`
	
##### 保存当前工作的更改
1.	`$git stash`
2.	列出保存的
	`$git stash list`


##### 版本回退
先用Git Log 查看CommitID，根据Id做版本回退

1.	回到当前版本（HEAD）的上一版本
	`$git reset --hard HEAD^`		
	
	上上版本
	
	`$git reset --hard HEAD^^`
	
	上N个版本
	
	`$git reset --hard HEAD^~N`
	

2.	根据Commit ID 做回退
	
	`$git reset --hard #Commit id#`
	
3.	(往后回退了，又想往前回退)需要以前的Commit 记录

	`$git reflog`


##### 保存工作状态
1.	保存
	`$git stash`
	
2.	列表
	`git stash list`
	
3.	恢复
	`git stash apply`
	
4.	删除
	`git stash drop`
	
5.	恢复并删除
	`git stash pop`


##### 标签的操作

1. 查看标签

	 `$git tag`
	 
2. 创建标签：

	`$git tag <tagName>`
	
3. 创建标签并添加标签信息

	`$git tag -a <tagname> -m "blablabla...`
	
4. 查看标签的信息

	`$git show <tagName>`

5. 提交Tag到远程 (提交操作同分支)

	`$git push origin <tagName>`
	
6. 提交本地所有的Tag (提交本地所有的分支那？？)

	`$git push origin --tags`


6. 删除标签

	`$git tag -d <tagName>`

7. 删除远程tag
	
	`$git push origin :refs/tags/<tagname>`

8. 获取标签

	`￥git checkout -b #newbranch# #tag#`



#####其它


2.	酷炫的Git log 查看方式 [个性化你的Log](https://ruby-china.org/topics/939)
 	
 	[1]
 	`git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset' --abbrev-commit --date=relative`
 	
 	[2]
 	`git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`
 
3.	git 配置别名 (以后可以用 git lg 代替 git log --graph)

	[git lg]显示图形化的Log
	
	`git config --global alias.lg "log --graph"`

	[git last]查看看最后一次提交信息
	
	`$ git config --global alias.last 'log -1'`
	
3. 忽略某些文件 

	GitHub已经为我们准备了各种配置文件[gitHub](https://github.com/github/gitignore)

##### 鸣谢

个性化你的Log

* 传送门：[biu ~](https://ruby-china.org/topics/939)

关于git的详细介绍请参照<RED>廖雪峰</RED>老师的讲解。

* 传送门：[biu ~](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
* 传送门（远程操作篇）：[biu ~](http://www.ruanyifeng.com/blog/2014/06/git_remote.html)
* GitBook1[biu ~](http://gitbook.liuhui998.com/index.html)
* GitBook2[biu ~](https://git-scm.com/book/zh/v2/)

##### 注意事项

1.	你要知道，工作区，暂存区，和版本库
	工作区修改文件后，通过`git add .`添加到暂存区，如果没有问题，则通过`git commit -m "#message#"`提交到版本库
	
2. 在操作员称仓库前请注意你是否具有某远程仓库的操作权限

3. 在熟练使用前请不要在线上分支上做练习

##### The Last 

如果你需要补充这个文档，欢迎ForkMe并提交你的修改

* 传送门：[Mr.Yang@github](https://github.com/youran1024)

2015 Copy right @Mr.Yang  v1.0.0

