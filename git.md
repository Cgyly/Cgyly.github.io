获取git版本信息
`$ git --version`
当前版本：git version 2.36.1.windows.1

安装完成：要执行，名字和邮箱设置作为表识
```
$ git config --global user.name "陈广 洋"
$ git config --global user.email "1811454781@qq.com"
```
global代表：机器上所有仓库都使用这个设置

# 1.基本操作
1.初始化仓库

`$ git init`

2.把文件添加到暂存区

`$ git add 文件名`

`$ git add .`

.代表：把当前目录所有文件都添加到暂存区

*.c 当前目录所有文件以.c结尾的 ， 适用linux命令

3.文件提交到本地仓库

`$ git commit -m '版本日志信息' 

linux里面commit 之后是 ' 单引号

-m表示：填写版本日志信息， 不写-m 也会需要你填写

4.查看仓库状态

`$ git status` 

5.删除文件

  - 将文件从工作区和暂存区中删除:`$ git rm  文件名`  
  - 如果删除之前修改过并且已经放到暂存区需强制删除,在工作区和暂存区都删除
  
    `$ git rm -f 文件名`
  - 仅在跟踪清单中删除，在暂存区中删除`$ git rm --cached 文件名`

6.移动或重命名文件

  - `$ git mv 原文件名 新文件名`

  - 如果新文件名已经存在则添加参数-f `$ git mv -f 原文件名 新文件名`

7. git diff比较文件差异

- 尚未缓存的改动`$ git diff`
- 查看已缓存的改动 `$ git diff --cached`
- 查看已缓存的与未缓存的所有改动 `$ git diff HEAD`
- 显示摘要，而非整个diff:`$ git diff --stat` 

8.版本回退
  - 回退到上一个版本 `$ git reset  HEAD^`  

    HEAD^ ^^ ^^^  ~1 ~2 ~3类推

  - 回退到指定版本`$ git reset 版本号`

  - 回退文件的版本，到上一个版本 ` $ git reset HEAD^ 文件名`

# 2.提交日志

1. `$ git log ` 查看提交详细记录，有名字，邮箱事件，版本号。

2. `$ git log --oneline ` 简洁版本 每条日志只有一行

3. ` $ git blame 文件名`查看指定文件修改记录

# 3.远程操作
1.远程仓库操作
    
- 载入远程仓库 `$ git clone 远程仓库网址`
- 显示所有远程仓库 `$ git  remote -v `
- 显示单个远程仓库信息`$ git remote show 网址`
- 添加远程库` $ git remote add 本地版本库名 url` url生成的. 远程库设置别名

- origin是远程仓库的别名。
- 删除远程仓库`$ git remote rm  name `
- 修改远程仓库名`$ git remote  rename old_name new_name`


2.推送到远程库，单位是分支`$ git push 远程库别名 master`

3.拉取远程库到本地库
  远程端分支master拉取本地
  `$ git pull 远程库别名 master `
# 4.分支管理
   - 查看分支

      查看本地分支`$ git branch` 

     查看本地和远程分支```$ git branch -a`` `

     查看本地分支及提交操作：`$ git branch -v`

   - 增加分支 `$ git branch hot-fix`

   - 切换分支

     切换到指定 `$ git checkout 分支名`

     新建并切换该分支`$ git checkout -b new_branch`

   - 合并分支 和并到当前分支master
    `$ git merge  branch`
   - 删除分支 `$ git branch -d branchname`

   - 重命名分支`$ git branch -m|-M olabranch new branch` 如果newbranch已经存在需要-M强制命名

   - 推送分支 `$ git push origin branch_nama`本地分支推送到远程.

        由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来

   - 删除远程分支`$ git push origin :remote_branch`删除远程分支本地分支还保留

   - 拉取远程指定分支 并在本地创建分支

        `$ git checkout -b local_branch orgin/remote_branch `

        ### 冲突问题

        1. 本地冲突：不同分支，同一文件同一行内容，修改后，添加提交，再合并分支，出现冲突.

         解决：合并出现问题，打开冲突文件，修改内容重新添加提交。

        2. 多人协同操作冲突：俩电脑，拉取数据库，对同一文件修改内容冲突，第一个推送后，第二个推送不了

           解决：最新拉取，然后出现冲突文件，类似本地冲突，直接修改文件，重新添加，提交，推送。



