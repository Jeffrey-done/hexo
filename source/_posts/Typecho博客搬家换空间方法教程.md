---
title: Typecho博客搬家换空间方法教程
date: 2021-02-20 04:01:00
categories: 默认分类
urlname: 37
tags:
---
<!--markdown-->Typecho博客系统换主机（或空间）的步骤很简单，和WordPress 博客系统的搬家方法一样，仅需要几步即可完成，但考虑到刚第一次开博客的新手，由于没有搬家经验可能会有些困难或出现错误，所以博客吧就啰嗦一番介绍下Typecho的搬家步骤。

Typecho 博客搬家方法步骤：

备份Typecho博客数据库，由于TE没有自备数据备份功能，所以需要进入phpmyadmin进行导出备份（不会的请看[Typecho 博客数据备份教程][1]）
使用FTP（或者登陆空间控制面板）把所有的Typecho文件下载到本地（自己电脑）
在新空间创建一个新的数据库，把从phpmyadmin导出的数据备份导入新的数据库
然后修改config.inc.php的数据库信息为新的数据库信息
使用FTP（或者空间控制面板）把刚才下载到本地的Typecho文件全部上传到新空间的根目录
把域名的A记录指向更改为新空间的IP地址
等待域名解析生效，搬家完成。
提醒：如果发现打开文章出现404页面，可能是.htaccess文件没有上传，可以重新上传.htaccess文件或者登陆后台重新设置永久链接。


  [1]: http://jeffrey.61fk.cn/index.php/archives/36/