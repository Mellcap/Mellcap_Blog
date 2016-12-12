---
title: pip
date: 2016-12-13 00:12:02
categories:
- Tools
tags:
- pip
- python
---

# pip 笔记
最近想整理下手头的工具，一点点写到博客里，方便以后查找。

## pip 安装
[PIP Install](https://pip.pypa.io/en/latest/installing/)

## pip 源
目前使用阿里的源，速度很赞。

运行 emacs ~/.pip/pip.conf 或者 vi ~/.pip/pip.conf
写入以下内容并保存：

```bash
[global]
trusted-host =  mirrors.aliyun.com
index-url = http://mirrors.aliyun.com/pypi/simple
```

## 更新包

pip install -U <Package>
