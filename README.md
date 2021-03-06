Git is a distributed version control system.
Git is free software distributed under the GPL.
版本2

### 版本回退 
```
git log //查看git版本历史 --pretty=oneline  历史几记录单行 只显示备注 时间倒叙

git reset --hard HEAD^  回退到上一版本  ^上一版  ^^上2版  HEAD~100  上100版

git reset --hard 2bca8db 回到制定版本（即使该版本比当前版本新也可以，版本号前几位即可，git自动匹配，，但是不能太短）

git relog 查看git操作命令

git checkout -- fileName  删除本地修改、当修改已提交暂存区则回到未add的状态 
其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

```

### 关联远程仓库

```
git clone xxxxxx //克隆远程仓库代码

git remote add origin git@server-name:path/repo-name.git；//本地与远程仓库关联

```

### 分支

```

git checkout -b dev

git checkout命令加上-b参数表示创建并切换，相当于以下两条命令：

$ git branch dev
$ git checkout dev


git branch 查看当前分支

git merge命令用于合并指定分支到当前分支。合并后，再查看readme的内容，就可以看到，和dev分支的最新提交是完全一样的。

注意到上面的Fast-forward信息，Git告诉我们，这次合并是“快进模式”，也就是直接把master指向dev的当前提交，所以合并速度非常快。

当然，也不是每次合并都能Fast-forward，我们后面会讲其他方式的合并。


git branch -d dev 删除dev 分支

git branch -d feature-vulcan  若此分支有代码未合并，强行才能删除

git log --graph --pretty=oneline --abbrev-commit 查看分体合并情况(单行显示)

```

### 分枝管理策略

 * 通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。

 * 如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。

```
git merge --no-ff -m "merge with no-ff" dev

本次合并要创建一个新的commit，所以加上-m参数，把commit描述写进去。
```

### 工作暂存
* 你不想提交，而是工作只进行到一半，还没法提交，预计完成还需1天时间。但是，必须在两个小时内修复该bug，怎么办？幸好，Git还提供了一个stash功能，可以把当前工作现场“储藏”起来，等以后恢复现场后继续工作：

```
git stash //Git还提供了一个stash功能，可以把当前工作现场“储藏”起来

git stash list

一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；

另一种方式是用git stash pop，恢复的同时把stash内容也删了：

你可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash，用命令：

$ git stash apply stash@{0}

```

#### 多人合作

```
git rebase  把分叉的提交历史“整理”成一条直线，看上去更直观。缺点是本地的分叉提交已经被修改过了。

```

#### 创建标签

``` 
git tag tagName //默认标签是打在最新提交的commit上的

git tag tagName commitId //再某个commit上打tag

git tag 查看tag(按字母排序，非时间)

git show <tagname> 查看标签详情

git tag -d v0.1 删除标签

git push origin <tagname>  因为创建的标签都只存储在本地，不会自动推送到远程。所以，打错的标签可以在本地安全删除。

如果要推送某个标签到远程

git push origin --tags 一次性推送全部尚未推送到远程的本地标签


要删除远程标签就麻烦一点，先从本地删除：
git tag -d v0.9
然后，从远程删除。删除命令也是push，但是格式如下
git push origin :refs/tags/v0.9

完结
```