[toc]
```
在第一篇目中可以学习了解了git的简单命令。
本篇介绍使用git的绝大多数用到的基础命令。
```

# 2.1 获取git仓库

```
获取git仓库的方法有两种。
a、把现有的项目获取目录导入到git中
![](static/pic/Snip20200131_5.png)
b、从服务器上克隆现有的git仓库
git clone xxxx
git clone xxxx xxxb
```

## 2.1.1 在现有的项目中初始化git仓库

```
git init
本操作会创建.git子目录。这个子目录包含了构成git仓库骨架的所有必须条件，此时还未跟踪任何文件

进行本工程的内容的跟踪
git add  文件【获取*.文件后缀】
提交
git commit -m 'commits'
```

### 2.1.2 克隆现有的仓库

```
git clone [curl] [newname]
本命令会将所有的服务器上的数据都会进行内容的肤质。
例如
git clone https://github.com/lihu1990/readgitbook.git
git clone https://github.com/lihu1990/readgitbook.git readgitbook
```

# 2.2 git仓库内容的变更

```
在git仓库中的文件存在两类状态
跟踪【tracked】、未跟踪【untracked】
在跟踪状态又分为未修改、已修改、已暂存
```

总体状态图

![](static/pic/Snip20200131_7.png)\

## 2.2.1 查看文件状态

```
git status
```
![](static/pic/Snip20200131_8.png)
## 2.2.2 跟踪新的文件

```
git add newfilename
git status
```
![](static/pic/Snip20200131_9.png)

## 2.2.3 暂存已经修改的文件

```
git commit -m '提交暂存的文件'
需要注意的是
在修改完一个文件时候，看到的是等待提交到暂存，
这个时候又进行内容的修改看到的状态是待提交和待跟踪需要在此进行git add filename
```


## 2.2.4 查看简洁的git状态信息

```yaml
git status -s
A 表示已经暂存
AM 表示未暂存已修改
?? 表示待跟踪
M 表示已修改
MM 表示已经暂存且已经修改
```
![](static/pic/Snip20200131_10.png)
## 2.2.5 忽略文件

```yaml
.gitignore
*.xml
*.log
*.apk
```

## 2.2.6 查看已暂存和未暂存的变更

```yaml
git status
git diff 
git difftool  #可视化进行区别查看
```
![](static/pic/Snip20200131_12.png)
## 2.2.7 提交变更
```yaml
git commit
```
## 2.2.8 跳过暂存区
```yaml
git commit -a -m "msg"
```
## 2.2.9 移除文件
```yaml
git rm filename
```
![](static/pic/Snip20200131_13.png)
```java
在实际的情况中我们希望某个文件不在服务器上进行跟踪(本地文件不删除，push后远程的删除)
git rm --cached filename
```
![](static/pic/Snip20200131_14.png)
![](static/pic/Snip20200131_15.png)
## 2.2.10 移动文件
```java
git mv fromFileName toFileName
此操作相当于执行如下3条命令
1、mv fromFileName toFileName
2、git rm fromFileName
3、git add toFileName
```
# 2.3查看提交历史
```java
git log
默认不加参数的情况下是针对当前的所有的提交的历史进行的展示(时间倒序)
```
![](static/pic/Snip20200131_16.png)

```java
git log -p -2
显示最近2次提交时候的差异内容
```
![](static/pic/Snip20200131_17.png)

# 2.4 撤销操作
```java
在提交时候忘记提交或写错了提交的信息，需要重新尝试提交【前提没有进行push上去】，可以使用--amend选项进行修改提交信息
git commit --amend

```

## 2.4.1 撤销已暂存的文件
```java
在实际的版本管理中，在管理工作区和暂存区的时候有时候会
git add *
导致有些文件错误提交到暂存区了，需要进行内容的撤销，如下图：
```
![](static/pic/Snip20200202_18.png)
```java
这里我错误的将a.t文件给提交到暂存区了，这个时候我想把a.t文件从暂存区移除，可以参考
git reset HEAD <file>...
因此我们按照提示
git reset HEAD a.t
如下图:
```
![](static/pic/Snip20200202_19.png)

## 2.4.2 撤销对文件的修改(危险操作，慎重使用)
```java
在实际的操作中，如果想要恢复到上个版本的状态，这个时候git status 会告诉你
执行git checkout --<file>... 进行恢复到上个版本
```
![](static/pic/Snip20200202_20.png)

# 2.5 远程仓库使用
## 2.5.1 显示远程仓库
## 2.5.2 添加远程仓库
## 2.5.3 从远程仓库拉取数据
## 2.5.4 将数据推送到远程仓库
## 2.5.5 检查远程仓库
## 2.5.6 删除和重命名远程仓库
# 2.6 标记
## 2.6.1 列举标签
## 2.6.2 创建标签
## 2.6.3 注释标签
## 2.6.4 轻量标签
## 2.6.5 补加标签
## 2.6.6 共享标签
## 2.6.7 检出标签
# 2.7 git别名
