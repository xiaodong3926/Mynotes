## Git——一个版本控制系统
#### 了解Git
![[repo.png]]
当你建立了一个Git版本库，那么存放.git（也就是版本库）的文件夹就被称为工作区，.git内部有一个暂存区，一个叫做master的分支，一个HEAD指针能够指向分支中不同版本的文件（现在叫做main分支）
#### 初始化Git

在安装完git之后，第一步是登陆
```git
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

然后你要选择一个文件夹，作为版本库（仓库），在此目录下使用`git init`来创建一个全新的版本库（会在此文件夹下生成.git文件夹）

## 版本库的相关操作

#### 添加文件到版本库

如果你有一个readme.txt文件，你需要先用`git add readme.txt`来把文件添加到仓库（此时会在stage暂存区），然后使用`git commit -m "This is a new"` 正式提交到master分支，-m后面跟的是你对本次提交的消息commit可以一次提交很多文件，因此你可以多add几个文件（使用git add .可以将工作区所有文件都添加到暂存区）

#### 仓库状态

`git status`这个命令告诉你当前仓库的状态以及已经被添加的文件

`git diff`则是告诉你上一次修改了什么内容

`git log`可以显示仓库拥有者与文件版本的时间与添加的消息

#### 版本回退

使用`git reset --hard HEAD^`命令

此命令有三个参数，--hard表示回到文件修改之前（上一个版本的文件被提交的状态），       --soft是回到上次提交之前，--mixed是回到上次被添加之前

HEAD^表示上一个版本，HEAD是当前版本，HEAD^^是上上个版本，也可以用HEAD～n表示（n代表回退到n个版本之前）

如果想回到当前版本，只需要用`git reset --hard 当前版本的版本号`就行
可以使用`git reflog`查看版本号，它会记录你的每一次命令

`git checkout -- readme.txt` 此命令起到的作用是撤销修改，当你不小心在readme文件中添加了错误信息，此时有两种情况：
- 如果你还没有把文件添加到暂存区此命令会让文件回到版本库中的状态
- 当你已经把文件添加到暂存区又在工作区进行了修改，此时这个命令会让文件回到暂存区中的状态
#### 删除

使用`git rm read.txt`命令可以将工作区、版本库中的该文件删除
而使用`git rm --cache`命令能够删除版本库中文件，工作区的文件得以保留
（git rm删除只是当前分支的文件，文件的历史记录仍然保留在版本库中，其他分支也不受影响）
使用`git checkout --readme.txt`可以将工作区的文件恢复
#### 使用远程仓库

````
git remote add origin + 你的仓库链接
````
使用此命令连接你的远程仓库（origin是远程仓库的默认名称）
`git remove -v`会显示你当前的远程地址


```
git push -u origin main
```
这个命令能把当前分支推送到远程，由于远程库是空的，我们第一次推送`master`分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的main分支关联起来，在以后的推送或者拉取时就可以简化命令

````
git clone + 远程仓库链接
````
可以将远程仓库的内容拉取到本地
#### .gitignore文件
当你的工作区里有很多文件想要一次全部推送但又不想把无关紧要的文件也推上去时，可以使用此文件,比如说
```git
*    #忽略全部文件
/notes    #忽略notes文件夹
!books    #取消忽略books文件夹
```
也就是说`/`表示根目录,此文件在add的时候起作用