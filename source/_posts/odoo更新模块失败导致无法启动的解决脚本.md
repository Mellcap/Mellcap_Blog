---
title: odoo更新模块失败导致无法启动的解决脚本
date: 2016-01-24 13:33:23
categories:
- odoo
tags:
- odoo
- bug

---

# 脚本
```bash
select DISTINCT STATE from ir_module_module;

update ir_module_module set state='installed' where state='to upgrade';
```
# 报错
odoo更新模块时报错偶尔会引起Server无法启动，解决办法就是在数据库中运行改脚本即可。

## 例子
更新模块时XML中写入了Model中未定义的字段"write_date"，更新模块时报错如图  
![报错](http://7xqfjn.com1.z0.glb.clouddn.com/2016%3A01%3A24%3Aodoo%E6%9B%B4%E6%96%B0%E6%A8%A1%E5%9D%97%E6%8A%A5%E9%94%991.png)  
重启时500，无法启动  
```bash
Internal Server Error

The server encountered an internal error and was unable to complete your request. Either the server is overloaded or there is an error in the application.
```
此时，进入数据库，运行上面给的脚本，重启后即可进入。
