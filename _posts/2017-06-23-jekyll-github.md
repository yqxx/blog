---
layout: post
title: Jekyll github搭建个人博客
date: 2016-6-26
categories: jekyll
tags: [jekyll,git]
description: 边学边记录。
---

### 为什么选择它

「免费的一切」
- github光坏
- 无限流量，世界各地都有理想的访问速度
- 享受git的版本管理功能，不用担心文章遗失
- 何时何地，只要向主机提交commit，就能发布新文章

![图片]({{ site.baseurl }}/img/post/github.png)

### 阅前说明
此文主要记录了我自己在建此站点过程中遇见的一些问题和解决方案，完全是在自身能力层级范围内进行描述，有误之处望请包涵指正。

### Jekyll 是什么
- 一个生成静态网页的工具
- 不需要数据库支持
- 可以免费部署在Github上

### 开始 
以Windows为例
- 下载安装Ruby

[http://rubyinstaller.org/downloads/](http://rubyinstaller.org/downloads/){:target="_blank"}
![图片]({{ site.baseurl }}/img/post/ruby-installer.png)
注意勾上
- 安装Jekyll
{% highlight Perl %}
gem install jekyll
{% endhighlight %}
- 获取最简单 Jekyll 模板并生成静态页面并运行的例子
{% highlight Perl %}
jekyll new myblog
cd myblog
jekyll serve
{% endhighlight %}
搞定，访问看[http://localhost:4000](http://localhost:4000){:target="_blank"}
![图片]({{ site.baseurl }}/img/post/jekyll.png)

- 上传到github
以我的github为例，博客的url就是[https://yqxx.github.io/blog/](https://yqxx.github.io/blog/){:target="_blank"}

至此github搭建个人博客最简单的流程已结束。