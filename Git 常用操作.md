# Git 常用操作

## 工作区/缓存区

### 1. 查看Git缓存区管理的文件：

```shell
git ls-files
```

### 2. 从Git缓存区删除文件，但保留本地文件

```shell
git rm <文件路径> --cached
```

## 远端仓库

### 1. 为本地仓库添加远程仓库地址

```shell
git remote add <远程仓库名字> <git SSH地址>
# 远程仓库名字一般为 origin，也可以自定义
```

### 2. 查看本地仓库的所有远程仓库地址

```shell
git remote -v
```

### 3. 拉取远程仓库代码

```shell
git pull <远程仓库名称> <本地分支>
# eg：git pull origin master
```

### 3-S. 当 git pull 碰到拒绝合并无关历史

```shell
git pull <远程仓库名称> <本地分支> --allow-unrelated-histories 
```

> By default, git merge command refuses to merge histories that do not share a common ancestor. This option can be used to override this safety when merging histories of two projects that started their lives independently. As that is a very rare occasion, no configuration variable to enable this by default exists and will not be added.

> 默认情况下，git合并命令拒绝合并没有共同祖先的历史。当两个项目的历史独立地开始时，这个选项可以被用来覆盖这个安全。由于这是一个非常少见的情况，因此没有默认存在的配置变量，也不会添加。
> 

### 4. 提交代码到远程仓库

```shell
# 提交本地master分支到远程origin仓库的master分支
git push origin master
```

### 4-S. 提交本地新分支代码到远程新分支

```shell
git push origin local_new_branch:remote_new_branch
```



## 组织协同

### 1. Creating a pull request

参考[new 一个 pull request](https://juejin.im/post/5b5d50bd5188251b3e646c5c#heading-21)

参考[github 官方指南](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request)

### 2. 拉取上游仓库更新

下面以 huggingface/transformers 为例：

现有本地仓库，自己的fork远程仓库（origin）（git@github.com:LiangsLi/pytorch-transformers.git），上游仓库（git@github.com:huggingface/transformers.git）

首先添加上游仓库地址（该地址不会自动添加）：

```shell
git remote add upstream git@github.com:huggingface/transformers.git
# 这里设置上游仓库名称为 upstream
```

拉取上游仓库的更新：

```shell
git fetch upstream
```

在本地master分支合并上游master分支更新：

```shell
git checkout master
git merge upstream/master
```

推送更新到fork仓库

```shell
git push origin master
```







