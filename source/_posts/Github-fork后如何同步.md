---
title: Github fork后如何同步
date: 2017-02-07 11:07:02
categories:
- Github
tags:
- Github
---

最近参与了一些开源项目，刚fork了个项目，想一直维护着。但是不知道如何与原项目保持同步，google了一下发现原来是这样，记录一下。

## 原项目fetch到本地，然后merge

1.配置原项目，即[上游仓库](https://help.github.com/articles/configuring-a-remote-for-a-fork/)

```bash
git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
```

2.fetch
```bash
git fetch upstream
```

3.merge
```bash
git checkout master
git merge upstream/master
```

##参考资料：
[如何同步 Github fork 出来的分支](http://jinlong.github.io/2015/10/12/syncing-a-fork/)
