---
title: second-blog
date: 2021-02-19 16:05:53
tags:
---

使用hexo新增一篇博客。

npm常用命令学习

npm全称是node package manager，是随NodeJs一起安装的包管理和分发工具，它让开发者很方便的下载、安装、上传以及管理已经安装的包。

1、npm install
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

2、npm run
该命令主要是执行package.json中的脚本命令scripts的内容。

```bash
npm run deploy
```
运行package.json中的scripts: deploy,即"hexo deploy"，部署网站，
执行hexo deploy时，Hexo会将public目录中的文件和目录推送至_config.yml中指定的远端仓库和分支中，并且完全覆盖该分支下的已有内容。