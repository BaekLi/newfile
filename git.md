```bash
//git status命令可以让我们时刻掌握仓库当前的状态
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")


//git log命令显示从最近到最远的提交日志
$ git log
commit 1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master)
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 21:06:15 2018 +0800

    append GPL

commit e475afc93c209a690c39c13a46716e8fa000c366
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 21:03:36 2018 +0800

    add distributed

commit eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 20:59:18 2018 +0800

    wrote a readme file

```



### 步骤

1. 先把文件从github上clone

```bash
//克隆文件
$ git clone https://github.com/BaekLi/GeneExpressionScatterPlot.git
```

2. 添加文件分两步执行的：

   第一步是用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；

   第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。

```bash
//提交文件,-m后面输入的是本次提交的说明
$ git add readme.txt
$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

3. 修改文件和添加文件相似

   第一步是用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；

   第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。

```bash
//修改文件
//git diff这个命令查看不同
$ git diff readme.txt 
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.

//1.add
$ git add readme.txt
//2.commit
$ git commit -m "add distributed"
[master e475afc] add distributed
 1 file changed, 1 insertion(+), 1 deletion(-)
```

4. 删除文件

```bash
$ git rm test.txt
rm 'test.txt'

$ git commit -m "remove test.txt"
[master d46f35e] remove test.txt
 1 file changed, 1 deletion(-)
 delete mode 100644 test.txt
```

5. 本地仓库的内容推送到GitHub仓库

   > 远程库的名字就是`origin`，这是Git默认的叫法

```bash
//$ git remote add origin git@github.com:michaelliao/learngit.git
$ git remote add origin https://github.com/BaekLi/GeneExpressionScatterPlot.git
```

6. 把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支`master`推送到远程

   > 由于远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数

```bash
$ git push -u origin master
Counting objects: 20, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (15/15), done.
Writing objects: 100% (20/20), 1.64 KiB | 560.00 KiB/s, done.
Total 20 (delta 5), reused 0 (delta 0)
remote: Resolving deltas: 100% (5/5), done.
To github.com:michaelliao/learngit.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

只要本地作了提交，就可以通过命令：

```bash
$ git push origin master
```

