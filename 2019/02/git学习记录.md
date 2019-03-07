# git学习记录

## 快速上手
  - git clone
  - git status
  - git log
  - git log -p
  - git log -stat 
  - git show "commit_number"
  - git diff --staged
  - git add
  - git commit
  - git push
  - git pull
  - git branch "name"
  - git branch -d "branch name"
  - git checkout "branch name"
  - git checkout -b "name"
  - git merge "branch name"
  - git merge --abort 

查看历史中的多个 commit：log
查看详细改动： git log -p
查看大致改动：git log --stat
查看具体某个 commit：show
要看最新 commit ，直接输入 git show ；要看指定 commit ，输入 git show commit的引用或SHA-1
如果还要指定文件，在 git show 的最后加上文件名
查看未提交的内容：diff
查看暂存区和上一条 commit 的区别：git diff --staged（或 --cached）
查看工作目录和暂存区的区别：git diff 不加选项参数
查看工作目录和上一条 commit 的区别：git diff HEAD_