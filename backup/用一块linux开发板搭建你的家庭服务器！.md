---
title: "用一块Linux开发板搭建你的家庭服务器！"
date: "2024-06-22"
categories: 
  - "tec"
tags: 
  - "linux"
  - "开发板"
coverImage: "code01-scaled.jpg"
---

两年前，我购置了一块香橙派开发板，使用它运行安卓系统，但是由于那个安卓系统兼容性问题，很多软件安装不上，这块板子就一直放在那里吃灰，后来由于购买的Windows迷你主机风扇突然发病整的家里像机场一样,所以便想到还有块开发板，装了个Ubuntu Server并将服务移植了过来。Linux的可玩性在开发板上比Android要高得多。下面我列出了几个我正在运行的服务

## 一、CasaOS（管理面板）

Ubuntu Server需要使用命令行操作，较为繁琐，所以我们需要一个可视化的管理面板。

> CasaOS is a community-based open source software focused on delivering simple personal cloud experience around Docker ecosystem.

可以看到CasaOS提供了一个简易的数据看板，并且提供了Docker应用一键安装功能，使用CasaOS可以很方便的管理你的HomeServer

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-1024x564.png)

CasaOS自带应用商店，只要点击安装就可以下载使用你想要的应用了

并且CasaOS还自带了一个文件管理器，支持自动挂载外置存储设备，还自带一个FilesDrop，可以在局域网中与其他设备方便安全地传输文件

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-1-1024x561.png)

CasaOS官网：[CasaOS - A simple, easy-to-use, elegant open-source personal cloud system](https://casaos.io/)

## 二、Alist（网盘聚合挂载）

之前使用Windows迷你主机时就安装了alist用来挂载网盘和移动硬盘，支持局域网所有设备访问。在开发板上我直接使用CasaOS自带的应用商店安装，alist自带数据备份恢复功能，所以很轻松地迁移过来了

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-2-1024x565.png)

搭配RaiDrive可以实现像管理自己本地电脑文件一样管理网盘中的文件（下图的容量为无法识别所以显示为7.99EB），注意新版RaiDrive有广告，请使用旧版。

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-4.png)

## 三、Navidrome（音乐服务器）

苦于网易云，QQ音乐等在线流媒体音乐平台版权之争，歌单里越来越多的歌变灰，所以搭建一个本地音乐平台是一个不错的选择。下图是Navidrome的界面

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-6-1024x561.png)

虽然看起来很简陋，但是Navidrome是一个偏向服务器的程序，这意味着有很多第三方客户端可以连接到Navidrome服务器听歌，比如这个由国人开发的音流，界面美观，支持Win，Android，Mac，Linux

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-7-1024x615.png)

不过这种音乐服务器最大的问题是数据的整理和更新比较麻烦，不过如果你动手能力强可以自己写一个脚本自动下载歌曲。

如果你的主要听歌软件是网易云，那么可以试试我自己开发的NCM Downloader：[xxynet/NCM-Downloader: A powerful NCM Downloader that supports built-in metadata 一个强大的网易云下载工具，支持内嵌元信息（歌曲名，歌手，专辑，歌曲封面）](https://github.com/xxynet/NCM-Downloader)，可以批量下载歌单中的歌曲，并且会自动添加元信息

## 四、自动备份脚本

这是我用Python写的一个脚本，用于每月自动使用FTP将远程服务器上的memos笔记数据保存到本地，备份成功后会发邮件通知我

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-8.png)

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-9-1024x392.png)

## 五、音乐播放器

是的，通过开发板的音频设备播放音乐，这样就不会占用手机或电脑的音频输出了

![image](https://raw.githubusercontent.com/xxynet/blog/main/images/images/image-10-1024x317.png)

上图的所有代码都是ChatGPT写的，目前还只是一个小Demo，功能比较鸡肋，后续完善还可以添加更多功能，如播放网盘里的音乐，直接播放网易云的歌曲等，如果你是语言学习者，还可以用这个服务不间断播放你的目标语言的音频，创造语言环境。UI方面打算美化一下，添加一个音频设备控制等

## The End

以上就是所有我正在运行的服务了，这还只是基础玩法，还有更多有趣的应用，比如HomeAssistant控制只能家居，Jellyfin媒体服务器等。还可以搭建QQ机器人，总之非常适合跑24小时运行的程序和自动化任务。

虽然将服务迁移到Linux开发板上是迫不得已之举，毕竟Win迷你主机的风扇实在是一言难尽，不过这也是一次契机逼迫我学习Linux的相关知识，以前因为Linux复杂的命令一直都是望而却步，而现在自己实践，在Linux系统上安装软件包，配置开发环境，跑起来自己的Python程序，好像也没有那么难，\[hidden type="blur"\]毕竟有ChatGPT……\[/hidden\]
