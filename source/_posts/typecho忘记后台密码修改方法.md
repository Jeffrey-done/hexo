---
title: typecho忘记后台密码修改方法
date: 2021-02-16 02:41:40
categories: 默认分类
urlname: 8
tags:
---
<!--markdown-->![blog_bg_12.jpg](http://jeffrey.61fk.cn/usr/uploads/2021/02/3985714413.jpg)


在此分享下利用PHPMYADMIN修改管理员密码的方法，高手表笑我，新手都需要慢慢成长嘛。

步骤1：
登录你的PHPMYADMIN账户，如果连PHPMYADMIN账户的密码都忘了请直接点屏幕右上角的XX。
打开typecho安装数据库，找typecho_users点进去在password前面打勾，选择浏览，就能看到uid1的详细信息了。
步骤2：
选择uid1然后点最前面的笔形图标“更改”，把第三行的password改为
e10adc3949ba59abbe56e057f20f883e
其他项目不要动，选择执行。这时候密码就是“123456”了。
步骤3：登录typecho后台，用你的帐号登录密码是123456然后到后台修改密码