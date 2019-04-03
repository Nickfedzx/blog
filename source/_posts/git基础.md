---
title: git基础
---

#### 在现有目录中初始化仓库
```
git init
添加内容到下一次提交中
git add *
git add LICENSE
git commit -m 'initial project version'
```
#### 克隆现有仓库
```
git clone https://github.com/libgit2/libgit2 [自定义仓库名]
```

```
已跟踪的文件有3种状态:未修改,已修改,已放入暂存区.
Unmodified, Modified, Staged
```

![使用git时文件的生命周期](https://git-scm.com/book/en/v2/images/lifecycle.png "生命周期")

#### 检查当前文件状态
```
文件状态
git status
状态简览
git status -s
查看尚未暂存的文件更新了哪些部分(工作目录中当前文件和暂存区域快照之间的差异)
git diff
查看已经暂存起来的变化
git diff --cached
```
#### 提交更新
```
提交之前一定要确认还有什么修改过的或新建的文件还没个git add过,
否则提交的时候不会记录这些还没暂存起来的变化.这些修改过的文件只保留在
本地磁盘.
git commit
每一次运行提交操作, 都是对你的项目作一次快照,以后可以回到这个状态,或者进行比较.
```
#### 跳过使用暂存区
```
git commit -a
git 自动把所有已经跟踪过的文件暂存起来一并提交,从而跳过git add
```

#### 移除文件
```
把文件从 Git 仓库中删除（亦即从暂存区域移除），但仍然希望保留在当前工作目录中。
换句话说，你想让文件保留在磁盘，但是并不想让 Git 继续跟踪。
git rm --cached <filename>
git rm log/\*.log   //删除log/目录下扩展名为.log的所有文件
```

#### 移动文件
```
git mv file_from file_to
```
#### 查看提交历史
```
git log 
git log 会按提交时间列出所有的更新，最近的更新排在最上面。 
这个命令会列出每个提交的 SHA-1 校验和、作者的名字和电子邮件地址、提交时间以及提交说明。

一个常用的选项是 -p，用来显示每次提交的内容差异。 
你也可以加上 -2 来仅显示最近两次提交
git log -p -2

查看每次提交的简略的统计信息,使用--stat
git log --stat

定制要显示的记录格式
git log --pretty=format:"%h - %an, %ar : %s"
%h  提交对象的简短哈希字串
%an 作者（author）的名字
%ar 作者修订日期，按多久以前的方式显示
%s  提交说明

添加一些ASCLL字符串来形象地展示你的分支,合并历史.
--graph
```

#### 撤消对文件的修改
```
git checkout -- <file_name>
你对那个文件做的任何修改都会消失 - 你只是拷贝了另一个文件来覆盖它。 
除非你确实清楚不想要那个文件了，否则不要使用这个命令。
```