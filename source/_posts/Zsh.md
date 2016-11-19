---
title: Zsh
date: 2016-04-01 15:55:38
categories:
- Tools
tags:
- zsh

---
# Zsh

## bash中颜色配置
mac下载了iTerm2后安装了oh-my-zsh，但是ls没有显示颜色，不好区分文件和目录。

原本bash目录是可以显示颜色的，看了`bash_profile`中的配置：
```bash
export CLICOLOR=1
```

google了一下，发现如果要在zsh中显示目录颜色，要在`.zshrc`文件中配置`LSCOLORS`:
```bash
	# LSCOLORS
	export LSCOLORS="exfxcxdxbxexexabagacad"
	alias ls='ls -G'
```
重启终端，ls就能看到目录的颜色了。
