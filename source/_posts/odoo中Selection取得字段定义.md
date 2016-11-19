---
title: odoo中Selection取得字段定义
date: 2016-01-27 16:09:25
categories:
- odoo
tags:
- odoo
- Selection

---
# 定义  
模型为:  `res.medical.doctor`
```python
gender = fields.Selection([(0, u'女'), (1, u'男')], u'性别',  select=True)
```
# 脚本
```python
req.env['res.medical.doctor']._columns['gender'].selection

>>> [(0, u'女'), (1, u'男')]

dict(req.env['res.medical.doctor']._columns['gender'].selection)

>>> {0: u'女', 1: u'男'}
```

这样就可以通过dict的`get(value)`来拿到对应的字段定义了。

**需要注意的是：**  

gender如果不是定义在res.medical.doctor中，比如是继承的，会导致报错。  

所以要提前判断一下  

```python
if req.env['res.medical.doctor']._columns.get('gender')
```


# 扩展

## dict通过value拿到key  

```python
[k for k, v in field_dic.items() if v==value]
```
需要注意的是key是唯一的，而value是可以重复的，所以得到的是一个**列表**。
