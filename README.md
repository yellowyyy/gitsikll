# gitskills
### 基本操作
###### git 中分为工作区和版本库，版本库有 stage （暂存区）和 master （分支），还有一个指向 master 的 HEAD 指针。

1. 创建现有的版本库：  
`git clone ssh://user@domain.com/repo.git` （可从GitHub克隆已有项目。）
2. 创建本地版本库：  
`git init` 可将某一目录让git进行管理，目录下包含 .git 的隐藏目录，用于跟踪管理版本库，使用 `ls -ah`查看。
3. 版本控制系统只能跟踪文本文件的改动，如：txt、网页、代码等，不能跟踪二进制文件，如：图片、视频、word格式等。
4. `git add <file>` 添加文件到暂存区 stage
5. `git commit -m "更改信息"` 提交更改，将暂存区的内容提交到当前分支。
6. `git status` 可查看工作区状态、历史修改记录等。
7. `git diff` 查看修改内容。
8. `git log` 查看提交日志，可加上 ` --pretty=online` 参数，简化输出内容。
9. `git reflog` 记录每一次命令。
10. `git reset --hard commit_id/HEAD` 返回某个历史版本，HEAD指向当前版本，HEAD^ 为前一个版本。
11. `git rm `删除一个文件（记得 commit）。  
### 分支管理
1. `git branch` 查看分支。
2. `git branch <name>` 创建分支。
3. `git checkout <name>` 切换分支。
4. `git checkout -b <name>`创建并切换到该分支。
5. `git merge <name>` 合并某分支到当前分支。  
`git merge --no-ff -m "相关信息" <name> `--no-f 禁用 fast forward 模式，否则会丢失分支信息。
6. `git rebase <branch>`合并当前 HEAD 到该分支。
7. `git rebase --abort`中止合并。
6. `git branch -d <name>`删除某分支。
### 远程管理
1. `git remote -v`查看远程仓库的详细信息。
2. `git remote add <name> <url>`将远程仓库添加到本地
3. `git pull <remote> <branch>`将远程仓库拉取到本地。
4. `git push <remote> <branch>`将本地推送到远程仓库。
5. `git branch -dr <remote/branch>` 删除远程或本地分支。
6. `git push --tags` 发布标签项。
### 标签管理
1. `git tag` 查看标签
2. `git tag <name> `：切换到需要打标签的分支上，加上标签名，默认标签打在最新提交的commit-id 上。
3. `git tag <name> <commit-id> `将标签打在某个commit上（git log --graph --pretty=online --abbrev-commit 查看id）
4. `git show <tagname> `查看标签信息。
5. `git tag -a <tagname>` -m "标签信息" 可以指定标签信息。
6. `it tag -d <tagname> `删除本地标签。创建的标签都在本地，不会自动推送到远程。
7. `git push origin <tagname> `推送某个标签到远程。
8. `git push origin --tags ` 一次性推送全部尚未推送到远程的本地标签。
9. `git push origin :refs/tags/<tagname> `删除推送到远程的标签。
### bug分支处理
1. `git stash` 隐藏当前工作区状态， 当前处于工作区，但需要临时修复 bug。
2. 切换到 bug 所在分支，并创建切换一个临时分支，修复bug。
3. 修复 bug 后，切换到bug 所在分支并合并临时分支的内容，使用 --no-ff 模式合并。
4. 删除临时分支。
5. 切换到工作分支。
6. git stash pop 恢复工作区内容。
### 多人协作
1. `git push  origin <branch-name> `推送自己的修改;
2. 若推送失败，远程分支比本地更新，先用 git pull 试图合并；
3. 合并有冲突，则解决冲突，并在本地提交；
4. 再用`git push origin <branch-name>`推送
5. git pull 提示 no traking information，说明本地分支和远程分支没有创建链接关系，`git branch --set-upsteame-to <branch-name> origin/<branch-name> `创建链接。
