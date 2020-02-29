---
title: 达芬奇导入视频没画面，使用ffmpeg转换视频位深
categories: 随笔
tags:
 - ffmpeg
 - 视频
 - 编码
 - 达芬奇
cover: true
img: >-
  http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.U2SHy*DPrf15JXk7Luto4WZVz*K5ul5JM85ie8VoaJCo5q8vqRdA0bV6F1uWGrQnlxDfErgCEsozqEZf7bo.Bs!/r.jpg
abbrlink: a77d
date: 2020-02-24 19:11:35
keywords: 达芬奇,ffmpeg,剪辑
---
# 使用ffmpeg转换视频位深

-------------------------------
最近使用达芬奇来剪辑视频，发现10bits的h264视频无法导入，或者导入没有画面只有声音根本识别不到视频流的内容，折腾了很久才确定是10bits的关系。利用ffmpeg将视频位深从10bits降低至8bits成功导入。下面来说说如何将10bits视频转换成8bits

---

### ffmpeg里面yuv的格式定义了很多种，比如下面：

1.PIX_FMT_YUV420P9BE, ///< planar YUV 4:2:0, 13.5bpp, (1 Cr & Cb sample per 2x2 Y samples), big-endian 
2.PIX_FMT_YUV420P9LE, ///< planar YUV 4:2:0, 13.5bpp, (1 Cr & Cb sample per 2x2 Y samples), little-endian 
3.PIX_FMT_YUV420P10BE,///< planar YUV 4:2:0, 15bpp, (1 Cr & Cb sample per 2x2 Y samples), big-endian 
4.PIX_FMT_YUV420P10LE,///< planar YUV 4:2:0, 15bpp, (1 Cr & Cb sample per 2x2 Y samples), little-endian 
5.PIX_FMT_YUV422P10BE,///< planar YUV 4:2:2, 20bpp, (1 Cr & Cb sample per 2x1 Y samples), big-endian 
6.PIX_FMT_YUV422P10LE,///< planar YUV 4:2:2, 20bpp, (1 Cr & Cb sample per 2x1 Y samples), little-endian 
7.PIX_FMT_YUV444P9BE, ///< planar YUV 4:4:4, 27bpp, (1 Cr & Cb sample per 1x1 Y samples), big-endian 
8.PIX_FMT_YUV444P9LE, ///< planar YUV 4:4:4, 27bpp, (1 Cr & Cb sample per 1x1 Y samples), little-endian 
9.PIX_FMT_YUV444P10BE,///< planar YUV 4:4:4, 30bpp, (1 Cr & Cb sample per 1x1 Y samples), big-endian 
10.PIX_FMT_YUV444P10LE,///< planar YUV 4:4:4, 30bpp, (1 Cr & Cb sample per 1x1 Y samples), little-endian 
11.PIX_FMT_YUV422P9BE, ///< planar YUV 4:2:2, 18bpp, (1 Cr & Cb sample per 2x1 Y samples), big-endian 
12.PIX_FMT_YUV422P9LE, ///< planar YUV 4:2:2, 18bpp, (1 Cr & Cb sample per 2x1 Y samples), little-endian 

---

# 下面来详细说明

#### 1.打开CMD

![打开CMD](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.axKZe4yVhW.sID3TN4G9OZzCxrsqkTS.Ze9UUp3sTzzaJALIKafvEk9j4gTPtahHM7iLGFkh6qmET3u7h3fHwI!/r)

#### 2.使用查看命令

进入到视频文件所在的目录，这里我要用视频文件在E:\迅雷下载\[Liuyun&VCB-S&ANK-Raws] Kill la Kill [Hi10p_1080p]，所以在CMD中输入命令：`cd E:\迅雷下载\[Liuyun&VCB-S&ANK-Raws] Kill la Kill [Hi10p_1080p]` 回车之后：![切换CMD目录](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.XBRplTNIYOXpb9ocgo12MP3G*AiGtytdCCzQPHaEDPu.O1dieS*od2Qufb0*xuC.9Y9WAMoeJs6soK1iA5SEiM!/r)

