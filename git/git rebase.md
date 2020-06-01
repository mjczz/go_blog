# git rebase 与 git merge 的使用

## 在开放分支上rebase主分支

### 提交b2修改，查看提交记录

```bash
Administrator@PC-20200402XMOU MINGW64 ~/Desktop/git_rebase (b2)
$ git log --oneline
b518614 (HEAD -> b2) b2修改
68aa122 (origin/master, origin/b2) b2修改
5603033 b7分支删除文件
1e60593 (b7) b7分支删除文件
12a85c0 (b6, b5, b4) b5提交
11bcbf1 b2提交
dbe77ba b4提交
3338e86 b3提交
bbcfa3f b3
a6491a6 b2
20c27b9 master
5a47d61 (dev) 1.txt

```



### b2分支rebase master分支

```bash
Administrator@PC-20200402XMOU MINGW64 ~/Desktop/git_rebase (b2)
$ git rebase master
Successfully rebased and updated refs/heads/b2.

```



### 再查看b2分支的提交记录

```bash
Administrator@PC-20200402XMOU MINGW64 ~/Desktop/git_rebase (b2)
$ git log --oneline
4f9cab4 (HEAD -> b2) b2修改
9025bce (master, b3) b3修改  
68aa122 (origin/master, origin/b2) b2修改
5603033 b7分支删除文件
1e60593 (b7) b7分支删除文件
12a85c0 (b6, b5, b4) b5提交
11bcbf1 b2提交
dbe77ba b4提交
3338e86 b3提交
bbcfa3f b3
a6491a6 b2
20c27b9 master
5a47d61 (dev) 1.txt

```

注意到master上的b3修改插入到了b2之前，b2的修改被排在了最后，也就是最终b2又重新基于master分支的代码。



##  最后在master上merge开放分支，切记merge

```bash
git merge b2
```

