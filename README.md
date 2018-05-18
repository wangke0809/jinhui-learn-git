# jinhui-learn-git
jinhui-learn-git

### clone

从远程仓库克隆仓库

	git clone git@github.com:wangke0809/jinhui-learn-git.git

通过ssh方式克隆，需要先将本地公钥添加至GitHub。

### status

查看状态

	git status

可以知道本地分支名称和远程分支名称。

### add

添加文件到仓库
	
	# 添加单个文件
	git add filename
	# 添加所有文件
	git add .

### commit

提交修改

	# -m 后跟本次提交的说明内容
	git commit -m "some msg" 

### push

将本地仓库推送到远程仓库

	# push到远程仓库
	git push origin master

其中`origin`是默认远程仓库名字，依据情况而定,`master`为当前所在分支。

### pull

从远程仓库拉取到本地仓库
	
	# 也可以直接 git pull ，表示拉去远程origin/master分支到当前分支
	# 默认pull的远程分支为本地对应的远程分支
	# 当然也可以指定
	git pull origin master

注意养成好习惯，每次改代码之前先`git pull`，保持本地仓库处于最新状态。

#### .gitignore

该文件作用为指定当前文件夹下要忽略的文件，可以使用通配符\*等

比如忽略指定文件夹`.DS_Store/`。
忽略所有pyc结尾的文件`*.pyc`。

### pulla解决冲突

	- 远程仓库较新，本地仓库也修改了文件，但是修改的文件远程仓库并没有修改，系统自动合并。
	- 远程仓库较新，本地仓库也修改了文件，本地修改的文件远程也修改了
		- 本地先提交修改到仓库(add, commit)，手动解决更新(先pull, 再手动更改)之后再add, commit, push
		- 首先git stash，将本地修改缓存起来(还没有add, commit)，正常git pull ,提升拉取成功(因为本地相当于什么都没有修改)，如果放弃本地更改，则无需操作，否则，git stash pop，弹出最新一次（stash 栈顶）的修改进行手动合并
