---
layout:     post
title:      "windows环境下安装jekyll相关问题汇总"
date:       2017-12-04 20:30:00
categories: [code] 
tags:       [jekyll,error]
header-img: "img/article-bg.jpg"
---

### 错误1：执行`gem install jekyll`时证书错误。
* **错误描述**：
```
ERROR: Could not find a valid gem ‘jekyll’ (>= 0), here is why: Unable to download data from https://rubygems.org/ - SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (https://api.rubygems.org/latest_spece.4.8.gz)
```
* **分析**：关键词 certificate，与证书相关的错误
* **解决办法**：[http://blog.csdn.net/qiujuer/article/details/44620019](http://blog.csdn.net/qiujuer/article/details/44620019)

### 错误2： Yikes! It looks like you don't have redcarpet or one of its dependencies installed.
* **错误描述**：
```
Dependency Error: Yikes! It looks like you don't have redcarpet or one of its
dependencies installed. In order to use Jekyll as currently configured, you'll n
eed to install this gem. The full error message from Ruby is: 'cannot load such
file -- redcarpet' If you run into trouble, you can find helpful resources at ht
tp://jekyllrb.com/help/!
  Conversion error: Jekyll::Converters::Markdown encountered an error while conv
erting '_posts/2014-12-28-first-blog.md':
redcarpet
 ERROR: YOUR SITE COULD NOT BE BUILT:
------------------------------------
redcarpet
```
* **分析**：jekyll默认使用kramdown作为Markdown解析器，要使用redcarpet的话，需要安装，但是用gem安装后仍有该问题
* **解决办法**：`gem install pygments.rb`，另外需要将`gem 'pygments.rb'`加入到Gemfile文件中。（目前还不清楚该文件作用）

### Tips：
* ruby devkit安装后文件要保存在相应位置不能动。（见官方网站说明）
* 代码区域显示样式等与相应css样式相关，与Markdown解析器关系不大。