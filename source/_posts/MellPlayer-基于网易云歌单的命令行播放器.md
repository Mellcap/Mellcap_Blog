---
title: 'MellPlayer, 基于网易云歌单的命令行播放器'
date: 2017-03-11 08:49:46
categories:
 - MellPlayer
tags:
 - MellPlayer
---
# MellPlayer

## 前言
我写代码时非常喜欢听音乐，最近在网易云歌单中听到了许多入耳惊艳的歌，觉得非常不错。但是歌单的随机播放以及快速切换是个软肋，于是开发了MellPlayer，可以按照分类随机听歌，实现了歌单间的快速切换，希望大家能够喜欢。

{% asset_img mellplayer_tutorial.gif %}

## 开发理念
MellPlayer的初版刚刚发布，还有许许多多需要改进的地方，非常希望能有志同道合的朋友Fork下来，一起打造越来越完美的播放器，下面就说下我的开发理念：

>MellPlayer是一款命令行播放器，主要是为了实现根据心情随机听歌，并且能够快速进行歌单间的切换，简约流畅，我希望在此基础上谨慎添加小而美的功能。并不想引入过多繁琐的功能，添加一大堆的快捷键，将简洁的东西繁琐化是违背我的初衷的。


## 关于项目
项目地址：[MellPlayer](https://github.com/Mellcap/MellPlayer)
项目基于python3开发，依赖mpv。还有很多地方需要优化改进，大家发现什么问题可以给我提Issue，当然非常欢迎有兴趣的朋友加入，一起打造我们喜欢的播放器。
既然看到这儿了，就来 [Star](https://github.com/Mellcap/MellPlayer) 一下， 互相 [Follow](https://github.com/Mellcap) 一下吧哈哈！！！

### 支持
OSX & Linux (Linux未经过测试)

### 安装
通过 [pip3](https://pip.pypa.io/en/stable/) 安装
```bash
[sudo] pip3 install MellPlayer
```

### Mac OSX 安装依赖
通过 [Homebrew](https://brew.sh/) 安装 mpv
```bash
brew install mpv
```

### 升级
通过 pip3 升级
```bash
[sudo] pip3 install MellPlayer --upgrade
```

### 使用
在命令行直接输入mellplayer即可享受：
```bash
mellplayer
```

### 快捷键
```

 操作
 [j]     [Next Line]         --->  下
 [k]     [Prev Line]         --->  上
 [q]     [Quit]              --->  退出

 音乐
 [space] [Start/Pause]       --->  播放／暂停
 [n]     [Next Song]         --->  下一曲
 [p]     [Prev Song]         --->  上一曲
 [f]     [Forward Playlist]  --->  下个歌单
 [b]     [Backward Playlist] --->  上个歌单

 音量
 [-]     [Reduce Volume]     --->  减小音量
 [=]     [Increase Volume]   --->  增加音量
 [m]     [Mute]              --->  静音

 歌词
 [l]     [Show/Hide Lyric]   --->  显示／关闭歌词

 帮助
 [h]     [Show/Hide Help]    --->  显示／关闭帮助
     
```
