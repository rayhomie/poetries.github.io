---
title: Hexo接入DaoVoice实现在线聊天功能
date: 2018-11-20 18:40:08
tags: Hexo
categories: Front-End
---

> DaoVoice 可以提供在线联系的功能，我们可以借助于此在自己的站点上接入了此功能

效果

![image.png](https://upload-images.jianshu.io/upload_images/1480597-257a8e64cd4f5c3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 一、注册

> 首先需要注册一个 `DaoVoice`，点击注册 http://dashboard.daovoice.io/get-started?invite_code=7f3d6e70

注册成功后，进入后台控制台，进入到 应用设置-->安装到网站 页面，可以得到一个 `app_id`

![image.png](https://upload-images.jianshu.io/upload_images/1480597-62c546cf2cbcb1b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 二、设置

> 以 fexo 主题为例，打开 themes//layout/_partials/head.ejs 文件中添加如下代码，位置随意

```js
{% if theme.daovoice %}
  <script>
  (function(i,s,o,g,r,a,m){i["DaoVoiceObject"]=r;i[r]=i[r]||function(){(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;a.charset="utf-8";m.parentNode.insertBefore(a,m)})(window,document,"script",('https:' == document.location.protocol ? 'https:' : 'http:') + "//widget.daovoice.io/widget/0f81ff2f.js","daovoice")
  daovoice('init', {
      app_id: "{{theme.daovoice_app_id}}"
    });
  daovoice('update');
  </script>
{% endif %}
```

> 在主题配置文件 `_config.yml`，添加如下代码

```bash
# Online contact 
daovoice: true
daovoice_app_id: #这里输入前面获取的app_id
```

> 应用设置--> 聊天设置修改主题

![image.png](https://upload-images.jianshu.io/upload_images/1480597-b1960b6a1ae41a5d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

也可以绑定微信

![image.png](https://upload-images.jianshu.io/upload_images/1480597-4eb3443dde9b8704.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


