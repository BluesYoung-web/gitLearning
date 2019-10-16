# 本地使用
- 将当前目录变为git管理仓库
`git init`
- 新建`readme.txt`
- 将文件添加到仓库
`git add readme.txt`
- 把文件提交到仓库
`git commit -m "wrote a readme file"`
`-m`后面输入的是本次提交的说明，将写入历史记录
多次`add`不同的文件，`commit`一次提交
- 修改`readme.txt`，使用`git status`查看状态
- 使用`git diff readme.txt`查看修改的地方
- 再次`add`和`commit`
- 查看提交历史记录`git log`
`--pretty=oneline`一条记录显示一行
- 回到上一个版本`git reset --hard HEAD~1`
回到前n个版本——`HEAD~n`
回到特定版本——`7542a`
- `git reflog`用来记录你的每一次命令
## 工作区与暂存区
- 当前文件夹即为工作区`.git`除外
- `.git`为版本库
- `.git`里面的`index`或`stage`为暂存区
`git add`把文件添加进去，实际上就是把文件修改添加到暂存区
`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支
创建`Git`版本库时，`Git`自动为我们创建了唯一一个`master`分支，所以，现在，`git commit`就是往`master`分支上提交更改
- `git checkout -- readme.txt`可以丢弃工作区的修改
- `git reset HEAD readme.txt`可以把暂存区的修改撤销掉（`unstage`），重新放回工作区
## 删除文件
- windows：dir看当前目录文件===ls
- `del LICENSE`/`rm LICENSE`删除本地文件
- 从版本库中删除该文件，那就用命令`git rm LICENSE`然后`git commit`
- 把误删的文件恢复到最新版本`git checkout -- LICENSE`
## 上传到远程仓库
- 创建SSH Key
`ssh-keygen -t rsa -C "youremail@exp.com"`
一路回车，直到结束
可以在用户主目录里找到`.ssh`目录，里面有`id_rsa`和`id_rsa.pub`两个文件
- 登陆GitHub，打开“Account settings”，“SSH Keys”页面
- 点“New SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容
- 点“Add Key”，你就应该看到已经添加的Key
- 登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库——gitLearning
- 关联远程仓库：
`git remote add origin https://github.com/BluesYoung-web/gitLearning.git`
- 将本地内容推送到远程
`git push -u origin master`
- 此后，每次本地提交后，只要有必要，就可以使用命令
`git push origin master`推送最新修改