---
title: npm
date: 2016-12-13 00:34:53
categories:
- Tools
tags:
- npm
---

# npm 笔记

## npm 源

目前使用阿里的源

[淘宝npm镜像](https://npm.taobao.org/)

在 `.zshrc` 中加入
```bash
alias cnpm="npm --registry=https://registry.npm.taobao.org \
--cache=$HOME/.npm/.cache/cnpm \
--disturl=https://npm.taobao.org/dist \
--userconfig=$HOME/.cnpmrc"
```
以后使用 `cnpm` 代替 `npm` 就OK了

如果使用 `sudo` 不识别 `cnpm` ，在后面加上源就好了，
如：
```bash
sudo npm install <Package> --registry=https://registry.npm.taobao.org
```
