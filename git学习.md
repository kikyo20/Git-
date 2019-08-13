### 一、常用命令
初始化一个Git仓库：
`git init`

添加文件到Git仓库：
1. 使用命令`git add <file>`，注意，可反复多次使用，添加多个文件；
2. 使用命令`git commit -m <message>`，完成。

`git status`告诉你有文件被修改过,用`git diff`可以查看修改内容

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

`git check -b dev`创建`dev`分支并切换到`dev`
相当于：

```

git branch dev
git checkout dev

```

`git branch` 查看所有分支
`git branch <name>`创建分支
`git checkout <name>`切换分支
`git branch -d <name>`删除分支

`git merge <name>`合并指定分支到当前分支


### 二、基础知识
1. 当前版本是`HEAD`,上一个版本是`HEAD^`，上上一个版本是`HEAD^^`,上100个版本是`HEAD~100`
2. 多个分支时`HEAD`指向当前分支
3. `git add`是添加文件到暂存区，`git commit`是把暂存区内容提交到当前分支

### 三、基本操作
一、如果要撤销修改
1. 撤销工作区修改，用`git checkout -- <file>`
2. 撤销已添加到暂存区的修改，用`git rest HEAD <file>`
3. 撤销已提交到版本库了的修改（但是还没推到远程库），直接回退版本`git reset --hard commit_id`
二、合并分支
三、解决冲突







______________________________
Creating a new branch is quick & simple.

