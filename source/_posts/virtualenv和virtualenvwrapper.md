---
title: virtualenv和virtualenvwrapper
date: 2016-12-13 00:41:47
categories:
- Tools
tags:
- virtualenv
- python
---

# virtualenv和virtualenvwrapper

## virtualenv

virtualenv 就是虚拟且独立的 Python 环境

## virtualenvwrapper

virtualenvwrapper 是 virtualenv 的扩展工具，提供了一系列命令行命令，</br>
可以方便地创建、删除、复制、切换不同的虚拟环境。

## 安装

```bash
pip install virtualenv
pip install virtualenvwrapper
```
安装 virtualenvwrapper 后需要设置环境变量，添加以下到 `.zshrc` 中

```bash
if [ -f /usr/local/bin/virtualenvwrapper.sh ]; then
   export WORKON_HOME=$HOME/.virtualenvs 
   source /usr/local/bin/virtualenvwrapper.sh
fi
```

然后执行 `source ~/.zshrc`


## 命令

```bash
mkvirtualenv # 创建虚拟环境

lsvirtualenv -b # 列出虚拟环境

workon [虚拟环境名称] # 切换虚拟环境

lssitepackages # 查看环境里安装了哪些包

cdvirtualenv [子目录名] # 进入当前环境的目录

cpvirtualenv [source] [dest] # 复制虚拟环境

deactivate # 退出虚拟环境

rmvirtualenv [虚拟环境名称] # 删除虚拟环境
```

</br>
>参考文章: [Python 开发必备神器 - virtualenv](http://codingpy.com/article/virtualenv-must-have-tool-for-python-development/)
