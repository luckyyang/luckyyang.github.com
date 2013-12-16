---
layout: post
title: UBUNTU 12.04下解决打开txt文件乱码问题
date: 2013-01-19 21:38
comments: true
categories: Linux
---

<img src="/images/ubuntu_rain_in_baires.png" alt="ubuntu_rain_in_baires" >

前几天因为一点事不得不用下windows，然后就在里面记了点东西，之后拷贝到ubuntu后发现乱码，开始也懒得去管它，可放在那始终是个问题，而且我最近正好要用到文档里的内容，就在网上搜索了下，基本的解决方法是这样的：

<!-- more -->

> 1. 终端输入gconf-editor调出gconf-edit(前面不需要加Sudo)
> 1. 依次点开 apps->gedit-2->preferences－＞encodings 中的auto-detected
> 1. 在双击弹出对话框中加入GB18030，GBK，GB2312,然后将GB18030,GB2312移到最上

但是这个方法在我这不行，之前我用vim切换编码也试过，行不通。

怎么办呢？

试试用浏览器吧，最后解决了，我把步骤说下吧，如果你正好有和我一样的问题并且搜到了这里，你也可以试一下：

1. 将文件的后缀.txt改为.html，这样浏览器就可以按html来读了。比如你的文件名是"解决个编码问题我容易么.txt"，改为"解决个编码问题我容易么.html"。
1. vim或者别的编辑器打开并编辑文件，在文件的最顶端加入：
>     <!DOCTYPE html>
>     <html>
>       <head><meta charset="GB18030"></head>
>       <body>
>         <pre>
1. 在文件的最末尾加入：
>         </pre>
>       </body>
>     </html>
1. 用浏览器打开文件，应该就可以正常显示中文了。
1. 新建一个文件，把浏览器中的中文拷贝进去。

嘿，解决了。
