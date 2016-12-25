---
title: 关于 python 异步框架
date: 2016-12-25 10:23:04
categories:
- Mellcap's Note
tags:
- python
- note
---

# 关于 python 的异步框架
自从 python3 引入 `asyncio` 之后，python 的异步备受关注，所以也一直想找个框架来玩玩。

目前比较感兴趣的有三个:
1. `tornado` : Facebook开源的一款，现在已经非常成熟了，异步协程支持的都很好。
2. `aiohttp` : 参加PyCon时了解到的，速度上很是理想。
3. `sanic` : 看博客时了解到的，速度惊人，据说可以达到 Go 的级别。

## 选择
先占个坑，想都玩儿一下再来评价一下三个框架的优劣。
