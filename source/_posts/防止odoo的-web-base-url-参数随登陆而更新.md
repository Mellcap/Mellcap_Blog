---
title: "防止odoo的'web.base.url'参数随登陆而更新"
date: 2016-11-09 14:23:33
categories:
- odoo
tags:
- odoo
---

# 问题
最近一直遇到这样的问题：

以Admin的身份登陆odoo后台时，如果带端口访问时，会自动更新`系统参数`中的`web.base.url`的值。
例如我以`www.mellcap.com:48369`登陆后台时，`web.base.url`的值会从`http://www.mellcap.com`改为`http://www.mellcap.com:48369`

# 解决方法
###### 在`系统参数`中增加`web.base.url.freeze`字段并赋值为`1`(也可以是其他非空参数)就可以解决该问题了。

## 原理
在`odoo/openerp/addons/base/res/res_users.py`中有这样一段函数：

```python
    def authenticate(self, db, login, password, user_agent_env):
        """Verifies and returns the user ID corresponding to the given
          ``login`` and ``password`` combination, or False if there was
          no matching user.

           :param str db: the database on which user is trying to authenticate
           :param str login: username
           :param str password: user password
           :param dict user_agent_env: environment dictionary describing any
               relevant environment attributes
        """
        uid = self._login(db, login, password)
        if uid == openerp.SUPERUSER_ID:
            # Successfully logged in as admin!
            # Attempt to guess the web base url...
            if user_agent_env and user_agent_env.get('base_location'):
                cr = self.pool.cursor()
                try:
                    base = user_agent_env['base_location']
                    ICP = self.pool['ir.config_parameter']
                    if not ICP.get_param(cr, uid, 'web.base.url.freeze'):
                        ICP.set_param(cr, uid, 'web.base.url', base)
                    cr.commit()
                except Exception:
                    _logger.exception("Failed to update web.base.url configuration parameter")
                finally:
                    cr.close()
        return uid
```

精华在这里：

```python
if not ICP.get_param(cr, uid, 'web.base.url.freeze'):
    ICP.set_param(cr, uid, 'web.base.url', base)
cr.commit()

```
如果有`web.base.url.freeze`那么就不更新`web.base.url`了。