现在可以先用ffprobe命令查看一下视频文件的信息，命令是：`ffprobe "文件名"`或者：`ffmpeg -i "文件名"`比如我要查看kill la kill.mp4的信息可以输入：`ffprobe "kill la kill.mp4"`文件名要用英文的引号括起来防止出错。一定要确保命令行所在目录与视频文件目录一致，否则会报错找不到文件。![命令行](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.QhrV70ev1To0ESRaSL8Zdyr9vCxX3UsOGhCv*8bsd1LcFbQH.Nd.A.TiT5Xl.PFcIL7wFj*Sucu41Vev9bO724!/r)

如果命令行与视频文件目录不一致的话，可以把上述命令中的文件名替换成**文件路径**，比如`E:\迅雷下载\[Liuyun&VCB-S&ANK-Raws] Kill la Kill [Hi10p_1080p]\kill la kill.mp4`![文件名替换成路径](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.Qh0LWejDLqJvbGd2ghVLMZTZ7OYahgWrfS1rLf7y1X2gs2waNvSmejT2nElHnqfYuaW*VdNqySi8D61Jx73Jl0!/r)

输入命令之后会看到这样的信息：![输入命令之后](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.bsWm3Kbs.3DCwg2ojM3K7Y3Uy37*E2r1Lbxz4ZdkRyYrbWa3DdokIv3wmy2dOQ7hpl43eg4*FoD0pIIyu*NqOA!/r)可以看到<font color=orange>Video：h264（High 10）</font>视频编解码器为h264的第10部分。<font color=orange>yuv420p10le</font>：色彩空间为<font color=orange>yuv</font>，色度抽样<font color=orange>4:2:0</font>，扫描方式：<font color=orange>p</font>：逐行扫描，位深：<font color=orange>10bits</font>，<font color=orange>le</font>：little endian，分辨率<font color=orange>1920×1080</font>，比特率<font color=orange>4745kb/s</font>，帧率<font color=orange>23.98fps</font>，音频编解码器为<font color=orange>aac</font>，封装格式<font color=orange>mp4a</font>等等……有用的信息非常多，这里就不一一列举了。

#### 3.使用命令来更改视频的位深，10bits转换至8bits。

接下来使用命令`-pix_fmt yuv *`来设置YUV格式，“*”星号代表上述列表中yuv后面所带的参数，比如：422p8be，而要转换成8bits可以直接输入yuv420p。所以命令是：`ffmpeg -i "要转换的视频文件名" -pix_fmt yuv420p "输出的文件名"`需要注意每个参数之间都要有一个空格。输完命令之后回车。

![正在转码](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.XGcpaM5ST8abcQKsljYc*DfgeLN*ZQul1nEiCCCWgZwCvyvkwyi5mi137JyB6MGyi6930.v9YljIQdljfkiU9E!/r)  ![转码完成](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.Ugszob1jSbTE*EiWXJ13EuWbjxELYdD2y9lfF.4V4n.OmN0HJR22g7eP*8xwhSvXEDLbaRYigH7eJcgsBXWQEY!/r)

现在我们再用ffprobe命令查看一下：![转码完成之后ffprobe查看](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.XP*fVnsNyXEAZuVCyWexIXNh63jrkUESZH0p.nTx4CcdDUQuOKeBImILdFwBat6gGUeOZ..c8yZ8IwB482VpO8!/r) 可以看到这里只显示yuv420p了没有了后面的10le，已经转换成功了，默认的yuv420p只有8bits。那么，到这里就结束了。

值得一提的是10bits转换8bits会损失相当一部分画质。

PS.最后经过测试发现达芬奇个人免费版相较于***studio***版本***阉割***了部分~~功能~~导致无法解码10bits、高质量h264、h265。

![达芬奇界面](http://r.photo.store.qq.com/psc?/V14RBB4W1HO62x/iXs1ae7hmJtTd.wIcSd4.U2SHy*DPrf15JXk7Luto4WZVz*K5ul5JM85ie8VoaJCo5q8vqRdA0bV6F1uWGrQnlxDfErgCEsozqEZf7bo.Bs!/r.jpg)
