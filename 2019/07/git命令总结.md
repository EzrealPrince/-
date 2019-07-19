### 创建本地分支并切换
**git checkout -b branchName**
### 分支提交  
只会提交commits以及branch，而不会去修改head
**git push origin branchName**
### 删除branch   
hand指向的branch不能删除 大写-D强制删除
**git branch -d branchName**
### merge
从目标 commit 和当前 commit （即 HEAD 所指向的 commit）分叉的位置起，把目标 commit 的路径上的所有 commit 的内容一并应用到当前 commit，然后自动生成一个新的 commit。
**git merge branchName**
发生冲突时，会将状态置为【merge冲突待解决】的中间态，然后解决冲突 add commit，如果在发生冲突时想放弃此次merge，使用
**git merge -abort**

### log
**git log -p** 
**git show commitName**
**git diff --cached** 查看你commit将会提交什么

## commit错误
将你要修改的文件添加进暂存区然后执行
**git commit --amend**

## 偏移符号
- **^** 在commit后面添加多少个该符号，表示在该commit的基础上向上回退几个commit
- **~** 在commit的后面加上该符号以及对应的数字，表示在该commit的基础上回退对应数字的commit
- **HEAD~2 ===  HEAD^^ === HEAD^1^1 !== HEAD^2**

## rebase
**git rebase -i 目标commit**
**在编辑界面中指定需要操作的 commits 以及操作类型；**
**git add 笑声  git commit --amend**
**操作完成之后用 git rebase --continue 来继续 rebase 过程。**

## c

## 基本开发流程
git checkout -b newBranch  //创建一个新分支
git push origin newBranch  //当代码编写完成，将代码推送到远程
git checkout master  //将分支切换到master
git pull //将head指到最新
git merge newBranch  //合并你所编写的分支
git push //将合并推送到远程
git branch -d newBranch  //删除掉你开发完成的分支
git push origin -d newBranch  //删除掉远程上开发完成的分支