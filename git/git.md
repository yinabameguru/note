# note

## git 笔记

[原文链接](https://juejin.im/post/5bd2a0d8e51d457a4e0d4fd5)

### 日志与文件状态

git reflog //查看操作记录 注：每条记录使用HEAD@{n}来标识

![git reflog](https://github.com/yinabameguru/note/blob/master/git/resources/git%20reflog.png "git reflog")

---

git show HEAD@{2} //查看索引为2的操作记录的详细信息

![git show HEAD@{2}](https://github.com/yinabameguru/note/blob/master/git/resources/git%20show%20HEAD%40%7B2%7D.png "git show HEAD@{2}")

---

git status //查看当前所处分支暂存区和工作区的文件

![git status](https://github.com/yinabameguru/note/blob/master/git/resources/git%20status.png "git status")

---

git status -s --ignored //以简介的模式查看暂存区和工作区的文件（全部显示，不执行过滤）

![git status -s --ignored](https://github.com/yinabameguru/note/blob/master/git/resources/git%20status%20-s%20--ignored.png "git status -s --ignored")

---

git status -uno //查看暂存区和工作区的***非***未跟踪状态文件

![git status -uno](https://github.com/yinabameguru/note/blob/master/git/resources/git%20status%20-uno.png "git status -uno")

---

git status -uall //查看暂存区和工作区的状态文件（递归子目录显示）

---

git log //查看本地版本库提交记录

![git log](https://github.com/yinabameguru/note/blob/master/git/resources/git%20log.png "git log")

---

git log --stat //查看本地版本库提交记录，显示每次修改文件数和行数

![git log --stat](https://github.com/yinabameguru/note/blob/master/git/resources/git%20log%20stat.png "git log --stat")

---

git log -p README.md //查看README.md的本地提交记录，显示每次修改内容

![git log -p README.md](https://github.com/yinabameguru/note/blob/master/git/resources/git%20log%20-p%20--%20README.md.png "git log -p README.md")

---

git log --grep "git" //查看注释中含有“git”的提交记录

![git log --grep "git"](https://github.com/yinabameguru/note/blob/master/git/resources/git%20log%20--grep%20%E5%8F%8C%E5%BC%95%E5%8F%B7git%E5%8F%8C%E5%BC%95%E5%8F%B7.png "git log --grep &quot;git&quot;")

---

git log --author=yinabameguru //查看本地版本库中作者为yinabameguru的提交记录

![git log --author=yinabameguru](https://github.com/yinabameguru/note/blob/master/git/resources/git%20log%20--author%3Dyinabameguru.png "git log --author=yinabameguru")

---

git log -S "note" //查看内容中包含“note”的提交记录

![git log -S "note"](https://github.com/yinabameguru/note/blob/master/git/resources/git%20log%20-S%20%E5%8F%8C%E5%BC%95%E5%8F%B7node%E5%8F%8C%E5%BC%95%E5%8F%B7.png "git log -S &quot;note&quot;")

---

git log --since=2.weeks //查看最近2周的提交记录

![git log --since=2.weeks](https://github.com/yinabameguru/note/blob/master/git/resources/git%20lof%20--since%3D2.weeks.png "git log --since=2.weeks")

---

git log --since="2 weeks 3 days 2 hours 30 minutes 59 seconds ago" // 查看2周3天2小时30分59秒以前~现在的提交记录

![git log --since="2 weeks 3 days 2 hours 30 minutes 59 seconds ago" ](https://github.com/yinabameguru/note/blob/master/git/resources/git%20log%20--since%3D%E5%8F%8C%E5%BC%95%E5%8F%B72%20weeks%203%20days%202%20hours%2030%20minutes%2059%20seconds%20ago%E5%8F%8C%E5%BC%95%E5%8F%B7.png "git log --since=&quot;2 weeks 3 days 2 hours 30 minutes 59 seconds ago&quot;")

---

git log --since="2019-07-26 00:00:00" --until "2019-07-26 23:00:00" //查看2019-07-26 00:00:00~2019-07-26 23:00:00之间的提交记录

![git log --since="2019-07-26 00:00:00" --until "2019-07-26 23:00:00"](https://github.com/yinabameguru/note/blob/master/git/resources/git%20log%20--since%3D%E5%8F%8C%E5%BC%95%E5%8F%B72019-07-26%2000%E5%86%92%E5%8F%B700%E5%86%92%E5%8F%B700%E5%8F%8C%E5%BC%95%E5%8F%B7%20--until%20%E5%8F%8C%E5%BC%95%E5%8F%B72019-07-26%2023%E5%86%92%E5%8F%B700%E5%86%92%E5%8F%B700%E5%8F%8C%E5%BC%95%E5%8F%B7.png "git log --since=&quot;2019-07-26 00:00:00&quot; --until &quot;2019-07-26 23:00:00&quot;")

git add -u . //将当前目录下（递归子目录）所有***追踪状态***的文件加入到暂存区

![git add -u .]( "git add -u .")
