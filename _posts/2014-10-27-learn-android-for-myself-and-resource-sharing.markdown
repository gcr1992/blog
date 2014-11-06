---
layout: post
title:  我是如何自学Android，资料分享
date:   2014-10-27 22:15							
category: "Android"			
---

最近知乎上有网友问我怎么自学Android，其实说实在的，我学的也一塌糊涂，当然在学习过程也积累了一些知识，对于以前没接触过Android的朋友，或者刚入门Android 的朋友，这篇文章作为入门，那是再合适不过了，希望对刚入门Android的朋友有帮助，接下来，就不罗嗦啦。

> 本文主要有以下几个步骤：
``1.``  Java 基础；
``2.`` 搭建Android 开发环境；
``3.`` 了解Android 运行原理以及一个工程项目结构；
``4.`` 如何系统学习Android；
``5.`` 推荐一些实用的资源
``6.`` 总结

<br />
### **首先呢？当然要有Java 基础；**
---
我大学的专业就是Java，但由于没学好，刚开始学Android 的时候，挺吃力的，后来又去补Java 基础去了；
因为Android SDK 是基于Java 开发的，使用的语言是Java，如果有了Java 基础，学Android 就会事半功倍；比如在Android 中要使用到的接口，抽象类，类型转换，继承，覆盖，匿名内部类，多线程，这些都是Java 语言的，如果以前没有基础过，学Android 会很郁闷的；

当然如果你有C++ 基础，当然也可以基于NDK 开发，可以不使用Java；

**对于没有Java 基础的朋友，我推荐一些资料：**
> Mars 的Java4Android：http://yun.baidu.com/s/1dD5RRQ5
> 极客学院推出的Android 专题：http://android.jikexueyuan.com/

<br />
### 搭建环境
---
Android 开发IDE选择，有Eclipse，IntelliJ IDEA，Android Studio（基于IntelliJ IDEA 社区版开发的），Eclipse 和 Android Studio 是免费的；
对于初学者我推荐使用Eclipse，因为Eclipse 成熟，遇到问题，搜索也容易找到答案；以后可以尝试不同的IDE；

**搭建环境的步骤：***
>1. Eclipse安装；
2. Android SDK安装（Android 开发工具包）；
3. ADT安装（Eclipse 的插件，使Eclipse 能够开发Android）；
4. 创建AVD（在电脑创建一个虚拟手机）；

> 详细步骤：[Android开发之旅：环境搭建及HelloWorld](http://www.cnblogs.com/skynet/archive/2010/04/12/1709892.html)

> 在这里会有很多工具，可能刚入门的会比较模糊，可以参考：[Android 开发，各种工具](http://tikitoo.github.io/blog/2014/10/12/android-tools/)

如果最终虚拟的手机屏幕能够显示主界面，则表示成功；

<br />
### 了解Android 运行原理，一个工程的项目结构
---

- 项目结构推荐慕课网的视频教程：[Android 项目结构介绍](http://www.imooc.com/video/1442)

- [Android项目目录结构介绍](http://tonyqus.blog.51cto.com/2676222/1305405)
- [Android开发之旅：HelloWorld项目的目录结构](http://www.cnblogs.com/skynet/archive/2010/04/13/1711479.html)

<br />
### 系统学习Android
---
有了上面的学习，对Android 也有了初步的认识，接下来可以系统地学习Android 啦，网上资料也很多啦，书籍也很多，视频也很多，我觉得首先要《[官方API Guide](https://developer.android.com/guide/index.html)》；然后手上准备一本书，可以当做字典，不会可以看看；如果看官方文档，有难度，看书进度太慢，可以看视频，跟着视频学，做一下东西，有什么不会的问题，可以Google 搜索；

如果说到细的知识点，比如四大组件，UI，多媒体处理，信号连接，数据存储，我在这里就不多介绍了；主要介绍了一些学习资料；

>**官方文档**
- 官方指南：[Introduction to Android | Android Developers](https://developer.android.com/guide/index.html)

> - Android API：[Android API| Android Developers](https://developer.android.com/reference/packages.html)

> - 官方中文文档： [序言 | Google Android官方培训课程中文版(v0.5)](http://hukai.me/android-training-course-in-chinese/index.html)

> ---
**书推荐**
> - 《[Head first Android Developer]()》；

> - 《[Pro Android]()》；

>---
**视频教程**
> - [Mars——Android 开发视频教程](http://marschen.com/portal.php)

> - [黎活明——8天快速掌握Android视频](http://pan.baidu.com/s/1qWAWU52)

> - [慕课网——Android 开发视频](http://www.imooc.com/course/list)

> - [极客学院——Android开发,安卓开发教程,android教程,安卓软件开发教程,安卓开发视频教程,安卓开发环境搭建](http://android.jikexueyuan.com/)

> ---

> **博客推荐**

> - **[android开发大牛博客](http://yeungeek.com/android%E5%BC%80%E5%8F%91%E5%A4%A7%E7%89%9B%E5%8D%9A%E5%AE%A2/)** <br />

> - [hellogv的专栏 - 博客频道](http://blog.csdn.net/hellogv) <br />

> - [Android_Tutor的专栏 - 博客频道](http://blog.csdn.net/android_tutor) <br />

> - [Storm' blog](http://stormzhang.github.io/) <br />

> - [恺风（Wei）之Android专栏](http://blog.csdn.net/column/details/flowingflying02.html) <br />

> - [老罗的Android之旅 - 博客频道](http://blog.csdn.net/luoshengyang) <br />

> ---
**网站推荐**

> - [ImportNew - 专注Java & Android 技术分享](http://www.importnew.com/)

> - [Android - 博客 - 伯乐在线](http://blog.jobbole.com/category/android/)

> - [Android开发中文站关注Android，关注开发者](http://www.androidchina.net/)

<br />
### 总结
---

1. 当然Github 上有很多开源的项目，多看看源码，自己才能快速提升；《[Android开源项目分类汇总](https://github.com/Trinea/android-open-project)》，这里几乎汇总了github 上所有的开源项目，可以自己找些慢慢学；

2. 然而学习是乏味的事，坚持到最后是不易的；

3. 要善于利用搜索引擎，遇到不会的问题，要使用Google 搜索；对了，作为一个开发者，要学会自备梯子；

4. 还有学Android，要时刻关注Android 的最新动态，比如最新发布的Android 5.0 棒棒糖版，去了解他的新特性；

5. 加一些QQ 群，有不会可以问问，相互交流；

---
> 本文作者：[Tikitoo](http://weibo.com/lyf0306)
本文出处：http://www.jianshu.com/p/2ee0e74abbdf
转载请在开头注明``作者详细信息``和``本文出处``。