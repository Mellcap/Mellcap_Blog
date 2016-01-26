---
title: Sublime
date: 2016-01-24 10:05:45
categories:
- Tools
tags:
- Sublime

---
# Sublime
## 快捷键
[osx快捷键](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/reference/keyboard_shortcuts_osx.html)  

`command + D`: 多重选择同一单词，可以一起编辑  

`command + shift + L`: 多重选择，配合`command + ←／→`，可以对首尾快速编辑  

`command + shift + V`: 在当前缩进下粘贴代码(避免粘贴代码还要重新调缩进)  

`command + shift + J`: 选择同缩进内容  

`control + M`: 首尾括号跳转  

`control  + shift + M`: 选择首位括号间东西    

`command + P`:  
* `@` 方法
* `#` 关键字
* `:` 行号

## 插件
* 王牌必然是 [PackageControl](https://packagecontrol.io/installation)
* 其次是 [Anaconda](https://packagecontrol.io/packages/Anaconda)
* Git跟踪 [GitGutter](https://packagecontrol.io/packages/GitGutter)
* Spacegray皮肤以及BracketHighlighter(自动匹配括号)插件 [说明](https://ruby-china.org/topics/20737)
* 格式化Python [Auto​PEP8](https://packagecontrol.io/packages/AutoPEP8)
	注：`control + shift + 8` 格式化选中代码
* 智能对其 [Alignment](https://packagecontrol.io/packages/Alignment)
* 格式化HTML [HTMLBeautify](https://packagecontrol.io/packages/HTMLBeautify)

## 配置文件

	{
		"auto_complete": true,
		"auto_complete_commit_on_tab": true,
		// 在选中区域搜索
		"auto_find_in_selection": true,
		// 使光标闪动更加柔和
		"caret_style": "phase",
		"color_scheme": "Packages/Theme - Spacegray/base16-eighties.dark.tmTheme",
		// 显示空白字符
		"draw_white_space": "all",
		// 保存时自动增加文件末尾换行
		"ensure_newline_at_eof_on_save": true,
		"font_face": "Monaco",
		"font_size": 13,
		// 高亮当前行
		"highlight_line": true,
		// 高亮有修改的标签
		"highlight_modified_tabs": true,
		"ignored_packages":
		[
			"Vintage"
		],
		"rulers":
		[
			72,
			79
		],
		"tab_size": 4,
		"theme": "Spacegray Eighties.sublime-theme",
		// 使用空格代替tab
		"translate_tabs_to_spaces": true,
		// 保存时自动去除行末空白
		"trim_trailing_white_space_on_save": true
	}



