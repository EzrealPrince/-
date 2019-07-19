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
发生冲突时，会将状态置为【merge冲突待解决】的中间态，然后解决冲突 add commit，如果在发生冲突时想放弃

