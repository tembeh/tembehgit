<This is a test message>
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
repository>
$ mkdir （目录名称）	//创建目录
$ cd（目录名称）	//打开目录
$ cat （文件名称）	//打开文件
$ pwd	//显示当前目录
$ git init	//目录变为Git管理仓库

$ git add （文件名称）	//添加文件至暂存区（stage），可反复多次使用，添加多个文件
$ git commit -m "（添加说明）"	//将暂存区所有修改提交到分支，同时必须添加本次提交说明

$ git status	//查看暂存区当前状态
$ git diff （文件名称）	//查看修改内容

$ git log	//查看修改历史
$ git log --pretty=oneline	//功能同上，简化显示
$ git reset --hard HEAD^	//回到上一个版本 其中HEAD^上个版本 HEAD^^上上个版本 HEAD~n 上n个版本
$ git reset --hard （commit id版本号）	//回退到commit id所对应版本
$ git reflog	//查看命令历史，也可找到commit id

<撤销修改>
$ git checkout -- （文件名称）	//用版本库版本替换工作区版本
$ git reset HEAD （文件名称）	//回退暂存区修改至工作区

<删除文件>
$ git rm （文件名称）	//删除文件

<远程库管理>
$ git remote add origin （github网址）	//关联github远程库
$ git push （远程库，默认名origin） （本地分支master）	//master分支最新修改推至github origin（$ git push -u origin master 第一次推送）
$ git clone （github网址）	//克隆远程库至本地
$ git remote	//查看远程库信息
$ git remote -v	//查看抓取和推送地址
$ git pull	//抓取远程文件
$ git checkout -b （本地分支名称） origin/（远程库分支名称）	//在本地创建和远程分支对应的分支
$ git branch --set-upstream （本地分支名称） origin/（远程库分支名称）	//建立本地分支和远程分支的关联

<分支创建与查看>
$ git branch （分支名称）	//创建分支
$ git checkout （分支名称）	//切换分支
$ git checkout -b （分支名称）	//创建+切换分支
$ git branch	//查看分支

<分支合并>
$ git merge （--no-ff） （分支名称）	//合并指定分支到当前分支，冲突时无法合并，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并
$ git log --graph	//查看分支合并图

<删除分支>
$ git branch -d （分支名称）	//删除分支
$ git branch -D feature-vulcan	//强行删除未被合并过的分支

<暂存当前工作>
$ git stash	//暂存当前工作
$ git stash list	//查看暂存区工作
$ git stash apply	//恢复工作
$ git stash drop	//删除暂存区工作
$ git stash pop	//恢复+删除
$ git stash apply （stash名称）	//恢复指定stash

<标签>
$ git tag （标签名称）	//创建标签（当前提交版本）
$ git tag （标签名称） （commit id）	//创建标签（commit id所对应版本）
$ git tag -a （标签名称） -m "（说明文字）" （commit id）	//创建带有说明的标签，-a改为-s则为PGP私钥签名标签
$ git tag	//查看所有标签
$ git show （标签名称）	//查看标签信息
$ git tag -d （标签名称）	//删除标签
$ git push （远程库，默认名origin） （标签名称）	//推送标签到远程，标签名称为--tags则推送所有标签
git push （远程库，默认名origin） :refs/tags/（标签名称）	//删除远程标签，需先本地删除
