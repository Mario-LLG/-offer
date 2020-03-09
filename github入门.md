[TOC]

# git - 简易指南

[git 查看远程仓库的信息 以及 git fetch 和git pull 的区别](https://blog.csdn.net/TH_NUM/article/details/77847031)

## 0. [GitHub 配置ssh（Mac）](https://blog.csdn.net/qq_34115898/article/details/90438106)

如果没有配置过ssh，就需要配置，如果配置过的，直接建立新仓库，具体方法可以在这篇文章中。

主要注意一个问题，在打开id_rsa.pub文件时相对麻烦，由于该文件生成路径在隐藏文件夹中（.ssh）所以不能直接用sublime点开，也许可以用终端 ，也可以把文件复制到i个可见的文件夹中用sublime text 打开。

```
/*  -e 是用默认文件编辑器打开， 后面部分是地址*/
open -e /Users/l/.ssh/id_rsa.pub
```

![2514846-3ee74d5df5c078f1](https://tva1.sinaimg.cn/large/00831rSTgy1gcnjh8cxs4j30gw0jctbt.jpg)



## 1. 创建新仓库

- 创立新文件夹（git bash here）

- 使用==git init==创建[新的git仓库](<https://www.bootcss.com/p/git-guide/>)

- 在github页面创建一个仓库
  ![image-20200309114208141](https://tva1.sinaimg.cn/large/00831rSTgy1gcnj0atk2vj30vi0imq58.jpg)

- 如果是远端服务器上的仓库，你的命令会是这个样子：（从远程服务端下载库）
  
  ```git
  git clone git@github.com:Mario-LLG/OPA.git
  ```
  
  

![](https://raw.githubusercontent.com/Mario-LLG/saved_picture/master/20191021190940.png)

## 2. 添加与提交

- 你可以计划改动（把它们添加到缓存区），使用如下命令：
  `git add <filename>`
  `git add *`

- 这是 git 基本工作流程的第一步；使用如下命令以实际提交改动：
  `git commit -m "代码提交信息"`

## 3. 推送改动

- 你的改动现在已经在本地仓库的 **HEAD** 中了。执行如下命令以将这些改动提交到远端仓库： 可以把 *master* 换成你想要推送的任何分支。
  `git push origin master`

- 如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加：
  `git remote add origin <server>`
  
  ```
  /*username是你的github用户名，proname是该项目的名称。注意加.git尾缀。*/
  git remote add origin https://github.com/username/proname.git
  ```
  
  
  
- 如此你就能够将你的改动推送到所添加的服务器上去了

![](https://raw.githubusercontent.com/Mario-LLG/saved_picture/master/20191021191222.png)

- 要更新你的本地仓库至最新改动，执行：
  `git pull`

- 以在你的工作目录中 *获取（fetch）* 并 *合并（merge）* 远端的改动。
  要合并其他分支到你的当前分支（例如 master），执行：
  `git merge <branch>`
- 两种情况下，git 都会尝试去自动合并改动。不幸的是，自动合并并非次次都能成功，并可能导致 *冲突（conflicts）*。 这时候就需要你修改这些文件来人肉合并这些 *冲突（conflicts）* 了。改完之后，你需要执行如下命令以将它们标记为合并成功：
  `git add <filename>`
- 在合并改动之前，也可以使用如下命令查看：
  `git diff <source_branch> <target_branch>`

