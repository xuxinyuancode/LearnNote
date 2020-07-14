# git



### 设置git信息

1. git config --global user.name "Your Name"
2. git config --global user.email "email@email.com"
3. git config命令中的--global参数是全局参数

### 初始化git并添加文件

1. git init
2. git add xxx.txt  //把xxx.txt添加到git仓库
3. git commit -m “Your Change” //把文件提交到git，-m后面是提交说明

### 查看仓库状态

1. git status
2. git diff 

### 查看日志

1. git log
2. 显示从最近到最远的提交日志
3. 参数 --pretty=oneline 可以排列整齐

### 回退版本

1. git reset --hard HEAD^
2. 回退到上一个版本
3. git reset --heard xxx
4. git reflog 查看命令历史

### 工作区和暂存区

工作区有一个隐藏的目录.git，这是Git的版本库，其中最重要的就是stage（暂存区），默认创建master分支，以及指向master的一个指针叫HEAD

1. git add添加文件其实就是把文件修改添加到暂存区，git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。默认master分支，所以默认提交到master分支。
2. 简单来说就是所有的操作首先一个一个的提交到暂存区，然后再一次性的提交。

### 管理修改

1. git diff HEAD --xxx 可以查看xxx工作区和版本库里面最新版本的区别。

### 撤销修改

1. git checkout --  &lt;file&gt;   // lt gt
2. 撤销修改，这里有两种

### 删除文件

1. git rm &lt;file&gt;
2. git commit -m "xxx"

不过如果是不小心删除错了，那么可以使用命令：

git checkout --&lt;file&gt; 

原理是：版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以一键还原。

### 远程仓库

##### github

注册github，然后创建一个SSH KEY

```
ssh-keygen -t rsa -C "youremail@example.com"
```



### 强制覆盖本地代码

```shell
git fetch --all
git reset --hard origin/master
git pull
```



### 修改已经推送的commit

> 这个需要确保本地文件是最新的

```shell
git rebase -i HEAD~1
git commit --amend
git push -f
```





# 命令库



### 初始化操作

```
$ git config -global user.name <name>  #设置提交者名字
$ git config -global user.email <email>  #设置提交者邮箱
$ git config -global core.editor <editor>  #设置默认文本编辑器
$ git config -global merge.tool <tool>  #设置解决合并冲突时差异分析工具
$ git config -list  #检查已有的配置信息
```

### 创建新版本库

```
$ git clone <url>  #克隆远程版本库
$ git init  #初始化本地版本库
```

### 修改和提交

```
$ git add .  #添加所有改动过的文件
$ git add <file>  #添加指定的文件
$ git mv <old> <new> #文件重命名
$ git rm <file>  #删除文件
$ git rm -cached <file>  #停止跟踪文件但不删除
$ git commit -m <file> #提交指定文件
$ git commit -m “commit message”  #提交所有更新过的文件
$ git commit -amend  #修改最后一次提交
$ git commit -C HEAD -a -amend  #增补提交（不会产生新的提交历史纪录）
```

### 查看提交历史

```
$ git log  #查看提交历史
$ git log -p <file>  #查看指定文件的提交历史
$ git blame <file>  #以列表方式查看指定文件的提交历史
$ gitk  #查看当前分支历史纪录
$ gitk <branch> #查看某分支历史纪录
$ gitk --all  #查看所有分支历史纪录
$ git branch -v  #每个分支最后的提交
$ git status  #查看当前状态
$ git diff  #查看变更内容
```

### 撤消操作

```
$ git reset -hard HEAD  #撤消工作目录中所有未提交文件的修改内容
$ git checkout HEAD <file1> <file2>  #撤消指定的未提交文件的
修改内容
$ git checkout HEAD. #撤消所有文件
$ git revert <commit>  #撤消指定的提交
```

### 分支与标签

```
$ git branch  #显示所有本地分支
$ git checkout <branch/tagname>  #切换到指定分支或标签
$ git branch <new-branch>  #创建新分支
$ git branch -d <branch>  #删除本地分支
$ git tag  #列出所有本地标签
$ git tag <tagname>  #基于最新提交创建标签
$ git tag -d <tagname>  #删除标签
```

### 合并与衍合

```
$ git merge <branch>  #合并指定分支到当前分支
$ git rebase <branch>  #衍合指定分支到当前分支
```

### 远程操作

```
$ git remote -v  #查看远程版本库信息
$ git remote show <remote>  #查看指定远程版本库信息
$ git remote add <remote> <url>  #添加远程版本库
$ git fetch <remote>  #从远程库获取代码
$ git pull <remote> <branch>  #下载代码及快速合并
$ git push <remote> <branch>  #上传代码及快速合并
$ git push <remote> : <branch>/<tagname>  #删除### 远程分支或标签
$ git push -tags  #上传所有标签
```

### 本地与远程仓库冲突

 先 git fetch origin 然后git merge origin/master, 和本地分支合并, 之后再push。 



### 克隆以前的版本

- 首先克隆最新版本
- 然后 git log -数字，找到要需要的版本，记住commit
- 最后git checkout commit里面的东西就行了