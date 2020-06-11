---
layout: post
title: typora+picgo+gitee搭建图床
subtitle: 超好用的博客工具，即将开始疯狂写博客
date: 2020-06-03
authro: tomlao
header-img: https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200611130218637.png
catalog: true
tags:
- 工具
---

**前言**：又将开始一轮很兴奋地写文章之旅，主要使用工具为Typora，编写的markdown文件为纯文档，对图片以链接形式渲染进来。采用本地图片存储的方式将难以迁移、分享及在坚果云查看；采用网络图片可以保证在任何位置访问。

**工具：**

1. [Typora](https://typora.io/)：可能是最优秀的md编辑器。
2. [PicGo](https://github.com/Molunerfinn/PicGo/releases)：一个用于快速上传图片并获取图片URL链接的工具，最新版的Typora原生支持PicGo关联。
3. [Gitee](https://gitee.com/)：码云（作图床），国内优秀的代码开源平台。选择gitee主要是其在国内，访问速度比github快且稳定；免费；无需备案；[点击查看几种图床的优缺点](https://www.jianshu.com/p/ea1eb11db63f)。

### 1. 建立gitee（码云）图床

注册码云后进入主页，点击右上角的+号，新建仓库作为图床。

![image-20200603123636052](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603123636052.png)

设置图床名称。**注意：在是否开源处选择公开，才能通过网络访问到图片**。**初始化Readme将自动建立master主分支。然后创建**

![image-20200603123943410](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603123943410.png)

**申请私人令牌，用于PicGo的令牌配置**。在右上角的个人头像处点击设置，然后在左边栏点击私人令牌，生成新令牌。

![image-20200603124258524](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603124258524.png)

![image-20200603124338635](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603124338635.png)

填写令牌描述，只需勾选projects，点击提交后需要输入密码。**生成的令牌只会显示一次，注意保存好，需要填入到PicGo。**

![image-20200603124449837](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603124449837.png)

![image-20200603124613804](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603124613804.png)

### 2. PicGo安装及配置

[https://github.com/Molunerfinn/PicGo/releases](https://github.com/Molunerfinn/PicGo/releases)选择最新版下载软件，安装，留意安装路径。

![image-20200603122809723](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603122809723.png)

打开picgo

![image-20200603122905128](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603122905128.png)

点击插件设置，输入gitee并搜索，安装插件。

![image-20200603123045505](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603123045505.png)

安装完成后重启一下PicGo。点击图层设置，选择gitee。需要设置4个选项：repo为你的代码库名称，branch为代码分支，选择主分支master，token为前面申请的gitee私人令牌，path为图床在代码库中的目录，可以设为img，下面的两个选项空着，在提交时默认填入时间来标识图片名称。

![image-20200603124839115](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603124839115.png)

其中repo为之前新建的作为图床的仓库，在浏览器的url中可以看到：如tomlao/typoratuchuang

![image-20200603125014450](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603125014450.png)

**点击确认，设为默认图床。**这样关于gitee的图床设置完毕，可以到上传区上传一张图片试试，如果提交后在gitee中可以看到即成功配置。

### 3. Typora配置

接近成功配置的最后一步啦，点击设置--偏好设置--图像，并按图片一样设置即可。

![image-20200603125428750](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603125428750.png)

![image-20200603125558420](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603125558420.png)

### 4. 测试

新建一个markdown文件，测试Snipaste（超好用的截图工具）粘贴图像，拖入图像，插入图像等操作验证是否能够成功插入并转为URL图像链接。

![image-20200603125856370](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200603125856370.png)

### 5. 享受便捷的写文章体验

无论什么工具，花了多少心思配置折腾，都比不上安心读文章学习，做笔记总结，写一些感悟。再华丽的方式都比不上一篇篇积累自身心路历程的文章，这段时间需要大量学习，开始自己的新阶段。

OVER

**我是和泽同学，关注我B站，知乎，公众号，我将持续分享**

![](https://gitee.com/tomlao/typoratuchuang/raw/master/img/iPhone_51075_IMG_0390.JPG)