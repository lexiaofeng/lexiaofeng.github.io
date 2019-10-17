---
layout: post
title: Git 忽略隐藏文件
tags: 基础
stickie: true
---

##关于Github上传中忽略文件的方法说明

在git的使用过程中，有很多文件是不需要被提交到版本库中的，比如我们这次提到的.DS_Store文件，这个文件在mac中是管理文件夹的位置之类的信息，所以并没有必要上传到git中，这个时候就需要用git.gitignore文件来忽略此类文件。



如果你需要忽略的文件在远端仓库中已经存在了，name你需要将远端的文件删除掉才可以。
使用命令：

` git rm --cached .DS_store`

git rm –cached 把文件.DS_Store从git的索引库中移除,但是对文件.DS_Store本身并不进行任何操作也就是说本地还是有.DS_Store文件的，但是远端却没有了

在默认情况下gitgnore文件是不存在的，所以我们
需要把这个文件新建。
*** Mac中显示隐藏文件的方法是 `command+shift+.`



首先在终端中进入Git目录，输入新建命令

` touch .gitignore`

这样就在文件中新建了一个.gitignore隐藏文件

可以使用

`ls -al`

对文件进行编辑

` vi .gitignore`

进入之后按下 i 进入编辑状态

配置语法：

以斜杠“/”开头表示目录；

以星号“*”通配多个字符；

以问号“?”通配单个字符

以方括号“[]”包含单个字符的匹配列表；

以叹号“!”表示不忽略(跟踪)匹配到的文件或目录；

此外，git 对于 .ignore 配置文件是按行从上到下进行规则匹配的，意味着如果前面的规则匹配的范围更大，则后面的规则将不会生效；

我配置的是(我只不想让.DS_Store上传，如果读者想让其他文件不上传只需要在后面添加上文件名即可)

`  Python/                                                                                                                                .DS_store  `

编辑好后退出vi模式即可
退出方法为：点击ESC,然后输入:wq命令回车进行保存。

完成后再使用git commit，git push上传提交。
在使用git status进行查看就可以了。

之后再也不用担心这个文件的冲突了



### 如果上传的项目里已经有.DS_store ，则需要吧文件里的都删除在上传提交

 ·删除项目中的所有.DS_Store。这会跳过不在项目中的 .DS_Store
1.`find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch`
将 .DS_Store 加入到 .gitignore
2.`echo .DS_Store >> ~/.gitignore`
更新项目
3.`git add --all`
4.`git commit -m '.DS_Store banished!'`·

##具体全局变量忽略.DS_Store文件

Mac OS X Finder 进入的每个目录都会有个名为` .DS_Store `的文件, 用于存储当前文件夹的一些详细的` metadata `信息，例如文件夹的排序等信息。在每次提交代码时，我们需要去忽略这类文件的提交。那怎么在` git commit `过程中忽略这种类型的文件呢？

### Git Repo 内忽略文件

可以通过在` .gitignore `文件中忽略` .DS_Store `文件.

```
## Mac OS X
.DS_Store
```



### 本地Git config

首先，通过如下命令查看现有git配置信息：

```
git config --list
```

创建` /.gitignore `文件，并在文件内添加需要全局忽略的文件名。例如忽略` .DS_Store `文件.

```
#创建 ~/.gitignore 文件
$ cd ~
$ touch .gitignore
$ vim .gitignore
```

在` .gitignore_global `文件中添加如下信息(忽略 .DS>Store 文件)：

```
# Mac OS X
.DS_Store
```

保存添加的信息，并在` ~/.gitconfig `中引入` .gitignore `。执行如下命令：

```
git config --global core.excludesfile ~/.gitignore
```

执行完毕之后，再查看下 Git 配置信息，执行如下命令:

```
core.excludesfile=/.gitignore
```

之后即不用在每个新的` Git Repo `的` .gitignore `文件中忽略` .DS_Store `了。如果是开源项目，其实自己更偏爱在每个` Git Repo `的` .gitignore `文件中也添加上需要忽略的文件文件名，