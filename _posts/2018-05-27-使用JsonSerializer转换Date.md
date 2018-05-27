---
layout: post
title:  "使用JsonSerializer转换Date"
date:   2018-05-27 20:00
categories: Java
tags: JsonSerializer,Java,Date
permalink: /archivers/JavaDate2Long/
---

&emsp;今天遇到了这样一种业务场景，其中返回createTime和updateTime的时间戳，

![result.png](https://upload-images.jianshu.io/upload_images/8918083-0cab08c6e32ca172.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

&emsp;结果如上，但是因为精确到微秒的原因，createTime和updateTime最后有000，但是前端并不需要精确到微秒，按照以前的思维，也就是新建一个属性一样的类，除了createTime和updateTime的类型设为Long类型，将createTime和updateTime的值除1000后赋值到新建的类，返回新建的类就行了，但是这样是十分低效而且很麻烦的行为。
&emsp;使用JsonSerializer转换Date，首先，如图

![3.png](https://upload-images.jianshu.io/upload_images/8918083-599bfbb65dcdb158.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

&emsp;建一个类继承JsonSerializer<T>，并重写父类的serialize方法，方法内容就是得到的时间除1000，然后在对应的属性前加上如图的注解就ok了

![4.png](https://upload-images.jianshu.io/upload_images/8918083-9356207f05a17254.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

&emsp;结果如图

![5.png](https://upload-images.jianshu.io/upload_images/8918083-0d815eaab8d1d603.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
内容如上。\（￣︶￣）/

参考资料:无所不知的度娘+各位大佬的博客
