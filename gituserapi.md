创造
克隆现有存储库

$ git clone ssh

创建一个新的本地存储库

$ git init

当地变化
Changed files in your working directory

$ git status

Changes to tracked files

$ git diff

将所有当前更改添加到下一个提交

$ git add .

在中添加一些更改到下一次提交

$ git add -p

提交跟踪文件中的所有本地更改

$ git commit -a

提交先前进行的更改

$ git commit

更改最后一次提交

不要修改已发布的提交！

$ git commit --amend

提交历史
显示所有提交，从最新开始

$ git log

显示特定文件随时间的变化e

$ git log -p

谁更改了中的内容和时间

$ git blame

分支机构和标签
列出所有现有分支

$ git branch -av

切换HEAD分支

$ git checkout

根据您当前的HEAD创建一个新分支

$ git branch

基于远程分支创建一个新的跟踪分支

$ git checkout --track

删除本地分支

$ git branch -d

用标签标记当前提交

$ git tag

更新和发布
列出所有当前配置的遥控器

$ git remote -v

显示有关遥控器的信息

$ git remote show

添加名为的新远程存储库

$ git remote add

从下载所有更改，但不要集成到HEAD中

$ git fetch

下载更改并直接合并/集成到HEAD中

$ git pull

在远程上发布本地更改

$ git push

删除遥控器上的分支

$ git branch -dr

发布标签

$ git push --tags

合并与基础
将合并到当前HEAD中

$ git merge

将当前的HEAD重新设置到

不要重新发布已发布的提交！

$ git rebase

中止基准

$ git rebase --abort

解决冲突后继续进行基准

$ git rebase --continue

使用您配置的合并工具解决冲突

$ git mergetool

使用编辑器手动解决冲突，并（在解决之后）将文件标记为已解决

$ git add

$ git rm

撤消
丢弃工作目录中的所有本地更改

$ git reset --hard HEAD

放弃特定文件中的本地更改

$ git checkout HEAD

还原提交（通过产生具有相反更改的新提交）

$ git revert

将HEAD指针重置为上一次提交

…并丢弃此后的所有更改

$ git reset --hard

…并将所有更改保留为未分阶段的更改

$ git reset

…并保留未提交的本地更改

$ git reset --keep
