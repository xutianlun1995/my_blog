---
title: Typora图床教程
date: 2020-07-06 20:49:36
tags: Typora
categories: 博客
keywords: 
description: 
top_img: https://xtl-blog.oss-cn-beijing.aliyuncs.com/covers/2.jpg
cover: https://xtl-blog.oss-cn-beijing.aliyuncs.com/covers/2.jpg
---

## 图床工具 - 阿里云 之 typora图床教程



## 准备工作（一），确保typora版本为最新且下载了pig-go-core

- 确保typora的版本在0.9.86以上



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-034e71c775fb07544d6e831263c97b8f_720w.jpg)



-  打开typora，点开最上面的帮助，点击里面的检测更新，先升级一下版本，确保能用。



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-e09cbfb10a97de6776646ae4751c17fa_720w.png)



- 接着点开 最上面的文件，点倒数第二个**偏好设置**



![img](https://pic1.zhimg.com/80/v2-720f2bbed480b9af87266a117ecf631c_720w.png)



- 点击图像



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-5f0555ef2a081901a1047b82676f5502_720w.jpg)



- 按照我下面的图，进行选择。



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-2f7c965687ee0689ced4a80a608599be_720w.jpg)



-  点击下载或更新



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-7c8667baf9a9461fca921fd3ae797013_720w.jpg)



## 准备工作（二）注册阿里云账号

- 复制下面链接，访问并注册账号

```text
https://www.aliyun.com/minisite/goods?source=5176.11533457&userCode=vnk7s0ek&type=copy
```

- 点击控制台



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-3d57ad89b4c81c941913df1b1cc2463a_720w.jpg)



- 选择对象存贮Oss，并开通服务。



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-eee3f811ed9d06847d83883b6427a527_720w.jpg)

- 点击概览，然后点击创建bucket.



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-0234659f70e003bd38aac9778fd847c9_720w.jpg)



- 输入创建的信息。

![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-4664c8ef7dc6bf1b1df8259e4a57bd23_720w.jpg)

- 最好先买个资源包。



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-03a8e9ca302ee4296aca7acebee84349_720w.jpg)





![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-4ecfcf1cb548f38a7d4119ae7fc18257_720w.jpg)



好了，到这里，基础工作就全部完成了。

## 决战开始，胜利就在眼前

- 桌面上新建一个txt文本，并复制下面内容到里面。

```text
{
  "picBed": {
    "uploader": "aliyun",
    "aliyun": {
    "accessKeyId": "",
    "accessKeySecret": "",
    "bucket": "", // 存储空间名
    "area": "", // 存储区域代号
    "path": "img/", // 自定义存储路径
     "customUrl": "", // 自定义域名，注意要加 http://或者 https://
     "options": "" // 针对图片的一些后缀处理参数 PicGo 2.2.0+ PicGo-Core 1.4.0+
    }
  },
  "picgoPlugins": {}
}
```

**显然上面信息都是要通过阿里云账号获取的**，首先我们来找**accessKeyId**和**accessKeySecret**

- 鼠标悬浮在右上角头像上，并选择AccssKey管理。



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-1c55243110fb55eb95e914739f598113_720w.jpg)



- 选择继续使用AccessKey，并点击创建accessKey，将新建的txt文本对应内容替换。



![img](https://pic2.zhimg.com/80/v2-6e5afb9967bafac2f7cfb94f95e45949_720w.png)

![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-59e3153f907e1a4afe0e42ffecf96802_720w.jpg)



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-4dc7840c4fb69e6b62f17f14447a0e90_720w.jpg)



- 回到之前的oss对象存贮，点击之前创建的bucket，在点击概览。

![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-0871673f6f7848aa58bff68001e96f86_720w.jpg)



- 根据下面的图，使用自己的创建的bucket信息填充之前新建的txt。



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-d464be251ee34460ad09ea77a526d6f3_720w.jpg)



- 将自己的替换更新。



```text
主要修改：
1. bucket
2. area
3. customUrl
```



- 在这里我提供一份完整的修改后的作为参考。

![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-381e669003f5e40a3e92d5ff4f643b72_720w.jpg)



- 回到typora，依次 文件 ----> 偏好设置 -----> 图像，到下面的页面，选择打开配置文件。



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-a4ddcce15c6a245c2ebd30219ab1ae3e_720w.jpg)



- **将之前的txt文本的里面的信息，复制粘贴到配置里，并ctrl+s进行保存。**

- 我们来验证下图片上传功能，点击验证图片上传选项



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-382611f57e2c12cbd758385bb428748b_720w.jpg)



- 看到下面这样的页面，那么恭喜你，你成功了。**congratulation！！！**



![img](https://xtl-blog.oss-cn-beijing.aliyuncs.com/img/v2-502f39cc0488c33e33a4eafc9d70d0dc_720w.jpg)