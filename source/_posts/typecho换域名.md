---
title: typecho换域名
date: 2021-03-02 04:50:00
categories: 默认分类
urlname: 50
tags:
---
<!--markdown-->备份方法如下

进入phpmyadmin
找到typecho数据库里面的typecho_options表
把里面的siteUrl值换成新的。
正常情况下，只要是修改好了数据库配置，这么操作就已经换过来了。

如果需要更换文章里面的网址，在数据库里面执行下面的语句




```php
UPDATE `typecho_contents` SET `text` = REPLACE(`text`,'旧域名地址','新域名地址');
```

