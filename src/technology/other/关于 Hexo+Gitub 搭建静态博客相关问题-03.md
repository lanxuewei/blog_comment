---
title: 关于 Hexo+Gitub 搭建静态博客相关问题
tags: [Hexo,博客]
categories: 技术
---

  本文主要介绍如何搭建一个简单静态的个人博客网站，也不知道从什么时候开始非常喜欢写点东西，不管是一开始的各种乱七八糟心情，还是后面的乱七八糟技术点，感觉都是自己人生中挺不错的宝贵经验，所以喜欢记录下来，夜半无人时总是翻开看看自己成长历程。

<!-- more -->

  搭建静态博客我们可以使用 Hexo+码云或者Gitub，两者都可以，但是作者选择的是码云，首先支持国产，其次Gitub有时候访问速度实在是不敢恭维。关于介绍如何搭建博客问题，这篇博客说的非常详细：

> [使用Hexo+Gitub搭建静态博客](https://z77z.oschina.io/2017/01/14/%E5%85%8D%E8%B4%B9%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2%E6%90%AD%E5%BB%BA%E6%95%99%E7%A8%8B%EF%BC%88%E8%AF%A6%E7%BB%86-%E5%9B%BE%E6%96%87%EF%BC%89--Hexo+OSChina/)

  因为作者也是照着这篇博客进行搭建的，所以这里就不把文章copy过来，这里说几个遇到的问题以及如何解决的就好了。

  

**问题1：在本地启动后一切正常，但是部署到Gitub或者码云之后，css样式丢失。**

  通过 F12 发现所有获取 css 的路径错误，我的码云项目名为 static_blog ，但是 css 都少了这一层路径，例：[https://lanxuewei.gitee.io/css/style.css](https://lanxuewei.gitee.io/static_blog/css/style.css)，加上项目路径后为：<https://lanxuewei.gitee.io/static_blog/css/style.css>。访问正常，ok，说明起始路径有问题，找到项目根目录的 _config.yml 配置文件，其中：



>  url: http://yoursite.com
>
> root: /static_blog



 将 root 修改为你项目名称，重新部署就可以了。



**问题2：使用 gittalk 作为评论系统，怎么配置，之前配置一直出现出初始化错误，或者加载错误之类的，总之就是配置项没弄好。**

  首先在 gitub 上申请账号，地址： <https://github.com/settings/developers> 

![](<http://psm763q72.bkt.clouddn.com/blog-03-pic-01.png)

  申请过程中需要填写以下几项：



>Application name（这里我填写的项目名称，即 static_blog）
>
>Homepage URL（项目访问路径，例如：http://lanxuewei.gitee.io/static_blog/）
>
>Authorization callback URL（我也是填上面项目访问路径）

  

  然后填写 gittalk 配置项



>gitalk: 
>
> \# gitub用户名
>
>owner: lanxuewei
>
>\# 存放评论的项目名，可以使用你的项目（gitub上的），也可以在gitub上新建一个
>
>repo: blog_comment
>
>\# 在上面申请完成后会有 client_id 和 client_secret，用于认证
>
>client_id: cb2v50e33bb2ds26bxxx
>
>client_secret: 8e3e3a79247b2c809c7152308xxxxxxxxxxxxxx



  其中 owner 以及 repo 我之前一直弄错，所以导致一直没办法加载成功，最后加载成功以后，需要使用自己的账号登录初始化。



**问题3：一切都完成以后，使用了一个新主题，不知道怎么定义标签以及将标签和文章进行关联。**

  这个问题当时很头疼，但其实是自己不认真，在之前那篇搭建博客文章中说的很清楚，在写博客过程中，需要在博客头加上：



>title: #文章标题
>
>date: #文章日期
>
>tags: #文章标签
>
>categories: #文章分类
>
>\---



  这里填写之后，自动会生成标签以及分类，我擦，这么简单，当时搞死老子了。

  还可以添加摘要，只要在博客头加上：



摘要：一帆风顺的自己，还是要多摔几跤才会好好走路，不然总以为上天总在眷顾。

<!-- more -->

