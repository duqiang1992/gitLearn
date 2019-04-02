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

```