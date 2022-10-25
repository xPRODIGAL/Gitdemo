# Gitdemo
a demo to testing with Git command


#### 1.1 Git下载全局配置

* git config -- global user.name "xr"
* git config --global user.email "..."



#### 1.2 常见命令

##### 1.2.1 远程仓库已有项目接着开发

* git clone 地址
* git add .
* git commit -m "备注"
* git pull (git fetch + git merge)
* git push



##### 1.2.2 自己搭建项目与远程

* 方案一：
  * git clone 地址
  * git add .
  * git commit -m "备注"
  * git push
* 方案二：
  * git init
  * git remote add orgin 地址
  * git fetch origin main
  * git merge --allow-unrelated-histories
  * git branch --set-upstream-to=origin/mian
  * git config push.default upstream
  * git push
* 方案三：
  * git checkout --track origin/main ->简写 git checkout main



#### 1.3 git tag

```shell
git tag v1.0.0

git tag

git tag -d v1.0.0

# push到远程仓库
git push origin v1.0.0
git push origin --tags

# 删除远程tag
git push origin -d v1.0.0
```



#### 1.4 本地分支使用

##### 1.4.1 创建并切换到新分支

```shell
git branch testing
git checkout testing

# 合并
git checkout -b testing
```



##### 1.4.2 合并分支

```shell
git merge testing
git add .
git commit -m ""
```



##### 1.4.3 查看所有分支

```shell
git branch

# 删除
git branch -d testing
```



#### 1.5 远程分支

##### 1.5.1 推送远程分支

```shell
git push origin dev

# 另外人操作
git checkout dev
```



##### 1.5.2 删除远程分支

```shell
git push origin -d dev
```



### 二、 git flow工作流

第一图:

* master: 记录主要的版本
* develop: 开发版本
* topic: 新主题



第二图:

* master: 记录主要的版本
  * tag
* hotfix: 热修复
  * merge master
  * merge develop
* develop: 开发分支
* release: 上线的分支
  * merge master
  * merge develop
* feature: 新特性



### 三、 git rebase

* 改变某一个分支base, 目的让log的历史记录更加的简洁
* ==黄金原则: 不要在主分支中使用rebase==



### 四、常见Git命令总结

基础的命令: (必须掌握)

```shell
git clone xxxxxxxx

git add .
git commit -m "xxxx"

git pull ->(git fetch + git merge)
git push
```



进阶的命令:

* main
* develop
* feature

```shell
git checkout develop
# 1.检查服务器是否有origin/develop这个分支
# 2.创建一个本地的develop分支
# 3.让本地的develop分支自动跟踪origin/develop
# 4.切换到develop分支

git add .
git commit -m ""
git pull
git push
```



高级的命令:

```shell
git tag

git checkout -b develop
git push origin develop

git merge develop

# rebase常用于将新特性feature合到main里面
git rebase main
git checkout main
git merge feature
git log --pretty=oneline --graph
```

