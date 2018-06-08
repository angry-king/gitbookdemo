### 常用命令和注释
- 常见问题：
配置过.gitignore文件，但是不生效；
因为.gitignore只能忽略那些原来没有被track的文件，如果某些文件已经纳入版本管理中，则修改.gitignore不会生效。解决办法就是先把本地缓存删除（改成未track状态），然后再提交”：
```
git rm -r --cached .
git add .
git commit -m "update .gitignore"
```
- 初始化一个代码仓库

```
git init
```
- 把文件添加到仓库
```
git add readme.txt
```
- 把文件提交到仓库
```
git commit -m "wrote a readme file"
```
> 为什么Git添加文件需要add，commit一共两步呢？因为commit可以一次提交很多文件，所以你可以多次add不同的文件
- 掌握仓库当前的状态
```
git status
```
- 查看具体修改了什么内容
```
git diff readme.txt //查看的是工作区和暂存区index的区别
git diff HEAD -- readme.txt //查看的是工作区和HEAD的区别
```
- 提交的历史记录
```
git log
git log --pretty=oneline //单行显示
```
- 回退 HEAD表示当前的版本，HEAD^表示上一个版本，HEAD-100 表示上100个版本
```
git reset --hard HEAD^
git reset --hard 3628164 //通过commit id回退
```
- 查看各个版本的commit id
```
git reflog
```
- 把工作区的代码回退和HEAD的一致
>不切换分支，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
```
git checkout -- readme.txt
```
- 代码已经提交到了缓存区，想要撤销缓存区,使缓存区的代码和最新版的HEAD一致
```
git reset HEAD readme.txt
```
---
>场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

>场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。

>场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
---
- 从版本库中删除文件
```
git rm test.txt
```
- 要关联一个远程库
```
git remote add origin git@server-name:path/repo-name.git
```
- 推送master的所有内容
```
git push -u origin master
```
- 每次本地提交之后，推送最新修改
```
git push origin master
```
- 克隆远程仓库
```
git clone *****
```
- 创建与合并分支
```
git branch  //查看分支
git branch <name> //创建分支
git checkout <name>  //切换分支
git checkout -b <name>  //创建并切换分支
git merge <name>  //合并name分支到当前分支
git branch -d <name>  //删除分支
```
- 查看某个远程仓库的详细信息
```
Git remote show [remote-name]
```
- 远程有package删除后，本地pull后，删除的文件还在,自动删除本地与远程不同步的文件
```
git clean -fd
```


