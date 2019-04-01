Git is a distributed version control system.
Git is free software distributed under the GPL.
版本2

### 版本回退 
```
git log //查看git版本历史 --pretty=oneline  历史几记录单行 只显示备注 时间倒叙

git reset --hard HEAD^  回退到上一版本  ^上一版  ^^上2版  HEAD~100  上100版

git reset --hard 2bca8db 回到制定版本（即使该版本比当前版本新也可以，版本号前几位即可，git自动匹配，，但是不能太短）

git relog 查看git操作命令

```