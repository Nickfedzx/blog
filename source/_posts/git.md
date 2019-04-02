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
```