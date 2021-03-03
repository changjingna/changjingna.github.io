---
title: First Blog By Hexo
date: 2021-02-18 20:56:18
tags: Hexo
categories: 建站
---
Welcome to my first blog. This blog use [Hexo](https://hexo.io/) and [GitHub](https://github.com/hexojs/hexo/issues).

参考：https://www.bilibili.com/video/BV1dt4y1Q7UE?p=1

## 搭建过程

### 本地安装
本地需要安装: Git, Node.js, Hexo.

### 安装Hexo
在E盘创建一个文件夹，用于放创建该博客的项目代码，打开命令行，进入这个文件夹下，输入命令：

```bash
npm install -g hexo-cli
```

使用命令检查是否安装成功：

``` bash
hexo -v
```

使用hexo框架创建一个项目：

```bash
hexo init myblog
cd myblog
npm install
```

myblog项目新建成功，然后用VScode打开该项目，使用命令运行项目：

```bash
hexo server

```

在浏览器输入 localhost:4000 就可以看到生成的博客了。


### 换一个好看的主题

在github中搜索 hexo theme，然后按照 most stars的顺序来查找，这里使用的是 [cactus](https://github.com/probberechts/hexo-theme-cactus)主题。
按照博主的说明，将该主题的代码复制到项目中：

```bash
git clone https://github.com/probberechts/hexo-theme-cactus.git themes/cactus
```

并在项目中配置这个主题，打开 _config.yml文件修改theme属性：
```bash
theme: cactus
```


### GitHub创建个人仓库

创建一个和自己用户名xxx相同的仓库，并且在名字后面加上 .github.io，这样就可以部署到 Github page上，并且访问地址就是  https://xxx.github.io ，分支在master分支上。

这里有两种方式：
（1）https://[username].github.io， 仓库名必须为 username.github.io，打包产物必须部署到master分支上，适合部署个人博客；
（2）https://[username].github.io/rep ，仓库名可以自定义，打包产物必须在 gh-pages 分支上，适合部署给自己的开源项目然后做Demo演示页面。

（PS:创建仓库时发现，github目前可以免费创建私有仓库啦，最多支持4人协作。）


### 将Hexo部署到GitHub

安装deploy-git：
```bash
npm install hexo-deployer-git --save
```

初始化仓库
```bash
git init
```

添加远程仓库地址
```bash
git remote add origin https://github.com/changjingna/cjn.github.io.git
```

修改项目配置 _config.yml:
```bash
deploy:
  type: git
  repo: https://github.com/changjingna/changjingna.github.io
  branch: master
```

部署代码
```bash
npm run deploy
```

在 github 的个人仓库点击"Settings"，往下滑找到 "GitHub page"，点击[地址](https://changjingna.github.io/), 查看博客是否部署成功。

## 自动化部署

1、提交源代码
创建 myblogcode 分支，将源代码提交到个人仓库：
```bash
git add .

git commit -m 'feat-init'

git push --set-upstream origin myblogcode
```
（本地创建分支myblogcode比较方便，点击 Vscode 左下角的 master，上方就会有操作提示）

2、使用github actions 实现自动化部署
（1）创建一个配置文件使用actions
创建文件夹：.github -> workflows
创建文件：deploy.yml
deploy.yml内容使用b站up主已经写好的内容。

（2）将修改过的项目代码提交到myblogcode分支上
```bash
git add .

git commit -m 'feat: add github action'

git push
```

这样每次修改项目代码后，将代码提交到myblogcode分支上，由 actions 实现代码的自动化部署。


## 在线编辑博客
一个比较巧妙的方式，通过提供一个链接到github编辑博客对应的markdown文件。







