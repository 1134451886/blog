---
title: 如何正确使用BT下载
categories: 
 - 随笔
 - 笔记
tags:
  - BT
  - 日常
  - 下载
  - 网络
  - 互联网
  - 迅雷
  - bittorrent
  - qbittorrent
keywords: 'BT,下载,网络,互联网,迅雷,bittorrent,qbittorrent,bitcomet'
cover: true
img: http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.Y2Gda.UvwHrLV8RZbQVawTkQxBwFZdQksIYs7Yio9SbyYsTkw3s*iGZE1.v10FJ.y3VuoCEBS5u0e7TIJCeDck!/r.png
abbrlink: 22fd
date: 2020-02-26 11:53:31
coverImg: http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.b1C7ApFzvhYxROU9xf5JinwUGZ96jmDmTqqF5C6f4p0Q6VX0jvTgEa0FMKaPC1JLkFG8HhH*Y6R1C.zXRtMYkU!/r.png
---
本文介绍BT下载的作用和姿势
------
对于国内BT下载用户来说，想必迅雷是再熟悉不过了。事实上我一开始也是彻头彻尾的迅雷用户，当时并不了解BT网络的原理，用迅雷图方便、快捷，相较于传统的BT下载工具，迅雷有它自己的服务器，可以解决死链，坏种的问题。即使某些冷门资源没人做种的情况下，它也能提供正常下载。
![迅雷](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.dplwK8tjLZ*ZwsYj.Xxt1bTAFZc4JorlppJwqgy4GPO2drgdZ3OVAPVVKNIHqhIOxVLdt5N3uJRkAnmuKC2rvU!/r.png)
可同样，由于受到服务器的管控，迅雷并不是BT下载最理想的工具。它经常出现：~~~***敏感资源无法下载***~~~;&ensp;诸如此类的问题。

所以我换用了qbittorrent，它没有烦人的广告，没有冗余的功能，没有敏感资源问题，有的，只是最精简的BT下载。
![qbittorrent](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.Y2Gda.UvwHrLV8RZbQVawTkQxBwFZdQksIYs7Yio9SbyYsTkw3s*iGZE1.v10FJ.y3VuoCEBS5u0e7TIJCeDck!/r.png)需要注意的是，使用此类BT下载软件要配置公网IP地址，公网IP地址一般家庭宽带是动态地址，可以打电话问问运营商客服。把公网IP地址映射到本机，要进行以下操作：
![路由器管理界面](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.TZddmQJtNXOfY7iKBJjhqsoOtePXuiPb*kf28TZHtBkPZ3X7vHqbf.njD2NXhbzAX9m7jxDEJe0CpXKzIMs2RM!/r.png)这里以华为路由器为例，每个品牌的路由器管理地址或许都不一样，一般会在路由器外壳下面注明。接着找到DMZ主机，把DMZ主机设为自己电脑的IP地址
![路由器管理界面2](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.aJ9MV9Bvk4ZeFLIZwa9o.hb620JJ.Xjl1ebGvxge5.DZ0usoeVjhocTj8uPmzuAGpmwQHUDC*QJ8yo5pUBgG*c!/r.png)这个就相当于把公网IP映射到内网你电脑的IP地址上。你使用的那台电脑就能以公网IP访问互联网资源。现在你就能尽情的享受BT下载带来的好处了，在BT软件中适当增加trackers服务器能提升下载速度。打开 工具→选项
![qbittorrent](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.QybsEPs5k4FdfmrrmJe1xLgeaO5TnPyGLifJ4s9VDzS1m72h4hLkJMvtKxqsGrAfWHmzGjTSBhWUcCM6LxAxdg!/r.png)找到bittorrent 在图中标记的地方添加trackers服务器地址，并勾选“自动添加以下tracker到新的bittorrent”这里我没有勾选只是做展示
![qbittorrent](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.ST6KtmFVd2R20D5nwNl61fP.tnG4Fazy5T69yY6kL0oB0Ch5q*alXfGizp.XY56fKwmy7qY6lD.fu9rWtAUKao!/r.png)

那么到这里，本文就结束了，下期见！