---
title: Hexo如何搭建个人主题
date: 2021-02-20 22:56:21
tags: Hexo
categories: 建站
---

起初是想要修改这个特定主题的主页，将一些信息替换为自己的，尝试了一波没有成功，就想到要了解一下Hexo是怎样生成特定主题的。

## 学习笔记

### Hexo全局变量
Hexo全局变量：site, page, config, theme等
site: eg. site.data.projects //根据主题作者的使用说明，指的是在 source下建：_data/projects.json目录与文件
config: 指的是本hexo项目的_config.yml
theme: 指的是主题里的_config.yml

### ejs
ejs是一种用于生成html的模板语言，目前我们需要知道：
1.<%- %>里包含要写到页面的内容
2.<% %>里包含不需要输出的js代码

参考：
[从零开始制作Hexo主题](https://segmentfault.com/a/1190000008040387#articleHeader1)
[从零开始定制hexo主题](https://www.maintao.com/2014/hexo-theme-from-scratch/)



