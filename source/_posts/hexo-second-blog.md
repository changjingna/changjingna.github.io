---
title: Hexo建站-探索原理1
date: 2021-02-19 16:05:53
tags: Hexo
categories: 建站
---

使用hexo新增一篇博客。

## npm常用命令学习

npm全称是node package manager，是随NodeJs一起安装的包管理和分发工具，它让开发者很方便的下载、安装、上传以及管理已经安装的包。

### npm install
该命令根据dependencies配置安装所有的依赖包，自动安装到开发目录的node_modules下。
通过以下选项，安装包将信息保持到项目的package.json文件中。
-S, --save安装包信息会加到dependencies(生产阶段的依赖)
```bash
npm install --save 或 npm run install -S
```
-D, --save-dev安装包信息会加到devDependencies(开发阶段的依赖)
```bash
npm install --save-dev 或 npm run install -D
```

### npm run
该命令主要是执行package.json中的脚本命令scripts的内容。

```bash
npm run deploy
```
运行package.json中的scripts: deploy,即"hexo deploy"，部署网站，
执行hexo deploy时，Hexo会将public目录中的文件和目录推送至_config.yml中指定的远端仓库和分支中，并且完全覆盖该分支下的已有内容。

## 如何理解actions做了什么
使用github actions可以实现代码的自动化部署，它的配置见  github/.workflow/deploy.yml 文件。
workflow文件的配置字段：
（1）on: 指定触发 workflow 的事件，如 git的"push"；
（2）jobs： 表示要执行的一项或多项任务，需要自定义任务的job_id，而每个任务的name则是对该任务的说明。
（3）runs-on：指定运行的虚拟环境，是必填字段；
（4）steps: 指定每个job的运行步骤。
这里用的是别人已经写好的一个[action] (JamesIves/github-pages-deploy-action)。

当我们修改源码后，将本地修改提交到远程仓库，这时候因为用了 push 命令，就会触发 github/.workflow/deploy.yml 的workflow，根据配置执行以下操作：
（1）Checkout： 获取源码
（2）Install and Build：安装和构建
（3）Deploy：部署

