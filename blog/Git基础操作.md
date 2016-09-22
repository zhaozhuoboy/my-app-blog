# Git基础操作

- 本地创建 `project` 文件夹

- 进入 `project` 文件夹 `cd project`

  1.` git init ` 初始化为git仓库

  2.` git status ` 查看仓库当前状态（就是说你对哪些文件做了修改）
  
  3.`git add -A`   添加所有文件到暂存区

    还有`git add .` `git add *` 都是添加所有文件到暂存区（`git add -A` 权限最高会把删除操作都会追踪到git版本中）

  4.`git commit -m "版本留言" ` 做成一个版本

  5.在github上创建一个与本地仓库同名的空的远端仓库（不勾选readme.md）   复制仓库地址

  6.`git remote add origin + 仓库地址  ` 将远端的仓库地址添加到版本中  以后push的时候就不用每次都加 网址了。

  7.`git push -u origin master `  将本地master分支推送到远端仓库 与远端的 master 分支对应起来。

  *如果是从远端克隆下来的仓库  5 6 可省略   在commit 做成版本之后  直接  git push 推送就可以了*

  > Tip: 如果提交的仓库地址错误：
  change remote address
  `atom .git/config` 用atom 打开 .git 文件夹下的config文件 删掉配置信息里的  错误地址，再次 git remote add origin 仓库地址
----
# Git分支操作

`git branch 分支名	`	创建分支

`git checkout 分支名	`	切换分支

`git branch `			显示所有分支  带星号的是当前分支

`git merge 分支名	`	合并某分支到当前分支

`git branch -d <name> `	删除分支

`git checkout -b <name>	` 创建并切换到当前分支

`git push -u origin gh-pages `  将新的分支push到远端的分支上  要加 -u origin  分支名

*新的分支第一次 push 的时候 要指明 推送的远端地址和 分支名*
