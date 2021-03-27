---
title: Git上传文件到指定的位置
date: 2021-03-06 05:44:04
categories: 默认分类
urlname: 53
tags:
---
<!--markdown-->思路是将整个git上的代码都clone下来，然后手动把自己的文件拉进指定文件夹，再上传上去

一.创建一个文件夹"text"来git bash

1.git init??

2.git clone [https].git

假设clone下来的文件名叫A

二.clone成功后我们打开A，将本地要上传的文件拖到指定文件夹内，然后git bash clone下来的文件A

1.git init

2.git add .? ? ? ? ? ? ? ? 注意add后面有一个空格和一个点

3.git commit -m? "提交的注释"

4.git merge?origin master? ? ? ? ? ? //注：master涉嫌歧视，现在都改为main

5.git pull origin master

6.git push [https]?master

?

大功告成
[原文链接][1]


  [1]: https://blog.csdn.net/banquet79/article/details/101077345