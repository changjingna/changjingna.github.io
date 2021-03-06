---
title: Hexo建站系列-第五篇
date: 2021-03-06 10:49:12
tags: Hexo
categories: 建站
---
小站新添加了标签页、分类页、搜索框、不蒜子统计、音乐播放器，试试吧~

## 标签页
为cactus主题开启标签页。

1、使用命令生成标签页
```
hexo new page tags
```
（此时生成 source/tags/index.md）

2、在 tags/index.md里添加 type: tags

3、在导航栏里添加链接
```
    nav:
      tags: /tags/
```

4、使用
在博客页面中添加
```
    tags:
    - tag1
    - tag2
```

## 分类页
和添加标签页类似。
在对应 tags 的地方换成 categories 即可。


## 搜索页
1、npm install hexo-generator-search --save

2、hexo new page search

3、在/search/index.md添加 type: search

4、添加导航
```
    nav:
        search: /search/
```


## 不蒜子统计
1、在主题的config.yml里配置
```
    busuanzi:
        enabled: true
```

2、在layout/_partial/footer.ejs里添加脚本
```
    <% if(theme.busuanzi && theme.busuanzi.enabled){ %>
      <!--不蒜子统计-->
      <script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>
      <span id="busuanzi_container_site_pv">本站总访问量<span id="busuanzi_value_site_pv"></span>次</span>%>
      <span id="busuanzi_container_site_uv">本站访客数<span id="busuanzi_value_site_uv"></span>人</span>
    <% } %>
```

## 音乐播放器
使用hexo-tag-aplayer插件。

1、hexo new page playlist

2、在 playlist/index.md中添加 type: playlist

3、在目前所用语言zh-CN.yml文件里添加对应的中文翻译：playlist: 歌单

4、npm install --save hexo-tag-aplayer

5、在根目录下的_config.yml里添加
```
aplayer:
  meting: true
```

6、在 playlist/index.md里添加歌单信息
```
{% meting "6628821650" "netease" "playlist" "autoplay" "preload:auto" "theme:#228B22" %}
```

7、过程中遇到过的报错
[hexo-tag-aplayer] Meting support is disabled
我将 preload 由原来的 none 修改为 auto 后就好了。


## 待做中...
1、代码高亮，目前没有达到喜欢的效果。
2、文章字数 + 阅读时长统计

