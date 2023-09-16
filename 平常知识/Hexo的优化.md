##### 主题更换
- 目录下配置文件`_config.yml`配置:
```
theme: hexo-theme-matery
```
##### 博客站点相关信息
```
title: 七破风的博客 # 网站标题
subtitle: '' # 网站副标题
description: '' #
keywords: # 关键字
author: Chipforn # 博客作者姓名
language: zh-CN # 博客使用的语言
timezone: '' # 时区，默认电脑时区
```
##### 代码高亮设置
- 安装hexo代码高亮插件
```
npm i -S hexo-prism-plugin
```
- 修改目录下 `_config.yml` 文件中 `highlight.enable` 的值为 `false`，并新增 `prism` 插件相关的配置：
```
highlight:
  enable: false

prism_plugin:
  mode: 'preprocess'    
  theme: 'tomorrow'
  line_number: false    
  custom_css:
```
##### 搜索功能
- 安装 hexo-generator-search 搜索插件
```
npm install hexo-generator-search --save
```
- 在目录下的 `_config.yml` 文件中，新增以下的配置项：
```
search:
  path: search.xml
  field: post
```
##### 文章字数统计插件
如果你想要在文章中显示文章字数、阅读时长信息，可以安装 hexo-wordcount插件。
```
npm i --save hexo-wordcount
```
然后只需在本主题下的 `_config.yml` 文件中，激活以下配置项即可：
```
postInfo:
  date: true # 发布日期
  update: true # 更新日期
  wordCount: true # 文章字数统计
  totalCount: true # 站点总文章字数
  min2read: true # 文章阅读时长
  readCount: true # 文章阅读次数
```
