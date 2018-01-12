---
layout: post
title: Linux上下行网速测试
date: 2017-7-5
categories: linux
tags: [linux]
description: 边学边记录。
---

- 下载安装pip

pip 一个管理 python 包的工具
{% highlight Perl %}
wget https://bootstrap.pypa.io/get-pip.py --no-check-certificate
python get-pip.py
pip -V
{% endhighlight %}

[speedtest官方站](https://github.com/sivel/speedtest-cli){:target="_blank"}

- 安装speedtest
{% highlight Perl %}
pip install speedtest-cli
speedtest --share
{% endhighlight %}

- 查看结果
![图片]({{ site.baseurl }}/img/post/linux-speedtest-share.png)
`--share`将测试结果上传到Speedtest.net服务器并以图形的方式展示。通过链接地址获得图形报告。
![图片]({{ site.baseurl }}/img/post/linux-speedtest.png)

