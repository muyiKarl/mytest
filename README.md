# git学习使用
## git init
初始化一个Git仓库，使用git init命令。
#
## 添加文件到Git仓库，分两步：
1、使用命令git add \<file\>，注意，可反复多次使用，添加多个文件；<br>
2、使用命令git commit -m \<message\>，完成。<br>
  `message：提交git的注释（解释）`
## git status
此命令可以让我们时刻掌握仓库当前的状态
#
## git log
此命令显示从最近到最远的提交日志
#
## git log --pretty=oneline 
此命令显示从最近到最远的提交日志（一行显示）
#
## reset --hard HEAD^
    HEAD表示当前版本
    HEAD^ 上一个版本就是
    HEAD^^ 上上一个版本就是
    HEAD~100 往上100个版本
    git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD 时，表示最新的版本。
#
## git reset --hard \<commit id\>
指定回到未来的某个版本(git log 或者 git reflog 的时候，可以查看到id)
#
## cat name 
读取文件内容
#
## git reflog
用来记录你的每一次命令(会返回你每次提交的id)
#
## git checkout -- file 
就是让这个文件回到最近一次git commit或git add时的状态
#
## git restore  -- file 
就是让这个文件回到最近一次git commit或git add时的状态
#
## git remote add origin git@server-name:path/repo-name.git 
    要关联一个远程库(添加远程库)
    关联后，使用命令git push -u origin master第一次推送master分支的所有内容
    此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改
#
## git clone
从远程库克隆
#
## git checkout -b dev || git switch -c dev
    创建并切换到名为dev的分支
      git checkout命令加上-b参数表示创建并切换，相当于以下两条命令
        git branch dev
        git checkout dev
#
## git branch
此命令查看当前分支<br>
`git branch命令会列出所有分支，当前分支前面会标一个*号`<br>
git checkout master || git switch master<br>
`切换到master分支`
#
## git merge dev
此命令用于合并指定分支到当前分支
  dev指定分支<br>
  当前分支使用`git branch`查看
#
## git branch -d dev
删除dev分支
#
## 工作现场
#### git stash
可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作
#
#### git stash list
查看工作现场
#
#### 恢复工作现场，有两个办法
  用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除<br>
  用git stash pop，恢复的同时把stash内容也删了
#
#### 多次stash
  恢复的时候，先用git stash list查看<br>
  使用git stash apply stash@{0}恢复指定的stash
#
#### git cherry-pick \<commit\>
  复制一个特定的提交到当前分支
#
## git branch -D \<name\>
  丢弃一个没有被合并过的分支，可以通过此命令强行删除
#
## git push origin master
推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上<br>
如果要推送其他分支，比如dev，就改成：git push origin dev
#
## git checkout -b dev origin/dev
从远程仓库 把dev分支 创建到本地
#
## git branch --set-upstream-to=origin/dev dev
git pull也失败了，原因是没有指定本地dev分支与远程origin/dev分支的链接，根据提示，设置dev和origin/dev的链接<br>
然后，再`git pull`
#
## 标签管理
#### 创建标签
    git tag \<name\>
      git tag v1.0 创建一个叫’v1.0‘的标签
    git tag
      查看所有标签
    git tag v0.9 \<commit id\>
      给对应的commit id创建标签
    git show \<tagname\>
      查看标签信息
    git tag -a \<tagname\> -m \<message\>
      tagname: 标签名称
      message：对于这个标签的描述
#### 操作标签
    git tag -d \<tagname\>
      删除标签
    git push origin <tagname>
      推送一个本地标签到远程
    git push origin --tags
      推送全部未推送过的本地标签
###### 删除远程标签
      先删除本地的
        git tag -d \<tagname\>
      在从远程删除
        git push origin :refs/tags/<tagname>


























