---
title: [N1盒子] n1盒子 U盘扩容法 解决其安装armbian之后使用docker和宝塔的空间不足问题 
date: 2021-02-26 15:08:37
categories: 默认分类
urlname: 40
tags:
---
<!--markdown-->最近看到有人使用n1盒子出现空间不足的问题，刚好我也有这方面的需求的解决之后将方案整理，分享给大家。
因为我自己的动手能力也不足，所以硬改的方案就暂时不考虑，采用U盘方式扩容
具体思路是挂载U盘并将其设为开机启动，然后将大的软件都迁移到U盘，这样下来的我的主空间不超过4g

接下来详细说明
前提准备：
n1安装的是armbian，一个U盘


首先将U盘插到n1盒子上，输入 df -T 查看U盘目录，一般是在 /dev/sda1
然后将其格式化为 ext4（这是linux的文件系统格式，如果是fat32或者ntfs的类型安装宝塔的时候会出错）
格式化命令为 mkfs.ext4 /dev/sda1
等一小会儿之后将其挂载
可以新建一个目录
mkdir /mnt/disk
然后把U盘挂载到这个目录
mount /dev/sda1 /mnt/disk

之后设置为每次开机就挂载
有两种方法
第一种是编辑文件 vi /etc/fstab
加入命令
/dev/sda1       /mnt/disk               ext4   default   0       0

这种方法需要小心谨慎一些，如果出错会进不去系统
另一种方法是编辑 vi /etc/rc.local
输入命令 mount /dev/sda1 /mnt/disk

设置好之后就可以迁移大的软件了
我这里占用内存比较大的是两个软件
一个是docker，另一个是宝塔

先说docker
先暂停docker， service docker stop
之后在U盘挂载的目录新建一个文件夹
mkdir /mnt/disk/docker/
然后把docker的文件都迁移到/mnt/disk/docker/目录中，命令为：
rsync -avz /var/lib/docker/ /mnt/disk/docker/
之后编辑 /etc/docker/daemon.json 配置文件，如果没有这个文件，那么需要自己创建一个，根据上面的迁移目录，基础配置如下：
{    "data-root": "/mnt/disk/docker/"}


将容器服务启动起来
service docker start
这样子之后你在docker安装的所有东西都会安装在U盘里


接下来说宝塔的迁移，因为宝塔要在/www文件夹里运行，所以宝塔的迁移方式有一点不一样
安装过宝塔的可以先卸载了，或者 rm -rf /www 把这个www文件夹删除了，然后新建 mkdir /www/

之后在U盘里新建目录 mkdir /mnt/disk/www
用软连接的命令（相当于创建快捷方式）
ln -s 源文件 目标文件源文件在U盘里为U盘新建的目录/mnt/disk/www，目标文件为/www总的来说命令为 ln -s /mnt/disk/www /www这一步完成之后就可以直接用宝塔的安装命令了wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh && bash install.sh慢慢等待吧
这样子之后，你在宝塔里安装的所有内容php，mysql之类的或者可道云，博客网站 都会安装在U盘
一般来说这两个搞定之后，大多数的大应用都可以通过宝塔和docker安装，n1盒子本身的占用不会超过4g


[原文地址，如若侵权!请联系删除][1]


  [1]: https://www.right.com.cn/forum/thread-4066384-1-1.html