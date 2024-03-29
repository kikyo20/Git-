### 一、常用命令

初始化一个Git仓库：
`git init`

添加文件到Git仓库：
1. 使用命令`git add <file>`，注意，可反复多次使用，添加多个文件；
2. 使用命令`git commit -m <message>`，完成。

`git status`告诉你有文件被修改过
`git diff`可以查看修改内容

`git log`查看日志，规范的话可以加参数`git log --pretty=oneline`

`git reset --hard commit_id`回退版本
`git reflog`查看历史命令

`git checkout -- <file>`撤销在工作区的修改(其实就是版本库里的版本替换工作区的版本)
例如：`git checkout -- readme.md`

`git rest HEAD <file>`撤销暂存区的修改
例如：`git reset HEAD readme.md`

`git rm <file>`删除版本库中的文件

`git remote add origin <origin>`关联一个远程库（先有本地库后有无程库时如何关联远程库）
例如：`git remote add origin git@github.com:kikyo20/Git-.git`

`git push -u origin master`第一次推送master分支的所有内容

`git clone <origin>`从远程库克隆

`git checkout -b dev`创建`dev`分支并切换到`dev`
相当于：
```
git branch dev
git checkout dev
```

`git branch` 查看所有分支
`git branch <name>`创建分支
`git checkout <name>`切换分支
`git branch -d <name>`删除分支
`git branch -D <name>`强行删除分支

`git merge <name>`合并指定分支到当前分支（以`fast forward`模式合并，默认）
`git merge --no-ff -m <message> <name>`（以普通模式合并）

`git log --graph` 查看分支合并图

`git stash`暂时储藏工作现场
`git stash pop`恢复工作现场且删除stash内容
`git stash apply`恢复工作现场但不删除stash内容
`git stash drop`删除stash内容

`git remote`查看远程库信息
`git remote -v`查看远程库详细信息

`git push origin <name>`推送到远程库
`git push --set-upstream origin <name>`将本地分支关联到远程分支

`git checkout -b <name> <name>`拉取远程分支到本地
例如：`git checkout -b dev origin/dev`从远程库拉取dev分支

`git pull`抓取远程库的最新提交
`git rebase`把本地未push的分叉提交历史整理成直线

`git tag <tagname>`创建一个新标签(默认为最新的commit)
`git tag <tagname> <commit id>`给指定的commit打标签
`git tag -a <tagname> -m <message>`指定标签信息
`git show <tagname>`查看标签说明文字
`git tag`查看所有标签
`git tag -d <tagname>`删除标签
`git push origin <tagname>`推送标签到远程
`git push origin --tags`一次性推送所有标签到远程
`git push origin :refs/tags/<tagname>`从远程删除标签


### 二、基础知识
1. 当前版本是`HEAD`,上一个版本是`HEAD^`，上上一个版本是`HEAD^^`,上100个版本是`HEAD~100`
2. 多个分支时`HEAD`指向当前分支
3. `git add`是添加文件到暂存区，`git commit`是把暂存区内容提交到当前分支
4. 合并分支时以普通模式合并能看出来曾经做过合并，用`fast forward`模式不行
5. 如果另一个人在远程库提交了新内容，这时会`push`失败，需要先`git pull`再`push`，否则提交不上去

### 三、常用操作
##### 一、如果要撤销修改
1. 撤销工作区修改，用`git checkout -- <file>`
2. 撤销已添加到暂存区的修改，用`git resest HEAD <file>`
3. 撤销已提交到版本库了的修改（但是还没推到远程库），直接回退版本`git reset --hard commit_id`
##### 二、合并分支/解决冲突
`git merge <name>`合并分支到当前分支，如果有冲突，在当前分支解决后提交
例如：在`master`合并`dev`有冲突，解决冲突后在`master`提交,切换到`dev`,在`dev`合并`master`,`master`和`dev`就是相同的内容了
##### 三、新增临时bug分支
场景：`dev`分支开发到一半时需要紧急处理一个bug，先`git stash`把`dev`的内容“储藏起来”(1.否则得先把`dev`的内容提交才能切换分支2.新建的文件不能被储藏，先`add`)，然后切换到`master`新建`issue-101`分支,处理完`issue-101`的bug后切回`dev`,`git stash pop`恢复内容继续完成开发任务
##### 四、删除未合并的分支
场景：新增了一个新功能分支但还没有合并，然后这个新功能不需要了这个分支得去掉，如果直接用`git branch -d`删除会提示`error: The branch 'feature-vulcan' is not fully merged.If you are sure you want to delete it, run 'git branch -D feature-vulcan'.`,这时得用`git branch -D <name>`才能删除成功
##### 五、新增本地分支并推送到远程库
1. 新增分支`dev`;
2. 推送：`git push --set-upstream origin dev`

##### 六、从远程库拉取分支
默认情况下，从远程库克隆的仓库，只有`master`分支，其它分支需要另外拉取，例例如：`git checkout -b dev origin/dev`

##### 七、操作标签（tags）


测试emoji。。。。。