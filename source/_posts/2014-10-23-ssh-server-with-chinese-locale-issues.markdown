---
layout: post
title: "使用ssh登录server后终端下显示中文乱码"
date: 2014-10-23 10:02
comments: true
categories: 
---

### 问题：

使用ssh登录server后，终端下显示中文乱码。
本地系统：ubuntu
<img src="/images/locale_problem.png" alt="locale problem">
<!-- more -->

### 查看

在命令行下用locale命令看一下，出现 Cannot set LC_CTYPE to default locale 的错误：

{% codeblock 终端中运行locale命令可以看到错误信息 lang:sh %}

$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en_US:
LC_CTYPE=zh_CN.UTF-8
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

{% endcodeblock %}

### 解决方法：

两条命令：

{% codeblock 重新生成zh_CN.UTF-8 的locale lang:sh %}

$ sudo locale-gen zh_CN.UTF-8
Generating locales...
zh_CN.UTF-8... done
Generation complete.

{% endcodeblock %}

{% codeblock 重新配置locale lang:sh %}

$ sudo dpkg-reconfigure locales
Generating locales...
en_AG.UTF-8... done
en_AU.UTF-8... done
en_BW.UTF-8... done
en_CA.UTF-8... done
en_DK.UTF-8... done
en_GB.UTF-8... done
en_HK.UTF-8... done
en_IE.UTF-8... done
en_IN.UTF-8... done
en_NG.UTF-8... done
en_NZ.UTF-8... done
en_PH.UTF-8... done
en_SG.UTF-8... done
en_US.UTF-8... done
en_ZA.UTF-8... done
en_ZM.UTF-8... done
en_ZW.UTF-8... done
zh_CN.UTF-8... up-to-date
Generation complete.

{% endcodeblock %}

### 最终效果：
<img src="/images/locale_solved.png" alt="locale solved">
