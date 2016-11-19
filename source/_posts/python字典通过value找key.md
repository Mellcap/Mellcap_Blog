---
title: python字典通过value找key
date: 2016-01-26 14:30:30
categories:
- python
tags:
- python

---

# Python字典通过value找key
Python默认通过key找value，需要注意的是**value是可以重复的** 。  
```python 
dict.keys()[dict.values().index(value)]
```
通过以上方法就可以通过value拿到key
