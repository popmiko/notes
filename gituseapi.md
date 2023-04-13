`git add.` 提交变更代码

`git commit -m "更新备注"` 	`--amend`重写上次提交信息

`git status `查看当前仓库状态

`git log` 查看日志

`git init`初始化当前仓库

`mkdir projectname`创建目录

 查看提交历史：`git reflog`

`git branch` 如果后面跟着名字则会创建分支，但不会切换

`git checkout` 后面如果是分支名称则切换过去

git合并分支：`git merge`
当我们新建分支并做完工作之后，想要把分支提交至master，只需要切换到master仓库，并执行git merge 分支名就可以了

如我们在分支中新建了一个f.c和test.c的文件

然后在使用git checkout master切换到master

在使用git merge dev将其合并
