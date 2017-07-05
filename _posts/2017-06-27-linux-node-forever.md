---
layout: post
title: 使用Forever在Linux运行Node工程
date: 2016-6-26
categories: linux
tags: [linux,node]
description: 边学边记录。
---

- 下载安装Node

[http://nodejs.cn/download/](http://nodejs.cn/download/){:target="_blank"}
![图片]({{ site.baseurl }}/img/post/node-download-page.jpg)

- 解压
{% highlight Perl %}
tar -xvf node-v6.10.3-linux-x64.tar.xz
{% endhighlight %}

- 创建软链接
{% highlight Perl %}
ln -s /usr/local/node/node-v6.10.3-linux-x64/bin/node /usr/local/bin/node
ln -s /usr/local/node/node-v6.10.3-linux-x64/bin/npm /usr/local/bin/npm
{% endhighlight %}
`/usr/local/node/node-v6.10.3-linux-x64/bin`按实际目录修改

- 查看是否安装成功
{% highlight Perl %}
node -v
npm -v
{% endhighlight %}

#### nodejs一般是当成一条用户命令执行，当用户断开客户连接，应用也就停了。如何让nodejs应用当成服务，在后台执行呢？

`forever` [https://github.com/foreverjs/forever](https://github.com/foreverjs/forever){:target="_blank"}

forever的用途就是帮我们更好的管理我们node App服务，本质上就是在forever进程之下，创建一个node app的子进程。

A simple CLI tool for ensuring that a given script runs continuously (i.e. forever).

{% highlight Perl %}
#安装
npm install forever -g
#-l 指定日志路径
#-a 追加日志
forever start -l /usr/spider-web/logs/app.log -a /usr/spider-web/app.js

#查看运行中的forever进程
forever list

#结束进程
forever stopall
forever stop /usr/spider-web/app.js
forever stop Id|Uid|Pid|Index|Script
{% endhighlight %}