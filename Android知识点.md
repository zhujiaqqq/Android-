<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [JAVA基础知识点](#java%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E7%82%B9)
  - [JVM相关](#jvm%E7%9B%B8%E5%85%B3)
    - [1. Java内存结构及分区](#1-java%E5%86%85%E5%AD%98%E7%BB%93%E6%9E%84%E5%8F%8A%E5%88%86%E5%8C%BA)
    - [2. Java对象的创建、存储及访问](#2-java%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%88%9B%E5%BB%BA%E5%AD%98%E5%82%A8%E5%8F%8A%E8%AE%BF%E9%97%AE)
    - [3. Java判断对象是否存活及垃圾回收算法(GC)](#3-java%E5%88%A4%E6%96%AD%E5%AF%B9%E8%B1%A1%E6%98%AF%E5%90%A6%E5%AD%98%E6%B4%BB%E5%8F%8A%E5%9E%83%E5%9C%BE%E5%9B%9E%E6%94%B6%E7%AE%97%E6%B3%95gc)
    - [4. Jvm中的常⻅的垃圾回收器](#4-jvm%E4%B8%AD%E7%9A%84%E5%B8%B8%E2%BB%85%E7%9A%84%E5%9E%83%E5%9C%BE%E5%9B%9E%E6%94%B6%E5%99%A8)
    - [5. Java类加载过程](#5-java%E7%B1%BB%E5%8A%A0%E8%BD%BD%E8%BF%87%E7%A8%8B)
    - [6. Java类加载器(双亲委派模型)](#6-java%E7%B1%BB%E5%8A%A0%E8%BD%BD%E5%99%A8%E5%8F%8C%E4%BA%B2%E5%A7%94%E6%B4%BE%E6%A8%A1%E5%9E%8B)
  - [集合相关](#%E9%9B%86%E5%90%88%E7%9B%B8%E5%85%B3)
    - [1. ArrayList分析](#1-arraylist%E5%88%86%E6%9E%90)
    - [2. LinkedList分析](#2-linkedlist%E5%88%86%E6%9E%90)
    - [3. HashMap分析](#3-hashmap%E5%88%86%E6%9E%90)
    - [4. HashTable分析](#4-hashtable%E5%88%86%E6%9E%90)
    - [5. LinkedHashMap分析](#5-linkedhashmap%E5%88%86%E6%9E%90)
    - [6. HashSet分析](#6-hashset%E5%88%86%E6%9E%90)
    - [7. LinkedHashSet分析](#7-linkedhashset%E5%88%86%E6%9E%90)
    - [8. ArrayMap、SparseMap、与HashMap的对比](#8-arraymapsparsemap%E4%B8%8Ehashmap%E7%9A%84%E5%AF%B9%E6%AF%94)
    - [9. ConcurrentHashMap分析](#9-concurrenthashmap%E5%88%86%E6%9E%90)
    - [10. SpareArray 的实现原理](#10-sparearray-%E7%9A%84%E5%AE%9E%E7%8E%B0%E5%8E%9F%E7%90%86)
    - [11. ArrayBlockingQueue、LinkedBlockingQueue](#11-arrayblockingqueuelinkedblockingqueue)
  - [并发相关](#%E5%B9%B6%E5%8F%91%E7%9B%B8%E5%85%B3)
    - [1. Java内存模型](#1-java%E5%86%85%E5%AD%98%E6%A8%A1%E5%9E%8B)
    - [2. volatile原理](#2-volatile%E5%8E%9F%E7%90%86)
    - [3. Synchronized的原理](#3-synchronized%E7%9A%84%E5%8E%9F%E7%90%86)
    - [4. AQS原理](#4-aqs%E5%8E%9F%E7%90%86)
    - [5. Condition原理](#5-condition%E5%8E%9F%E7%90%86)
    - [6. ReentrantLock 原理](#6-reentrantlock-%E5%8E%9F%E7%90%86)
    - [7. 公平锁与非公平锁](#7-%E5%85%AC%E5%B9%B3%E9%94%81%E4%B8%8E%E9%9D%9E%E5%85%AC%E5%B9%B3%E9%94%81)
    - [8. ReentrantReadWriteLock原理](#8-reentrantreadwritelock%E5%8E%9F%E7%90%86)
  - [线程相关](#%E7%BA%BF%E7%A8%8B%E7%9B%B8%E5%85%B3)
    - [1. 线程的启动和终止](#1-%E7%BA%BF%E7%A8%8B%E7%9A%84%E5%90%AF%E5%8A%A8%E5%92%8C%E7%BB%88%E6%AD%A2)
    - [2. 线程间通信](#2-%E7%BA%BF%E7%A8%8B%E9%97%B4%E9%80%9A%E4%BF%A1)
    - [3. 等待/通知机制](#3-%E7%AD%89%E5%BE%85%E9%80%9A%E7%9F%A5%E6%9C%BA%E5%88%B6)
    - [4. 什么是深拷贝和浅拷贝](#4-%E4%BB%80%E4%B9%88%E6%98%AF%E6%B7%B1%E6%8B%B7%E8%B4%9D%E5%92%8C%E6%B5%85%E6%8B%B7%E8%B4%9D)
    - [5. 多线程断点续传的实现原理](#5-%E5%A4%9A%E7%BA%BF%E7%A8%8B%E6%96%AD%E7%82%B9%E7%BB%AD%E4%BC%A0%E7%9A%84%E5%AE%9E%E7%8E%B0%E5%8E%9F%E7%90%86)
  - [线程池相关](#%E7%BA%BF%E7%A8%8B%E6%B1%A0%E7%9B%B8%E5%85%B3)
    - [1. 使用线程池的原因](#1-%E4%BD%BF%E7%94%A8%E7%BA%BF%E7%A8%8B%E6%B1%A0%E7%9A%84%E5%8E%9F%E5%9B%A0)
    - [2. 线程池内部原理](#2-%E7%BA%BF%E7%A8%8B%E6%B1%A0%E5%86%85%E9%83%A8%E5%8E%9F%E7%90%86)
    - [3. 线程池中的几种重要的参数及流程说明](#3-%E7%BA%BF%E7%A8%8B%E6%B1%A0%E4%B8%AD%E7%9A%84%E5%87%A0%E7%A7%8D%E9%87%8D%E8%A6%81%E7%9A%84%E5%8F%82%E6%95%B0%E5%8F%8A%E6%B5%81%E7%A8%8B%E8%AF%B4%E6%98%8E)
    - [4. 线程池中几种常⻅的工作队列](#4-%E7%BA%BF%E7%A8%8B%E6%B1%A0%E4%B8%AD%E5%87%A0%E7%A7%8D%E5%B8%B8%E2%BB%85%E7%9A%84%E5%B7%A5%E4%BD%9C%E9%98%9F%E5%88%97)
    - [5. 几种常⻅的线程池及使用场景](#5-%E5%87%A0%E7%A7%8D%E5%B8%B8%E2%BB%85%E7%9A%84%E7%BA%BF%E7%A8%8B%E6%B1%A0%E5%8F%8A%E4%BD%BF%E7%94%A8%E5%9C%BA%E6%99%AF)
  - [IO相关](#io%E7%9B%B8%E5%85%B3)
    - [1. Socket](#1-socket)
    - [2. BIO/NIO](#2-bionio)
- [Android基础知识点](#android%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86%E7%82%B9)
  - [Activity相关](#activity%E7%9B%B8%E5%85%B3)
    - [1. 典型状况下的生命周期](#1-%E5%85%B8%E5%9E%8B%E7%8A%B6%E5%86%B5%E4%B8%8B%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
    - [2. 异常情况下的生命周期](#2-%E5%BC%82%E5%B8%B8%E6%83%85%E5%86%B5%E4%B8%8B%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
    - [3. 异常情况下的数据保存](#3-%E5%BC%82%E5%B8%B8%E6%83%85%E5%86%B5%E4%B8%8B%E7%9A%84%E6%95%B0%E6%8D%AE%E4%BF%9D%E5%AD%98)
    - [4. 各种情况下跳转到某个Activity时目标Activity及当前Activity的生命周期](#4-%E5%90%84%E7%A7%8D%E6%83%85%E5%86%B5%E4%B8%8B%E8%B7%B3%E8%BD%AC%E5%88%B0%E6%9F%90%E4%B8%AAactivity%E6%97%B6%E7%9B%AE%E6%A0%87activity%E5%8F%8A%E5%BD%93%E5%89%8Dactivity%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
    - [5. Activity的启动模式及应用场景](#5-activity%E7%9A%84%E5%90%AF%E5%8A%A8%E6%A8%A1%E5%BC%8F%E5%8F%8A%E5%BA%94%E7%94%A8%E5%9C%BA%E6%99%AF)
    - [6. 进程和应用生命周期](#6-%E8%BF%9B%E7%A8%8B%E5%92%8C%E5%BA%94%E7%94%A8%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
    - [7. Activity启动流程](#7-activity%E5%90%AF%E5%8A%A8%E6%B5%81%E7%A8%8B)
  - [Service相关](#service%E7%9B%B8%E5%85%B3)
    - [1. Service的定义及作用](#1-service%E7%9A%84%E5%AE%9A%E4%B9%89%E5%8F%8A%E4%BD%9C%E7%94%A8)
    - [2. Service两种启动方式 startService、 bindService 区别及生命周期](#2-service%E4%B8%A4%E7%A7%8D%E5%90%AF%E5%8A%A8%E6%96%B9%E5%BC%8F-startservice-bindservice-%E5%8C%BA%E5%88%AB%E5%8F%8A%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
    - [3. Service绑定服务的三种实现方式，扩展Binder类、使用Messenger、使用AIDL](#3-service%E7%BB%91%E5%AE%9A%E6%9C%8D%E5%8A%A1%E7%9A%84%E4%B8%89%E7%A7%8D%E5%AE%9E%E7%8E%B0%E6%96%B9%E5%BC%8F%E6%89%A9%E5%B1%95binder%E7%B1%BB%E4%BD%BF%E7%94%A8messenger%E4%BD%BF%E7%94%A8aidl)
    - [4. 关于启动服务与绑定服务间的转换问题 先绑定服务后启动服务、先启动服务后绑定服务](#4-%E5%85%B3%E4%BA%8E%E5%90%AF%E5%8A%A8%E6%9C%8D%E5%8A%A1%E4%B8%8E%E7%BB%91%E5%AE%9A%E6%9C%8D%E5%8A%A1%E9%97%B4%E7%9A%84%E8%BD%AC%E6%8D%A2%E9%97%AE%E9%A2%98-%E5%85%88%E7%BB%91%E5%AE%9A%E6%9C%8D%E5%8A%A1%E5%90%8E%E5%90%AF%E5%8A%A8%E6%9C%8D%E5%8A%A1%E5%85%88%E5%90%AF%E5%8A%A8%E6%9C%8D%E5%8A%A1%E5%90%8E%E7%BB%91%E5%AE%9A%E6%9C%8D%E5%8A%A1)
    - [5. 服务Service与线程Thread的区别](#5-%E6%9C%8D%E5%8A%A1service%E4%B8%8E%E7%BA%BF%E7%A8%8Bthread%E7%9A%84%E5%8C%BA%E5%88%AB)
    - [6. Android 5.0以上的隐式启动问题及其解决方案](#6-android-50%E4%BB%A5%E4%B8%8A%E7%9A%84%E9%9A%90%E5%BC%8F%E5%90%AF%E5%8A%A8%E9%97%AE%E9%A2%98%E5%8F%8A%E5%85%B6%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88)
    - [7. 如何保证服务不被杀死](#7-%E5%A6%82%E4%BD%95%E4%BF%9D%E8%AF%81%E6%9C%8D%E5%8A%A1%E4%B8%8D%E8%A2%AB%E6%9D%80%E6%AD%BB)
    - [8. IntentService的使用及原理](#8-intentservice%E7%9A%84%E4%BD%BF%E7%94%A8%E5%8F%8A%E5%8E%9F%E7%90%86)
  - [BroadcastReceiver相关](#broadcastreceiver%E7%9B%B8%E5%85%B3)
    - [1. BroadcastReceiver定义及作用、应用场景](#1-broadcastreceiver%E5%AE%9A%E4%B9%89%E5%8F%8A%E4%BD%9C%E7%94%A8%E5%BA%94%E7%94%A8%E5%9C%BA%E6%99%AF)
    - [2. BroadcastReceiver的注册方式](#2-broadcastreceiver%E7%9A%84%E6%B3%A8%E5%86%8C%E6%96%B9%E5%BC%8F)
    - [3. BroadcastReceiver注册与取消的时机](#3-broadcastreceiver%E6%B3%A8%E5%86%8C%E4%B8%8E%E5%8F%96%E6%B6%88%E7%9A%84%E6%97%B6%E6%9C%BA)
    - [4. BroadcastReceiver的不同类型](#4-broadcastreceiver%E7%9A%84%E4%B8%8D%E5%90%8C%E7%B1%BB%E5%9E%8B)
  - [Fragment相关](#fragment%E7%9B%B8%E5%85%B3)
    - [1. Fragment生命周期](#1-fragment%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F)
    - [2. Fragment的懒加载](#2-fragment%E7%9A%84%E6%87%92%E5%8A%A0%E8%BD%BD)
    - [3. Fragment之间的通信](#3-fragment%E4%B9%8B%E9%97%B4%E7%9A%84%E9%80%9A%E4%BF%A1)
    - [4. FragmentPagerAdapter与FragmentStatePagerAdapter的区别](#4-fragmentpageradapter%E4%B8%8Efragmentstatepageradapter%E7%9A%84%E5%8C%BA%E5%88%AB)
    - [5. 为什么不建议直接通过使用new Fragment的方式传入数据](#5-%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%8D%E5%BB%BA%E8%AE%AE%E7%9B%B4%E6%8E%A5%E9%80%9A%E8%BF%87%E4%BD%BF%E7%94%A8new-fragment%E7%9A%84%E6%96%B9%E5%BC%8F%E4%BC%A0%E5%85%A5%E6%95%B0%E6%8D%AE)
  - [序列化相关](#%E5%BA%8F%E5%88%97%E5%8C%96%E7%9B%B8%E5%85%B3)
    - [1. 序列化与反序列化的定义及区别](#1-%E5%BA%8F%E5%88%97%E5%8C%96%E4%B8%8E%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96%E7%9A%84%E5%AE%9A%E4%B9%89%E5%8F%8A%E5%8C%BA%E5%88%AB)
    - [2. Serializable中serialVersionUID及transient关键字的作用](#2-serializable%E4%B8%ADserialversionuid%E5%8F%8Atransient%E5%85%B3%E9%94%AE%E5%AD%97%E7%9A%84%E4%BD%9C%E7%94%A8)
    - [3. 序列化:Parcelable和Serializable差异](#3-%E5%BA%8F%E5%88%97%E5%8C%96parcelable%E5%92%8Cserializable%E5%B7%AE%E5%BC%82)
  - [IPC相关](#ipc%E7%9B%B8%E5%85%B3)
    - [1. 在Android中什么样的情况下会使用多进程模式，如何开启多进程](#1-%E5%9C%A8android%E4%B8%AD%E4%BB%80%E4%B9%88%E6%A0%B7%E7%9A%84%E6%83%85%E5%86%B5%E4%B8%8B%E4%BC%9A%E4%BD%BF%E7%94%A8%E5%A4%9A%E8%BF%9B%E7%A8%8B%E6%A8%A1%E5%BC%8F%E5%A6%82%E4%BD%95%E5%BC%80%E5%90%AF%E5%A4%9A%E8%BF%9B%E7%A8%8B)
    - [2. Android为什么采用Binder做为IPC机制](#2-android%E4%B8%BA%E4%BB%80%E4%B9%88%E9%87%87%E7%94%A8binder%E5%81%9A%E4%B8%BAipc%E6%9C%BA%E5%88%B6)
    - [3. IPC常用方式](#3-ipc%E5%B8%B8%E7%94%A8%E6%96%B9%E5%BC%8F)
    - [4. AIDL的语义](#4-aidl%E7%9A%84%E8%AF%AD%E4%B9%89)
    - [5. AIDL如何创建 AIDL生成Java文件详细分析](#5-aidl%E5%A6%82%E4%BD%95%E5%88%9B%E5%BB%BA-aidl%E7%94%9F%E6%88%90java%E6%96%87%E4%BB%B6%E8%AF%A6%E7%BB%86%E5%88%86%E6%9E%90)
  - [View事件机制相关](#view%E4%BA%8B%E4%BB%B6%E6%9C%BA%E5%88%B6%E7%9B%B8%E5%85%B3)
    - [1. View的坐标体系](#1-view%E7%9A%84%E5%9D%90%E6%A0%87%E4%BD%93%E7%B3%BB)
    - [2. View滑动的几种方式，使用ScrollTo/ScrollBy、使用动画、改变布局参数](#2-view%E6%BB%91%E5%8A%A8%E7%9A%84%E5%87%A0%E7%A7%8D%E6%96%B9%E5%BC%8F%E4%BD%BF%E7%94%A8scrolltoscrollby%E4%BD%BF%E7%94%A8%E5%8A%A8%E7%94%BB%E6%94%B9%E5%8F%98%E5%B8%83%E5%B1%80%E5%8F%82%E6%95%B0)
    - [3. 弹性滑动的原理及实现](#3-%E5%BC%B9%E6%80%A7%E6%BB%91%E5%8A%A8%E7%9A%84%E5%8E%9F%E7%90%86%E5%8F%8A%E5%AE%9E%E7%8E%B0)
    - [4. View的事件分发机制，点击事件的传递规则，事件分发的源码解读](#4-view%E7%9A%84%E4%BA%8B%E4%BB%B6%E5%88%86%E5%8F%91%E6%9C%BA%E5%88%B6%E7%82%B9%E5%87%BB%E4%BA%8B%E4%BB%B6%E7%9A%84%E4%BC%A0%E9%80%92%E8%A7%84%E5%88%99%E4%BA%8B%E4%BB%B6%E5%88%86%E5%8F%91%E7%9A%84%E6%BA%90%E7%A0%81%E8%A7%A3%E8%AF%BB)
    - [5. 处理滑动冲突的场景及解决方法](#5-%E5%A4%84%E7%90%86%E6%BB%91%E5%8A%A8%E5%86%B2%E7%AA%81%E7%9A%84%E5%9C%BA%E6%99%AF%E5%8F%8A%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95)
  - [View绘制相关](#view%E7%BB%98%E5%88%B6%E7%9B%B8%E5%85%B3)
    - [1. DecorView、Window、ViewRootImpl等概念](#1-decorviewwindowviewrootimpl%E7%AD%89%E6%A6%82%E5%BF%B5)
    - [2. MeasureSpec概念](#2-measurespec%E6%A6%82%E5%BF%B5)
    - [3. View的工作流程，measure过程、layout过程、draw过程](#3-view%E7%9A%84%E5%B7%A5%E4%BD%9C%E6%B5%81%E7%A8%8Bmeasure%E8%BF%87%E7%A8%8Blayout%E8%BF%87%E7%A8%8Bdraw%E8%BF%87%E7%A8%8B)
    - [4. 自定义View需要注意的事项](#4-%E8%87%AA%E5%AE%9A%E4%B9%89view%E9%9C%80%E8%A6%81%E6%B3%A8%E6%84%8F%E7%9A%84%E4%BA%8B%E9%A1%B9)
    - [5. Activity、Window、View三者之间的关系](#5-activitywindowview%E4%B8%89%E8%80%85%E4%B9%8B%E9%97%B4%E7%9A%84%E5%85%B3%E7%B3%BB)
  - [View动画相关](#view%E5%8A%A8%E7%94%BB%E7%9B%B8%E5%85%B3)
    - [1. 常用动画View动画(补间动画)、属性动画与帧动画](#1-%E5%B8%B8%E7%94%A8%E5%8A%A8%E7%94%BBview%E5%8A%A8%E7%94%BB%E8%A1%A5%E9%97%B4%E5%8A%A8%E7%94%BB%E5%B1%9E%E6%80%A7%E5%8A%A8%E7%94%BB%E4%B8%8E%E5%B8%A7%E5%8A%A8%E7%94%BB)
    - [2. 补间动画与属性动画区别](#2-%E8%A1%A5%E9%97%B4%E5%8A%A8%E7%94%BB%E4%B8%8E%E5%B1%9E%E6%80%A7%E5%8A%A8%E7%94%BB%E5%8C%BA%E5%88%AB)
    - [3. 插值器和估值器理解](#3-%E6%8F%92%E5%80%BC%E5%99%A8%E5%92%8C%E4%BC%B0%E5%80%BC%E5%99%A8%E7%90%86%E8%A7%A3)
    - [4. 属性动画的工作原理](#4-%E5%B1%9E%E6%80%A7%E5%8A%A8%E7%94%BB%E7%9A%84%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86)
  - [Handler相关](#handler%E7%9B%B8%E5%85%B3)
    - [1. Handler机制之ThreadLocal](#1-handler%E6%9C%BA%E5%88%B6%E4%B9%8Bthreadlocal)
    - [2. Handler机制之Looper、Handler、消息队列如何理解](#2-handler%E6%9C%BA%E5%88%B6%E4%B9%8Blooperhandler%E6%B6%88%E6%81%AF%E9%98%9F%E5%88%97%E5%A6%82%E4%BD%95%E7%90%86%E8%A7%A3)
    - [3. Handler机制之Message的发送与取出](#3-handler%E6%9C%BA%E5%88%B6%E4%B9%8Bmessage%E7%9A%84%E5%8F%91%E9%80%81%E4%B8%8E%E5%8F%96%E5%87%BA)
    - [4. Handler机制之Message及Message的回收机制](#4-handler%E6%9C%BA%E5%88%B6%E4%B9%8Bmessage%E5%8F%8Amessage%E7%9A%84%E5%9B%9E%E6%94%B6%E6%9C%BA%E5%88%B6)
    - [5. Handler机制之循环消息队列的退出](#5-handler%E6%9C%BA%E5%88%B6%E4%B9%8B%E5%BE%AA%E7%8E%AF%E6%B6%88%E6%81%AF%E9%98%9F%E5%88%97%E7%9A%84%E9%80%80%E5%87%BA)
    - [6. Handler机制之内存泄漏](#6-handler%E6%9C%BA%E5%88%B6%E4%B9%8B%E5%86%85%E5%AD%98%E6%B3%84%E6%BC%8F)
    - [7. Handler机制之IdleHandle的理解及使用](#7-handler%E6%9C%BA%E5%88%B6%E4%B9%8Bidlehandle%E7%9A%84%E7%90%86%E8%A7%A3%E5%8F%8A%E4%BD%BF%E7%94%A8)
  - [AsyncTask相关](#asynctask%E7%9B%B8%E5%85%B3)
    - [1. AsyncTask的使用和注意事项](#1-asynctask%E7%9A%84%E4%BD%BF%E7%94%A8%E5%92%8C%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
    - [2. AsyncTask几个重要的方法 doInBackgound、onProgressUpdate、onPostExecute等](#2-asynctask%E5%87%A0%E4%B8%AA%E9%87%8D%E8%A6%81%E7%9A%84%E6%96%B9%E6%B3%95-doinbackgoundonprogressupdateonpostexecute%E7%AD%89)
    - [3. AsyncTask的工作原理及源码理解](#3-asynctask%E7%9A%84%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86%E5%8F%8A%E6%BA%90%E7%A0%81%E7%90%86%E8%A7%A3)
  - [SharedPreference相关](#sharedpreference%E7%9B%B8%E5%85%B3)
    - [1. 获取 SharedPreferences 对象过程中，系统做了什么](#1-%E8%8E%B7%E5%8F%96-sharedpreferences-%E5%AF%B9%E8%B1%A1%E8%BF%87%E7%A8%8B%E4%B8%AD%E7%B3%BB%E7%BB%9F%E5%81%9A%E4%BA%86%E4%BB%80%E4%B9%88)
    - [2. getXxx 方法做了什么](#2-getxxx-%E6%96%B9%E6%B3%95%E5%81%9A%E4%BA%86%E4%BB%80%E4%B9%88)
    - [3. putXxx方法做了什么](#3-putxxx%E6%96%B9%E6%B3%95%E5%81%9A%E4%BA%86%E4%BB%80%E4%B9%88)
    - [4. commit/apply方法如何实现同步/异步写磁盘](#4-commitapply%E6%96%B9%E6%B3%95%E5%A6%82%E4%BD%95%E5%AE%9E%E7%8E%B0%E5%90%8C%E6%AD%A5%E5%BC%82%E6%AD%A5%E5%86%99%E7%A3%81%E7%9B%98)
  - [Bitmap压缩回收相关](#bitmap%E5%8E%8B%E7%BC%A9%E5%9B%9E%E6%94%B6%E7%9B%B8%E5%85%B3)
    - [1. Bitmap所占内存](#1-bitmap%E6%89%80%E5%8D%A0%E5%86%85%E5%AD%98)
    - [2. 常用压缩图片方式](#2-%E5%B8%B8%E7%94%A8%E5%8E%8B%E7%BC%A9%E5%9B%BE%E7%89%87%E6%96%B9%E5%BC%8F)
    - [3. LruCache原理](#3-lrucache%E5%8E%9F%E7%90%86)
    - [4. DiskLruCache原理](#4-disklrucache%E5%8E%9F%E7%90%86)
    - [5. LinkedHashMap原理](#5-linkedhashmap%E5%8E%9F%E7%90%86)
  - [ListView与RecyclerView相关](#listview%E4%B8%8Erecyclerview%E7%9B%B8%E5%85%B3)
    - [1. ListView的原理和复用机制](#1-listview%E7%9A%84%E5%8E%9F%E7%90%86%E5%92%8C%E5%A4%8D%E7%94%A8%E6%9C%BA%E5%88%B6)
    - [2. ListView和RecyclerView的区别](#2-listview%E5%92%8Crecyclerview%E7%9A%84%E5%8C%BA%E5%88%AB)
  - [数据存储相关](#%E6%95%B0%E6%8D%AE%E5%AD%98%E5%82%A8%E7%9B%B8%E5%85%B3)
    - [1. 常用数据库框架GreenDao,官方Room](#1-%E5%B8%B8%E7%94%A8%E6%95%B0%E6%8D%AE%E5%BA%93%E6%A1%86%E6%9E%B6greendao%E5%AE%98%E6%96%B9room)
    - [2. 数据库数据迁移问题](#2-%E6%95%B0%E6%8D%AE%E5%BA%93%E6%95%B0%E6%8D%AE%E8%BF%81%E7%A7%BB%E9%97%AE%E9%A2%98)
    - [3. GreenDao中一对一，一对多，多对多关系](#3-greendao%E4%B8%AD%E4%B8%80%E5%AF%B9%E4%B8%80%E4%B8%80%E5%AF%B9%E5%A4%9A%E5%A4%9A%E5%AF%B9%E5%A4%9A%E5%85%B3%E7%B3%BB)
- [Android开源框架知识点](#android%E5%BC%80%E6%BA%90%E6%A1%86%E6%9E%B6%E7%9F%A5%E8%AF%86%E7%82%B9)
  - [OkHttp相关](#okhttp%E7%9B%B8%E5%85%B3)
    - [1. OkHttp的优点](#1-okhttp%E7%9A%84%E4%BC%98%E7%82%B9)
    - [2. OkHttp执行请求的整个流程](#2-okhttp%E6%89%A7%E8%A1%8C%E8%AF%B7%E6%B1%82%E7%9A%84%E6%95%B4%E4%B8%AA%E6%B5%81%E7%A8%8B)
    - [3. OkHttp中的拦截器](#3-okhttp%E4%B8%AD%E7%9A%84%E6%8B%A6%E6%88%AA%E5%99%A8)
    - [4. OkHttp中的同步请求与异步请求的理解及其源码](#4-okhttp%E4%B8%AD%E7%9A%84%E5%90%8C%E6%AD%A5%E8%AF%B7%E6%B1%82%E4%B8%8E%E5%BC%82%E6%AD%A5%E8%AF%B7%E6%B1%82%E7%9A%84%E7%90%86%E8%A7%A3%E5%8F%8A%E5%85%B6%E6%BA%90%E7%A0%81)
    - [5. OkHttp中涉及到的设计模式](#5-okhttp%E4%B8%AD%E6%B6%89%E5%8F%8A%E5%88%B0%E7%9A%84%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F)
    - [6. OkHttp底层网络请求实现，socket还是URLConnection](#6-okhttp%E5%BA%95%E5%B1%82%E7%BD%91%E7%BB%9C%E8%AF%B7%E6%B1%82%E5%AE%9E%E7%8E%B0socket%E8%BF%98%E6%98%AFurlconnection)
  - [Retrofit相关](#retrofit%E7%9B%B8%E5%85%B3)
    - [1. Retrofit执行请求的整个流程](#1-retrofit%E6%89%A7%E8%A1%8C%E8%AF%B7%E6%B1%82%E7%9A%84%E6%95%B4%E4%B8%AA%E6%B5%81%E7%A8%8B)
    - [2. Retrofit中ConverterFactory、CallAdapterFactory的理解](#2-retrofit%E4%B8%ADconverterfactorycalladapterfactory%E7%9A%84%E7%90%86%E8%A7%A3)
    - [3. Retrofit中CallAdapter的适配器模式](#3-retrofit%E4%B8%ADcalladapter%E7%9A%84%E9%80%82%E9%85%8D%E5%99%A8%E6%A8%A1%E5%BC%8F)
  - [RxJava相关](#rxjava%E7%9B%B8%E5%85%B3)
    - [1. RxJava常用创建操作符 create、from、just、interval、range等](#1-rxjava%E5%B8%B8%E7%94%A8%E5%88%9B%E5%BB%BA%E6%93%8D%E4%BD%9C%E7%AC%A6-createfromjustintervalrange%E7%AD%89)
    - [2. RxJava常用组合、合并操作符 combineLatest、join、merge、zip等](#2-rxjava%E5%B8%B8%E7%94%A8%E7%BB%84%E5%90%88%E5%90%88%E5%B9%B6%E6%93%8D%E4%BD%9C%E7%AC%A6-combinelatestjoinmergezip%E7%AD%89)
    - [3. RxJava错误处理操作符 onErrorReturn、onErrorResumeNext、onExceptionResumeNext等](#3-rxjava%E9%94%99%E8%AF%AF%E5%A4%84%E7%90%86%E6%93%8D%E4%BD%9C%E7%AC%A6-onerrorreturnonerrorresumenextonexceptionresumenext%E7%AD%89)
    - [4. RxJava过滤操作符 filter、ofType、sample、take等](#4-rxjava%E8%BF%87%E6%BB%A4%E6%93%8D%E4%BD%9C%E7%AC%A6-filteroftypesampletake%E7%AD%89)
    - [5. Rxjava背压相关理解](#5-rxjava%E8%83%8C%E5%8E%8B%E7%9B%B8%E5%85%B3%E7%90%86%E8%A7%A3)
    - [6. RxJava实际开发中的使用](#6-rxjava%E5%AE%9E%E9%99%85%E5%BC%80%E5%8F%91%E4%B8%AD%E7%9A%84%E4%BD%BF%E7%94%A8)
  - [Glide相关](#glide%E7%9B%B8%E5%85%B3)
    - [1. Glide的执行流程](#1-glide%E7%9A%84%E6%89%A7%E8%A1%8C%E6%B5%81%E7%A8%8B)
    - [2. Glide的缓存机制](#2-glide%E7%9A%84%E7%BC%93%E5%AD%98%E6%9C%BA%E5%88%B6)
    - [3. Glide图片转换](#3-glide%E5%9B%BE%E7%89%87%E8%BD%AC%E6%8D%A2)
    - [4. Glide带进度的图片加载功能](#4-glide%E5%B8%A6%E8%BF%9B%E5%BA%A6%E7%9A%84%E5%9B%BE%E7%89%87%E5%8A%A0%E8%BD%BD%E5%8A%9F%E8%83%BD)
    - [5. Glide内存、磁盘缓存，优先级使用](#5-glide%E5%86%85%E5%AD%98%E7%A3%81%E7%9B%98%E7%BC%93%E5%AD%98%E4%BC%98%E5%85%88%E7%BA%A7%E4%BD%BF%E7%94%A8)
  - [ButterKnife相关](#butterknife%E7%9B%B8%E5%85%B3)
    - [1. Java注解相关Annotation](#1-java%E6%B3%A8%E8%A7%A3%E7%9B%B8%E5%85%B3annotation)
    - [2. Java注解相关之APT工具](#2-java%E6%B3%A8%E8%A7%A3%E7%9B%B8%E5%85%B3%E4%B9%8Bapt%E5%B7%A5%E5%85%B7)
    - [3. ButterKnife注解框架原理](#3-butterknife%E6%B3%A8%E8%A7%A3%E6%A1%86%E6%9E%B6%E5%8E%9F%E7%90%86)
  - [EventBus相关](#eventbus%E7%9B%B8%E5%85%B3)
    - [1. EventBus原理，及索引类的使用](#1-eventbus%E5%8E%9F%E7%90%86%E5%8F%8A%E7%B4%A2%E5%BC%95%E7%B1%BB%E7%9A%84%E4%BD%BF%E7%94%A8)
  - [Android性能优化](#android%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96)
    - [1. 性能优化布局优化、绘制优化、线程优化等](#1-%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96%E5%B8%83%E5%B1%80%E4%BC%98%E5%8C%96%E7%BB%98%E5%88%B6%E4%BC%98%E5%8C%96%E7%BA%BF%E7%A8%8B%E4%BC%98%E5%8C%96%E7%AD%89)
    - [2. ANR异常](#2-anr%E5%BC%82%E5%B8%B8)
    - [3. OOM异常:内存溢出的原因](#3-oom%E5%BC%82%E5%B8%B8%E5%86%85%E5%AD%98%E6%BA%A2%E5%87%BA%E7%9A%84%E5%8E%9F%E5%9B%A0)
    - [4. 内存泄漏](#4-%E5%86%85%E5%AD%98%E6%B3%84%E6%BC%8F)
  - [Android屏幕适配知识点](#android%E5%B1%8F%E5%B9%95%E9%80%82%E9%85%8D%E7%9F%A5%E8%AF%86%E7%82%B9)
    - [1. 今日头条适配方式](#1-%E4%BB%8A%E6%97%A5%E5%A4%B4%E6%9D%A1%E9%80%82%E9%85%8D%E6%96%B9%E5%BC%8F)
    - [2. 宽高限定符适配方式](#2-%E5%AE%BD%E9%AB%98%E9%99%90%E5%AE%9A%E7%AC%A6%E9%80%82%E9%85%8D%E6%96%B9%E5%BC%8F)
    - [3. smallestWidth适配](#3-smallestwidth%E9%80%82%E9%85%8D)
  - [Android打包知识点](#android%E6%89%93%E5%8C%85%E7%9F%A5%E8%AF%86%E7%82%B9)
    - [1. 打包的流程](#1-%E6%89%93%E5%8C%85%E7%9A%84%E6%B5%81%E7%A8%8B)
    - [2. 安卓签名的理解](#2-%E5%AE%89%E5%8D%93%E7%AD%BE%E5%90%8D%E7%9A%84%E7%90%86%E8%A7%A3)
    - [3. Gradle多渠道打包](#3-gradle%E5%A4%9A%E6%B8%A0%E9%81%93%E6%89%93%E5%8C%85)
  - [Android不同版本特性知识点](#android%E4%B8%8D%E5%90%8C%E7%89%88%E6%9C%AC%E7%89%B9%E6%80%A7%E7%9F%A5%E8%AF%86%E7%82%B9)
    - [1. 广播在7.0、8.0、9.0下的适配](#1-%E5%B9%BF%E6%92%AD%E5%9C%A8708090%E4%B8%8B%E7%9A%84%E9%80%82%E9%85%8D)
    - [2. Android 6.0 权限下的适配](#2-android-60-%E6%9D%83%E9%99%90%E4%B8%8B%E7%9A%84%E9%80%82%E9%85%8D)
    - [3. Android 7.0 应用共享文件(FileProvider)](#3-android-70-%E5%BA%94%E7%94%A8%E5%85%B1%E4%BA%AB%E6%96%87%E4%BB%B6fileprovider)
  - [网络知识点](#%E7%BD%91%E7%BB%9C%E7%9F%A5%E8%AF%86%E7%82%B9)
    - [1. 计算机网络三种体系架构，OSI体系架构(7层)、TCP/IP体系架构(4层)，五层体系架构 TCP的连接管理(三报文握手，四报文握手)](#1-%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C%E4%B8%89%E7%A7%8D%E4%BD%93%E7%B3%BB%E6%9E%B6%E6%9E%84osi%E4%BD%93%E7%B3%BB%E6%9E%B6%E6%9E%847%E5%B1%82tcpip%E4%BD%93%E7%B3%BB%E6%9E%B6%E6%9E%844%E5%B1%82%E4%BA%94%E5%B1%82%E4%BD%93%E7%B3%BB%E6%9E%B6%E6%9E%84-tcp%E7%9A%84%E8%BF%9E%E6%8E%A5%E7%AE%A1%E7%90%86%E4%B8%89%E6%8A%A5%E6%96%87%E6%8F%A1%E6%89%8B%E5%9B%9B%E6%8A%A5%E6%96%87%E6%8F%A1%E6%89%8B)
    - [2. TCP与UDP的理解与区别](#2-tcp%E4%B8%8Eudp%E7%9A%84%E7%90%86%E8%A7%A3%E4%B8%8E%E5%8C%BA%E5%88%AB)
    - [3. Http(HyberText Transfer Protocol)基本概念及报文结构](#3-httphybertext-transfer-protocol%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5%E5%8F%8A%E6%8A%A5%E6%96%87%E7%BB%93%E6%9E%84)
    - [4. Http常⻅错误码](#4-http%E5%B8%B8%E2%BB%85%E9%94%99%E8%AF%AF%E7%A0%81)
    - [5. Http1.0与Http1.1与Http2.0的区别](#5-http10%E4%B8%8Ehttp11%E4%B8%8Ehttp20%E7%9A%84%E5%8C%BA%E5%88%AB)
    - [6. Http中get请求与post请求的区别](#6-http%E4%B8%ADget%E8%AF%B7%E6%B1%82%E4%B8%8Epost%E8%AF%B7%E6%B1%82%E7%9A%84%E5%8C%BA%E5%88%AB)
    - [7. Http中cookie与session的区别](#7-http%E4%B8%ADcookie%E4%B8%8Esession%E7%9A%84%E5%8C%BA%E5%88%AB)
    - [8. Http与Https的区别 Https加密算法相关面试问题，签名证书，公钥私钥、数字摘要的理解](#8-http%E4%B8%8Ehttps%E7%9A%84%E5%8C%BA%E5%88%AB-https%E5%8A%A0%E5%AF%86%E7%AE%97%E6%B3%95%E7%9B%B8%E5%85%B3%E9%9D%A2%E8%AF%95%E9%97%AE%E9%A2%98%E7%AD%BE%E5%90%8D%E8%AF%81%E4%B9%A6%E5%85%AC%E9%92%A5%E7%A7%81%E9%92%A5%E6%95%B0%E5%AD%97%E6%91%98%E8%A6%81%E7%9A%84%E7%90%86%E8%A7%A3)
  - [设计模式知识点](#%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F%E7%9F%A5%E8%AF%86%E7%82%B9)
    - [1. 单例模式](#1-%E5%8D%95%E4%BE%8B%E6%A8%A1%E5%BC%8F)
    - [2. Builder模式](#2-builder%E6%A8%A1%E5%BC%8F)
    - [3. 装饰模式](#3-%E8%A3%85%E9%A5%B0%E6%A8%A1%E5%BC%8F)
    - [4. 策略模式](#4-%E7%AD%96%E7%95%A5%E6%A8%A1%E5%BC%8F)
    - [5. 模板方法](#5-%E6%A8%A1%E6%9D%BF%E6%96%B9%E6%B3%95)
    - [6. 观察者模式](#6-%E8%A7%82%E5%AF%9F%E8%80%85%E6%A8%A1%E5%BC%8F)
  - [算法知识点](#%E7%AE%97%E6%B3%95%E7%9F%A5%E8%AF%86%E7%82%B9)
    - [1. 常⻅的八大排序方式](#1-%E5%B8%B8%E2%BB%85%E7%9A%84%E5%85%AB%E5%A4%A7%E6%8E%92%E5%BA%8F%E6%96%B9%E5%BC%8F)
    - [2. 时间复杂度的计算](#2-%E6%97%B6%E9%97%B4%E5%A4%8D%E6%9D%82%E5%BA%A6%E7%9A%84%E8%AE%A1%E7%AE%97)
    - [3. 链表相关算法，链表翻转，链表合并等](#3-%E9%93%BE%E8%A1%A8%E7%9B%B8%E5%85%B3%E7%AE%97%E6%B3%95%E9%93%BE%E8%A1%A8%E7%BF%BB%E8%BD%AC%E9%93%BE%E8%A1%A8%E5%90%88%E5%B9%B6%E7%AD%89)
    - [4. 二叉树相关算法前序、中序、后序遍历(递归，迭代)](#4-%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9B%B8%E5%85%B3%E7%AE%97%E6%B3%95%E5%89%8D%E5%BA%8F%E4%B8%AD%E5%BA%8F%E5%90%8E%E5%BA%8F%E9%81%8D%E5%8E%86%E9%80%92%E5%BD%92%E8%BF%AD%E4%BB%A3)
    - [5. 红黑树与BL树](#5-%E7%BA%A2%E9%BB%91%E6%A0%91%E4%B8%8Ebl%E6%A0%91)
    - [6. 给阿里2万多名员工按年龄排序应该选择哪个算法](#6-%E7%BB%99%E9%98%BF%E9%87%8C2%E4%B8%87%E5%A4%9A%E5%90%8D%E5%91%98%E5%B7%A5%E6%8C%89%E5%B9%B4%E9%BE%84%E6%8E%92%E5%BA%8F%E5%BA%94%E8%AF%A5%E9%80%89%E6%8B%A9%E5%93%AA%E4%B8%AA%E7%AE%97%E6%B3%95)
    - [7. GC算法(各种算法的优缺点以及应用场景)](#7-gc%E7%AE%97%E6%B3%95%E5%90%84%E7%A7%8D%E7%AE%97%E6%B3%95%E7%9A%84%E4%BC%98%E7%BC%BA%E7%82%B9%E4%BB%A5%E5%8F%8A%E5%BA%94%E7%94%A8%E5%9C%BA%E6%99%AF)
    - [8. 蚁群算法与蒙特卡洛算法](#8-%E8%9A%81%E7%BE%A4%E7%AE%97%E6%B3%95%E4%B8%8E%E8%92%99%E7%89%B9%E5%8D%A1%E6%B4%9B%E7%AE%97%E6%B3%95)
    - [9. 子串包含问题(KMP 算法)写代码实现](#9-%E5%AD%90%E4%B8%B2%E5%8C%85%E5%90%AB%E9%97%AE%E9%A2%98kmp-%E7%AE%97%E6%B3%95%E5%86%99%E4%BB%A3%E7%A0%81%E5%AE%9E%E7%8E%B0)
    - [10. 一个无序，不重复数组，输出N个元素，使得N个元素的和相加为M，给出时间复杂度、空间复杂度。手写算法](#10-%E4%B8%80%E4%B8%AA%E6%97%A0%E5%BA%8F%E4%B8%8D%E9%87%8D%E5%A4%8D%E6%95%B0%E7%BB%84%E8%BE%93%E5%87%BAn%E4%B8%AA%E5%85%83%E7%B4%A0%E4%BD%BF%E5%BE%97n%E4%B8%AA%E5%85%83%E7%B4%A0%E7%9A%84%E5%92%8C%E7%9B%B8%E5%8A%A0%E4%B8%BAm%E7%BB%99%E5%87%BA%E6%97%B6%E9%97%B4%E5%A4%8D%E6%9D%82%E5%BA%A6%E7%A9%BA%E9%97%B4%E5%A4%8D%E6%9D%82%E5%BA%A6%E6%89%8B%E5%86%99%E7%AE%97%E6%B3%95)
    - [11. 万亿级别的两个URL文件A和B，如何求出A和B的差集C(提示：Bit映射->hash分组->多文件读写效率->磁盘寻址以及应用层面对寻址的优化)](#11-%E4%B8%87%E4%BA%BF%E7%BA%A7%E5%88%AB%E7%9A%84%E4%B8%A4%E4%B8%AAurl%E6%96%87%E4%BB%B6a%E5%92%8Cb%E5%A6%82%E4%BD%95%E6%B1%82%E5%87%BAa%E5%92%8Cb%E7%9A%84%E5%B7%AE%E9%9B%86c%E6%8F%90%E7%A4%BAbit%E6%98%A0%E5%B0%84-hash%E5%88%86%E7%BB%84-%E5%A4%9A%E6%96%87%E4%BB%B6%E8%AF%BB%E5%86%99%E6%95%88%E7%8E%87-%E7%A3%81%E7%9B%98%E5%AF%BB%E5%9D%80%E4%BB%A5%E5%8F%8A%E5%BA%94%E7%94%A8%E5%B1%82%E9%9D%A2%E5%AF%B9%E5%AF%BB%E5%9D%80%E7%9A%84%E4%BC%98%E5%8C%96)
    - [12. 两个不重复的数组集合中，求共同的元素](#12-%E4%B8%A4%E4%B8%AA%E4%B8%8D%E9%87%8D%E5%A4%8D%E7%9A%84%E6%95%B0%E7%BB%84%E9%9B%86%E5%90%88%E4%B8%AD%E6%B1%82%E5%85%B1%E5%90%8C%E7%9A%84%E5%85%83%E7%B4%A0)
    - [13. 两个不重复的数组集合中，这两个集合都是海量数据，内存中放不下，怎么求共同的元素](#13-%E4%B8%A4%E4%B8%AA%E4%B8%8D%E9%87%8D%E5%A4%8D%E7%9A%84%E6%95%B0%E7%BB%84%E9%9B%86%E5%90%88%E4%B8%AD%E8%BF%99%E4%B8%A4%E4%B8%AA%E9%9B%86%E5%90%88%E9%83%BD%E6%98%AF%E6%B5%B7%E9%87%8F%E6%95%B0%E6%8D%AE%E5%86%85%E5%AD%98%E4%B8%AD%E6%94%BE%E4%B8%8D%E4%B8%8B%E6%80%8E%E4%B9%88%E6%B1%82%E5%85%B1%E5%90%8C%E7%9A%84%E5%85%83%E7%B4%A0)
    - [14. 一个文件中有100万个整数，由空格分开，在程序中判断用户输入的整数是否在此文件中。说出最优的方法](#14-%E4%B8%80%E4%B8%AA%E6%96%87%E4%BB%B6%E4%B8%AD%E6%9C%89100%E4%B8%87%E4%B8%AA%E6%95%B4%E6%95%B0%E7%94%B1%E7%A9%BA%E6%A0%BC%E5%88%86%E5%BC%80%E5%9C%A8%E7%A8%8B%E5%BA%8F%E4%B8%AD%E5%88%A4%E6%96%AD%E7%94%A8%E6%88%B7%E8%BE%93%E5%85%A5%E7%9A%84%E6%95%B4%E6%95%B0%E6%98%AF%E5%90%A6%E5%9C%A8%E6%AD%A4%E6%96%87%E4%BB%B6%E4%B8%AD%E8%AF%B4%E5%87%BA%E6%9C%80%E4%BC%98%E7%9A%84%E6%96%B9%E6%B3%95)
    - [15. 一张Bitmap所占内存以及内存占用的计算](#15-%E4%B8%80%E5%BC%A0bitmap%E6%89%80%E5%8D%A0%E5%86%85%E5%AD%98%E4%BB%A5%E5%8F%8A%E5%86%85%E5%AD%98%E5%8D%A0%E7%94%A8%E7%9A%84%E8%AE%A1%E7%AE%97)
    - [16. 2000万个整数，找出第五十大的数字](#16-2000%E4%B8%87%E4%B8%AA%E6%95%B4%E6%95%B0%E6%89%BE%E5%87%BA%E7%AC%AC%E4%BA%94%E5%8D%81%E5%A4%A7%E7%9A%84%E6%95%B0%E5%AD%97)
    - [17. 求1000以内的水仙花数以及40亿以内的水仙花数](#17-%E6%B1%821000%E4%BB%A5%E5%86%85%E7%9A%84%E6%B0%B4%E4%BB%99%E8%8A%B1%E6%95%B0%E4%BB%A5%E5%8F%8A40%E4%BA%BF%E4%BB%A5%E5%86%85%E7%9A%84%E6%B0%B4%E4%BB%99%E8%8A%B1%E6%95%B0)
    - [18. 烧一根不均匀的绳，从头烧到尾总共需要1个小时。现在有若干条材质相同的绳子，问如何用烧绳的方法来计时一个小时十五分钟呢](#18-%E7%83%A7%E4%B8%80%E6%A0%B9%E4%B8%8D%E5%9D%87%E5%8C%80%E7%9A%84%E7%BB%B3%E4%BB%8E%E5%A4%B4%E7%83%A7%E5%88%B0%E5%B0%BE%E6%80%BB%E5%85%B1%E9%9C%80%E8%A6%811%E4%B8%AA%E5%B0%8F%E6%97%B6%E7%8E%B0%E5%9C%A8%E6%9C%89%E8%8B%A5%E5%B9%B2%E6%9D%A1%E6%9D%90%E8%B4%A8%E7%9B%B8%E5%90%8C%E7%9A%84%E7%BB%B3%E5%AD%90%E9%97%AE%E5%A6%82%E4%BD%95%E7%94%A8%E7%83%A7%E7%BB%B3%E7%9A%84%E6%96%B9%E6%B3%95%E6%9D%A5%E8%AE%A1%E6%97%B6%E4%B8%80%E4%B8%AA%E5%B0%8F%E6%97%B6%E5%8D%81%E4%BA%94%E5%88%86%E9%92%9F%E5%91%A2)
    - [19. 5枚硬币，2正3反如何划分为两堆然后通过翻转让两堆中正面向上的硬8币和反面向上的硬币个数相同](#19-5%E6%9E%9A%E7%A1%AC%E5%B8%812%E6%AD%A33%E5%8F%8D%E5%A6%82%E4%BD%95%E5%88%92%E5%88%86%E4%B8%BA%E4%B8%A4%E5%A0%86%E7%84%B6%E5%90%8E%E9%80%9A%E8%BF%87%E7%BF%BB%E8%BD%AC%E8%AE%A9%E4%B8%A4%E5%A0%86%E4%B8%AD%E6%AD%A3%E9%9D%A2%E5%90%91%E4%B8%8A%E7%9A%84%E7%A1%AC8%E5%B8%81%E5%92%8C%E5%8F%8D%E9%9D%A2%E5%90%91%E4%B8%8A%E7%9A%84%E7%A1%AC%E5%B8%81%E4%B8%AA%E6%95%B0%E7%9B%B8%E5%90%8C)
    - [20.时针走一圈，时针分针重合几次](#20%E6%97%B6%E9%92%88%E8%B5%B0%E4%B8%80%E5%9C%88%E6%97%B6%E9%92%88%E5%88%86%E9%92%88%E9%87%8D%E5%90%88%E5%87%A0%E6%AC%A1)
  - [面试真题](#%E9%9D%A2%E8%AF%95%E7%9C%9F%E9%A2%98)
    - [1. 如何减少对第三方框架的耦合](#1-%E5%A6%82%E4%BD%95%E5%87%8F%E5%B0%91%E5%AF%B9%E7%AC%AC%E4%B8%89%E6%96%B9%E6%A1%86%E6%9E%B6%E7%9A%84%E8%80%A6%E5%90%88)
    - [2. 手写单例，DCL为什么要加Volatile关键字](#2-%E6%89%8B%E5%86%99%E5%8D%95%E4%BE%8Bdcl%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E5%8A%A0volatile%E5%85%B3%E9%94%AE%E5%AD%97)
    - [3. 直接在Activity Sleep 5000ms,再post一个runable会不会ANR](#3-%E7%9B%B4%E6%8E%A5%E5%9C%A8activity-sleep-5000ms%E5%86%8Dpost%E4%B8%80%E4%B8%AArunable%E4%BC%9A%E4%B8%8D%E4%BC%9Aanr)
    - [4. 如何监听ANR](#4-%E5%A6%82%E4%BD%95%E7%9B%91%E5%90%ACanr)
    - [5. 组件化如何实现组件间通信](#5-%E7%BB%84%E4%BB%B6%E5%8C%96%E5%A6%82%E4%BD%95%E5%AE%9E%E7%8E%B0%E7%BB%84%E4%BB%B6%E9%97%B4%E9%80%9A%E4%BF%A1)
    - [6. 安装包优化](#6-%E5%AE%89%E8%A3%85%E5%8C%85%E4%BC%98%E5%8C%96)
    - [7. 如果有A,B,C,D,E五个步骤,每个步骤都需要操作对应请求,用哪种设计模式](#7-%E5%A6%82%E6%9E%9C%E6%9C%89abcde%E4%BA%94%E4%B8%AA%E6%AD%A5%E9%AA%A4%E6%AF%8F%E4%B8%AA%E6%AD%A5%E9%AA%A4%E9%83%BD%E9%9C%80%E8%A6%81%E6%93%8D%E4%BD%9C%E5%AF%B9%E5%BA%94%E8%AF%B7%E6%B1%82%E7%94%A8%E5%93%AA%E7%A7%8D%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F)
    - [8. 如果让你设计一个app,打算怎么设计](#8-%E5%A6%82%E6%9E%9C%E8%AE%A9%E4%BD%A0%E8%AE%BE%E8%AE%A1%E4%B8%80%E4%B8%AAapp%E6%89%93%E7%AE%97%E6%80%8E%E4%B9%88%E8%AE%BE%E8%AE%A1)
    - [9. Serial使用的哪一种回收算法](#9-serial%E4%BD%BF%E7%94%A8%E7%9A%84%E5%93%AA%E4%B8%80%E7%A7%8D%E5%9B%9E%E6%94%B6%E7%AE%97%E6%B3%95)
    - [10. Android主线程是怎么启动的](#10-android%E4%B8%BB%E7%BA%BF%E7%A8%8B%E6%98%AF%E6%80%8E%E4%B9%88%E5%90%AF%E5%8A%A8%E7%9A%84)
    - [11. dex是如何转为机器码的](#11-dex%E6%98%AF%E5%A6%82%E4%BD%95%E8%BD%AC%E4%B8%BA%E6%9C%BA%E5%99%A8%E7%A0%81%E7%9A%84)
    - [12. llvm编译是如何优化代码的](#12-llvm%E7%BC%96%E8%AF%91%E6%98%AF%E5%A6%82%E4%BD%95%E4%BC%98%E5%8C%96%E4%BB%A3%E7%A0%81%E7%9A%84)
    - [13. 静态类的静态方法能不能被子类重写，为什么](#13-%E9%9D%99%E6%80%81%E7%B1%BB%E7%9A%84%E9%9D%99%E6%80%81%E6%96%B9%E6%B3%95%E8%83%BD%E4%B8%8D%E8%83%BD%E8%A2%AB%E5%AD%90%E7%B1%BB%E9%87%8D%E5%86%99%E4%B8%BA%E4%BB%80%E4%B9%88)
    - [14. Linux的启动流程](#14-linux%E7%9A%84%E5%90%AF%E5%8A%A8%E6%B5%81%E7%A8%8B)
    - [15. looper的唤醒是在Java还是Native层,怎么做到的](#15-looper%E7%9A%84%E5%94%A4%E9%86%92%E6%98%AF%E5%9C%A8java%E8%BF%98%E6%98%AFnative%E5%B1%82%E6%80%8E%E4%B9%88%E5%81%9A%E5%88%B0%E7%9A%84)
    - [16. 跨平台开发熟不熟悉](#16-%E8%B7%A8%E5%B9%B3%E5%8F%B0%E5%BC%80%E5%8F%91%E7%86%9F%E4%B8%8D%E7%86%9F%E6%82%89)
    - [17. 如何提高海外用户的访问速度,假设服务器在深圳](#17-%E5%A6%82%E4%BD%95%E6%8F%90%E9%AB%98%E6%B5%B7%E5%A4%96%E7%94%A8%E6%88%B7%E7%9A%84%E8%AE%BF%E9%97%AE%E9%80%9F%E5%BA%A6%E5%81%87%E8%AE%BE%E6%9C%8D%E5%8A%A1%E5%99%A8%E5%9C%A8%E6%B7%B1%E5%9C%B3)
    - [18. 红包随机算法 是怎么做到的](#18-%E7%BA%A2%E5%8C%85%E9%9A%8F%E6%9C%BA%E7%AE%97%E6%B3%95-%E6%98%AF%E6%80%8E%E4%B9%88%E5%81%9A%E5%88%B0%E7%9A%84)
    - [19. 手写一个二叉树的深度度优先遍历,递归 非递归](#19-%E6%89%8B%E5%86%99%E4%B8%80%E4%B8%AA%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%B7%B1%E5%BA%A6%E5%BA%A6%E4%BC%98%E5%85%88%E9%81%8D%E5%8E%86%E9%80%92%E5%BD%92-%E9%9D%9E%E9%80%92%E5%BD%92)
    - [20. Android中LocalServerSocket是干什么用的](#20-android%E4%B8%ADlocalserversocket%E6%98%AF%E5%B9%B2%E4%BB%80%E4%B9%88%E7%94%A8%E7%9A%84)
    - [21. binder的Native层代码](#21-binder%E7%9A%84native%E5%B1%82%E4%BB%A3%E7%A0%81)
    - [22. Linux有哪些RPC机制](#22-linux%E6%9C%89%E5%93%AA%E4%BA%9Brpc%E6%9C%BA%E5%88%B6)
    - [23. 为什么android使用了Binder机制没采用共享内存](#23-%E4%B8%BA%E4%BB%80%E4%B9%88android%E4%BD%BF%E7%94%A8%E4%BA%86binder%E6%9C%BA%E5%88%B6%E6%B2%A1%E9%87%87%E7%94%A8%E5%85%B1%E4%BA%AB%E5%86%85%E5%AD%98)
    - [24. 如果让你设计一套进程间通信的机制,你会怎么设计](#24-%E5%A6%82%E6%9E%9C%E8%AE%A9%E4%BD%A0%E8%AE%BE%E8%AE%A1%E4%B8%80%E5%A5%97%E8%BF%9B%E7%A8%8B%E9%97%B4%E9%80%9A%E4%BF%A1%E7%9A%84%E6%9C%BA%E5%88%B6%E4%BD%A0%E4%BC%9A%E6%80%8E%E4%B9%88%E8%AE%BE%E8%AE%A1)
    - [25. Linux的模块动态加载机制是怎么实现的](#25-linux%E7%9A%84%E6%A8%A1%E5%9D%97%E5%8A%A8%E6%80%81%E5%8A%A0%E8%BD%BD%E6%9C%BA%E5%88%B6%E6%98%AF%E6%80%8E%E4%B9%88%E5%AE%9E%E7%8E%B0%E7%9A%84)
    - [26. 一个物理屏划分为三个逻辑屏,是靠谁来分发事件的](#26-%E4%B8%80%E4%B8%AA%E7%89%A9%E7%90%86%E5%B1%8F%E5%88%92%E5%88%86%E4%B8%BA%E4%B8%89%E4%B8%AA%E9%80%BB%E8%BE%91%E5%B1%8F%E6%98%AF%E9%9D%A0%E8%B0%81%E6%9D%A5%E5%88%86%E5%8F%91%E4%BA%8B%E4%BB%B6%E7%9A%84)
    - [27. ConcurrentHashMap是不是绝对的线程安全](#27-concurrenthashmap%E6%98%AF%E4%B8%8D%E6%98%AF%E7%BB%9D%E5%AF%B9%E7%9A%84%E7%BA%BF%E7%A8%8B%E5%AE%89%E5%85%A8)
    - [28. 线程池是如何管理线程状态的](#28-%E7%BA%BF%E7%A8%8B%E6%B1%A0%E6%98%AF%E5%A6%82%E4%BD%95%E7%AE%A1%E7%90%86%E7%BA%BF%E7%A8%8B%E7%8A%B6%E6%80%81%E7%9A%84)
    - [29. Kotlin的访问权限](#29-kotlin%E7%9A%84%E8%AE%BF%E9%97%AE%E6%9D%83%E9%99%90)
    - [30. Koltin为什么比Java更安全](#30-koltin%E4%B8%BA%E4%BB%80%E4%B9%88%E6%AF%94java%E6%9B%B4%E5%AE%89%E5%85%A8)
    - [31. Koltin比Java好在哪](#31-koltin%E6%AF%94java%E5%A5%BD%E5%9C%A8%E5%93%AA)
    - [32. 为什么操作数栈是Thread-Private](#32-%E4%B8%BA%E4%BB%80%E4%B9%88%E6%93%8D%E4%BD%9C%E6%95%B0%E6%A0%88%E6%98%AFthread-private)
    - [33. 计算二叉树的深度](#33-%E8%AE%A1%E7%AE%97%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%B7%B1%E5%BA%A6)
    - [34. 动态代理静态代理区别](#34-%E5%8A%A8%E6%80%81%E4%BB%A3%E7%90%86%E9%9D%99%E6%80%81%E4%BB%A3%E7%90%86%E5%8C%BA%E5%88%AB)
    - [35. 启动优化怎么做的](#35-%E5%90%AF%E5%8A%A8%E4%BC%98%E5%8C%96%E6%80%8E%E4%B9%88%E5%81%9A%E7%9A%84)
    - [36. http有哪几种版本,版本间有什么区别。https跟http有什么区别](#36-http%E6%9C%89%E5%93%AA%E5%87%A0%E7%A7%8D%E7%89%88%E6%9C%AC%E7%89%88%E6%9C%AC%E9%97%B4%E6%9C%89%E4%BB%80%E4%B9%88%E5%8C%BA%E5%88%ABhttps%E8%B7%9Fhttp%E6%9C%89%E4%BB%80%E4%B9%88%E5%8C%BA%E5%88%AB)
    - [37. apk为什么要签名,v1跟v2签名的区别](#37-apk%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E7%AD%BE%E5%90%8Dv1%E8%B7%9Fv2%E7%AD%BE%E5%90%8D%E7%9A%84%E5%8C%BA%E5%88%AB)
    - [38. dex到odex为什么不能在编译期优化](#38-dex%E5%88%B0odex%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%8D%E8%83%BD%E5%9C%A8%E7%BC%96%E8%AF%91%E6%9C%9F%E4%BC%98%E5%8C%96)
    - [39. 热修复原理](#39-%E7%83%AD%E4%BF%AE%E5%A4%8D%E5%8E%9F%E7%90%86)
    - [40. 安装包优化有哪几种方式](#40-%E5%AE%89%E8%A3%85%E5%8C%85%E4%BC%98%E5%8C%96%E6%9C%89%E5%93%AA%E5%87%A0%E7%A7%8D%E6%96%B9%E5%BC%8F)
    - [41. 如何应对弱网环境](#41-%E5%A6%82%E4%BD%95%E5%BA%94%E5%AF%B9%E5%BC%B1%E7%BD%91%E7%8E%AF%E5%A2%83)
    - [42. android数据存储方式](#42-android%E6%95%B0%E6%8D%AE%E5%AD%98%E5%82%A8%E6%96%B9%E5%BC%8F)
    - [43. 如果一个app无法访问网络,你怎么做数据存储](#43-%E5%A6%82%E6%9E%9C%E4%B8%80%E4%B8%AAapp%E6%97%A0%E6%B3%95%E8%AE%BF%E9%97%AE%E7%BD%91%E7%BB%9C%E4%BD%A0%E6%80%8E%E4%B9%88%E5%81%9A%E6%95%B0%E6%8D%AE%E5%AD%98%E5%82%A8)
    - [44. DVM跟JVM的区别](#44-dvm%E8%B7%9Fjvm%E7%9A%84%E5%8C%BA%E5%88%AB)
      - [Java虚拟机](#java%E8%99%9A%E6%8B%9F%E6%9C%BA)
      - [Dalvik虚拟机](#dalvik%E8%99%9A%E6%8B%9F%E6%9C%BA)
    - [45. React Native跟原生开发的优劣](#45-react-native%E8%B7%9F%E5%8E%9F%E7%94%9F%E5%BC%80%E5%8F%91%E7%9A%84%E4%BC%98%E5%8A%A3)
    - [46. Android 沉浸式状态栏 怎么实现的](#46-android-%E6%B2%89%E6%B5%B8%E5%BC%8F%E7%8A%B6%E6%80%81%E6%A0%8F-%E6%80%8E%E4%B9%88%E5%AE%9E%E7%8E%B0%E7%9A%84)
    - [47. 事件处理函数有哪几个,父View 子View 监听同一个事件,重写哪些方法。在哪个View重写](#47-%E4%BA%8B%E4%BB%B6%E5%A4%84%E7%90%86%E5%87%BD%E6%95%B0%E6%9C%89%E5%93%AA%E5%87%A0%E4%B8%AA%E7%88%B6view-%E5%AD%90view-%E7%9B%91%E5%90%AC%E5%90%8C%E4%B8%80%E4%B8%AA%E4%BA%8B%E4%BB%B6%E9%87%8D%E5%86%99%E5%93%AA%E4%BA%9B%E6%96%B9%E6%B3%95%E5%9C%A8%E5%93%AA%E4%B8%AAview%E9%87%8D%E5%86%99)
    - [48. ViewRootImpl接受事件吗](#48-viewrootimpl%E6%8E%A5%E5%8F%97%E4%BA%8B%E4%BB%B6%E5%90%97)
    - [49. 利用logging监听方法耗时，会不会让app增大延迟](#49-%E5%88%A9%E7%94%A8logging%E7%9B%91%E5%90%AC%E6%96%B9%E6%B3%95%E8%80%97%E6%97%B6%E4%BC%9A%E4%B8%8D%E4%BC%9A%E8%AE%A9app%E5%A2%9E%E5%A4%A7%E5%BB%B6%E8%BF%9F)
    - [50. eventbus为什么要用CopyOnWriteList](#50-eventbus%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E7%94%A8copyonwritelist)
    - [51. 插件化怎么加载资源的](#51-%E6%8F%92%E4%BB%B6%E5%8C%96%E6%80%8E%E4%B9%88%E5%8A%A0%E8%BD%BD%E8%B5%84%E6%BA%90%E7%9A%84)
    - [52. JVM怎么保证gc效率跟线程运行效率的](#52-jvm%E6%80%8E%E4%B9%88%E4%BF%9D%E8%AF%81gc%E6%95%88%E7%8E%87%E8%B7%9F%E7%BA%BF%E7%A8%8B%E8%BF%90%E8%A1%8C%E6%95%88%E7%8E%87%E7%9A%84)
    - [53. 如果android没用对应的view,flutter能运行吗](#53-%E5%A6%82%E6%9E%9Candroid%E6%B2%A1%E7%94%A8%E5%AF%B9%E5%BA%94%E7%9A%84viewflutter%E8%83%BD%E8%BF%90%E8%A1%8C%E5%90%97)
    - [54. 接口暴露,但是不让别人调用,有哪些办法](#54-%E6%8E%A5%E5%8F%A3%E6%9A%B4%E9%9C%B2%E4%BD%86%E6%98%AF%E4%B8%8D%E8%AE%A9%E5%88%AB%E4%BA%BA%E8%B0%83%E7%94%A8%E6%9C%89%E5%93%AA%E4%BA%9B%E5%8A%9E%E6%B3%95)
    - [55. 为什么采用flatbuffer? 比Json好在哪里](#55-%E4%B8%BA%E4%BB%80%E4%B9%88%E9%87%87%E7%94%A8flatbuffer-%E6%AF%94json%E5%A5%BD%E5%9C%A8%E5%93%AA%E9%87%8C)
    - [56. 如何处理Crash,NativeCrash呢?Google是怎么做到的?如果上报过程中再次产生Crash能不能捕捉到](#56-%E5%A6%82%E4%BD%95%E5%A4%84%E7%90%86crashnativecrash%E5%91%A2google%E6%98%AF%E6%80%8E%E4%B9%88%E5%81%9A%E5%88%B0%E7%9A%84%E5%A6%82%E6%9E%9C%E4%B8%8A%E6%8A%A5%E8%BF%87%E7%A8%8B%E4%B8%AD%E5%86%8D%E6%AC%A1%E4%BA%A7%E7%94%9Fcrash%E8%83%BD%E4%B8%8D%E8%83%BD%E6%8D%95%E6%8D%89%E5%88%B0)
    - [57. uncaughtException是被谁调用的,如果再次崩溃能不能捕获到](#57-uncaughtexception%E6%98%AF%E8%A2%AB%E8%B0%81%E8%B0%83%E7%94%A8%E7%9A%84%E5%A6%82%E6%9E%9C%E5%86%8D%E6%AC%A1%E5%B4%A9%E6%BA%83%E8%83%BD%E4%B8%8D%E8%83%BD%E6%8D%95%E8%8E%B7%E5%88%B0)
    - [58. Linux是怎么知道app崩溃的,如果想要在被kill前 做一些耗时操作,该怎么做](#58-linux%E6%98%AF%E6%80%8E%E4%B9%88%E7%9F%A5%E9%81%93app%E5%B4%A9%E6%BA%83%E7%9A%84%E5%A6%82%E6%9E%9C%E6%83%B3%E8%A6%81%E5%9C%A8%E8%A2%ABkill%E5%89%8D-%E5%81%9A%E4%B8%80%E4%BA%9B%E8%80%97%E6%97%B6%E6%93%8D%E4%BD%9C%E8%AF%A5%E6%80%8E%E4%B9%88%E5%81%9A)
    - [59. 考虑设计一个crash捕捉模块](#59-%E8%80%83%E8%99%91%E8%AE%BE%E8%AE%A1%E4%B8%80%E4%B8%AAcrash%E6%8D%95%E6%8D%89%E6%A8%A1%E5%9D%97)
    - [60. 100万个数字求100个最大值](#60-100%E4%B8%87%E4%B8%AA%E6%95%B0%E5%AD%97%E6%B1%82100%E4%B8%AA%E6%9C%80%E5%A4%A7%E5%80%BC)
    - [61. 手写快速排序算法](#61-%E6%89%8B%E5%86%99%E5%BF%AB%E9%80%9F%E6%8E%92%E5%BA%8F%E7%AE%97%E6%B3%95)
    - [62. 如何防止DNS劫持](#62-%E5%A6%82%E4%BD%95%E9%98%B2%E6%AD%A2dns%E5%8A%AB%E6%8C%81)
    - [63. 如果让你实现一个调试器,你会怎么设计?静态调试?动态调试呢](#63-%E5%A6%82%E6%9E%9C%E8%AE%A9%E4%BD%A0%E5%AE%9E%E7%8E%B0%E4%B8%80%E4%B8%AA%E8%B0%83%E8%AF%95%E5%99%A8%E4%BD%A0%E4%BC%9A%E6%80%8E%E4%B9%88%E8%AE%BE%E8%AE%A1%E9%9D%99%E6%80%81%E8%B0%83%E8%AF%95%E5%8A%A8%E6%80%81%E8%B0%83%E8%AF%95%E5%91%A2)
    - [64. 一个应用程序安装到手机上的过程发生了什么](#64-%E4%B8%80%E4%B8%AA%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E5%AE%89%E8%A3%85%E5%88%B0%E6%89%8B%E6%9C%BA%E4%B8%8A%E7%9A%84%E8%BF%87%E7%A8%8B%E5%8F%91%E7%94%9F%E4%BA%86%E4%BB%80%E4%B9%88)
    - [65. RecyclerView的缓存机制](#65-recyclerview%E7%9A%84%E7%BC%93%E5%AD%98%E6%9C%BA%E5%88%B6)
    - [66. 生产者和消费者模型如何理解](#66-%E7%94%9F%E4%BA%A7%E8%80%85%E5%92%8C%E6%B6%88%E8%B4%B9%E8%80%85%E6%A8%A1%E5%9E%8B%E5%A6%82%E4%BD%95%E7%90%86%E8%A7%A3)
    - [67.六大设计原则](#67%E5%85%AD%E5%A4%A7%E8%AE%BE%E8%AE%A1%E5%8E%9F%E5%88%99)
    - [68. LeakCanary监控原理解析](#68-leakcanary%E7%9B%91%E6%8E%A7%E5%8E%9F%E7%90%86%E8%A7%A3%E6%9E%90)
    - [69. Android 项目中 asset 目录和 res 目录有什么区别](#69-android-%E9%A1%B9%E7%9B%AE%E4%B8%AD-asset-%E7%9B%AE%E5%BD%95%E5%92%8C-res-%E7%9B%AE%E5%BD%95%E6%9C%89%E4%BB%80%E4%B9%88%E5%8C%BA%E5%88%AB)
    - [70. SparseArray原理](#70-sparsearray%E5%8E%9F%E7%90%86)
    - [71.  invalidate()、requestLayout() 区别](#71--invalidaterequestlayout-%E5%8C%BA%E5%88%AB)
    - [72. ArrayList 怎么实现线程安全](#72-arraylist-%E6%80%8E%E4%B9%88%E5%AE%9E%E7%8E%B0%E7%BA%BF%E7%A8%8B%E5%AE%89%E5%85%A8)
    - [73. RelativeLayout与LinerLayout的区别](#73-relativelayout%E4%B8%8Elinerlayout%E7%9A%84%E5%8C%BA%E5%88%AB)
    - [74. 一个无限单向链表如何计算长度，如果有环如何计算长度](#74-%E4%B8%80%E4%B8%AA%E6%97%A0%E9%99%90%E5%8D%95%E5%90%91%E9%93%BE%E8%A1%A8%E5%A6%82%E4%BD%95%E8%AE%A1%E7%AE%97%E9%95%BF%E5%BA%A6%E5%A6%82%E6%9E%9C%E6%9C%89%E7%8E%AF%E5%A6%82%E4%BD%95%E8%AE%A1%E7%AE%97%E9%95%BF%E5%BA%A6)
    - [75. Tinker 为什么需要重启](#75-tinker-%E4%B8%BA%E4%BB%80%E4%B9%88%E9%9C%80%E8%A6%81%E9%87%8D%E5%90%AF)
    - [76. TCP怎么做长连接](#76-tcp%E6%80%8E%E4%B9%88%E5%81%9A%E9%95%BF%E8%BF%9E%E6%8E%A5)
    - [77. 如果子View已经处理了事件，父View怎么拦截子View事件](#77-%E5%A6%82%E6%9E%9C%E5%AD%90view%E5%B7%B2%E7%BB%8F%E5%A4%84%E7%90%86%E4%BA%86%E4%BA%8B%E4%BB%B6%E7%88%B6view%E6%80%8E%E4%B9%88%E6%8B%A6%E6%88%AA%E5%AD%90view%E4%BA%8B%E4%BB%B6)
    - [78. 线程状态转换图](#78-%E7%BA%BF%E7%A8%8B%E7%8A%B6%E6%80%81%E8%BD%AC%E6%8D%A2%E5%9B%BE)
    - [79. onNewIntent() 调用时机](#79-onnewintent-%E8%B0%83%E7%94%A8%E6%97%B6%E6%9C%BA)
    - [80. setContentView()后面的流程](#80-setcontentview%E5%90%8E%E9%9D%A2%E7%9A%84%E6%B5%81%E7%A8%8B)
    - [81. WindowManager.addView()，View.getParent()是谁](#81-windowmanageraddviewviewgetparent%E6%98%AF%E8%B0%81)
    - [82. 有多个线程1、2、3、4，1、2、3 并行完后与 4 串行，至少 3 种方式实现](#82-%E6%9C%89%E5%A4%9A%E4%B8%AA%E7%BA%BF%E7%A8%8B1234123-%E5%B9%B6%E8%A1%8C%E5%AE%8C%E5%90%8E%E4%B8%8E-4-%E4%B8%B2%E8%A1%8C%E8%87%B3%E5%B0%91-3-%E7%A7%8D%E6%96%B9%E5%BC%8F%E5%AE%9E%E7%8E%B0)
    - [83. TCP三次握手、四次挥手](#83-tcp%E4%B8%89%E6%AC%A1%E6%8F%A1%E6%89%8B%E5%9B%9B%E6%AC%A1%E6%8C%A5%E6%89%8B)
    - [84. Android系统启动流程](#84-android%E7%B3%BB%E7%BB%9F%E5%90%AF%E5%8A%A8%E6%B5%81%E7%A8%8B)
    - [85. epoll 机制的原理](#85-epoll-%E6%9C%BA%E5%88%B6%E7%9A%84%E5%8E%9F%E7%90%86)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# JAVA基础知识点

## JVM相关

### 1. Java内存结构及分区

运行时数据区分为：

- 共享数据区：
  - 方法区：类信息、常量、静态变量、编译后的代码
    - 常量池：编译器生成的各种字面量和符号引用
  - 堆：对象分配的内存区域

- 线程私有：
  - 程序计数器：线程中记录执行的虚拟机字节码地址（在执行本地方法时，程序计数器为空）
  - 虚拟机栈：线程中方法执行的内存区，每个方法执行的时候都要在此创建栈帧
  - 本地方法栈：虚拟机Native方法执行的内存区域

### 2. Java对象的创建、存储及访问

**对象创建（遇见关键字new）：**

1. 类加载检查

   1. 如果没有加载类则先进行类加载

2. 为对象分配内存

   - 在堆中分配

   - 如果堆内存**规整**：采用**指针碰撞**方式分配

   - 如果堆内存**不规整**：采用**空闲列表**方式分配

     *（内存是否规整取决于垃圾收集器是否带有压缩整理功能）*

3. 将内存空间初始化为零值（不包括对象头）

4. 对对象进行必要的设置（hash码、对象分代年龄等）

**对象内存布局：**

1. 对象头

   - 如哈希码（`HashCode`）、GC分代年龄、锁状态标志、线程持有的锁、偏向线程ID、偏向时间戳等（8字节）
   - 对象指向它的类元数据的指针（4字节）
   - 如果对象是数组：记录数组长度的数据（4字节）

2. 对象数据

   对象真正有效的信息，各基本数据类型变量的大小相加、每个引用数据类型占4字节

3. 对齐填充

   如果对象的大小不是8的倍数，则占位补满

**对象的访问：**

通过栈上的引用类型数据来访问堆上的对象。

虚拟机的实现不同分为两种访问方式：

- 句柄访问
  1. 栈中引用类型存储的是对象的句柄地址
  2. 程序通过栈中的引用类型获取对象的句柄地址，然后根据句柄地址去定位、访问对象
- 直接指针访问
  1. 栈中的引用类型存储对象的地址

### 3. Java判断对象是否存活及垃圾回收算法(GC)

- 可达性分析法（引用计数有缺陷）
- GC Roots
  - 栈中引用的对象
  - 方法区中静态属性、常量引用的对象
- 在可达性分析算法中，要真正宣告一个对象死亡，至少要经历两次标记过程
  - finalize()
- 标志-清除
- 标志-整理
- 复制
- 分代收集

### 4. Jvm中的常⻅的垃圾回收器

### 5. Java类加载过程

1. 加载：查找并加载类的二进制文件，在java堆中创建一个类的对象
2. 连接：包括三部分内容
   - 验证：对文件格式、元数据、字节码、符号引用进行验证
   - 准备：为类的静态变量分配内存，并将其初始化为默认值
   - 解析：把类中的符号引用转换为直接引用
3. 初始化：为类的静态变量赋予正确的初始值
4. 使用：new出对象并使用
5. 卸载：执行垃圾回收

### 6. Java类加载器(双亲委派模型)

- 启动类加载器：Bootstrap ClassLoader

  C实现的，加载Java的核心类库

- 扩展类加载器：Extension ClassLoader

  Java实现的，负责加载jre/lib/ext下的类

- 应用程序类加载器：Application ClassLoader

  负责加载用户类路径下的类，开发者可以直接使用该类加载器
  
**双亲委派：**如果一个类加载器需要加载类，那么首先它会把这个类请求委派给父类加载器去完成，每一层都是如此。一直递归到顶层，当父加载器无法完成这个请求时，子类才会尝试去加载。

*双亲委派模型不是一种强制性约束，也就是你不这么做也不会报错怎样的，它是一种JAVA设计者推荐使用类加载器的方式。*

## 集合相关

### 1. ArrayList分析

- 内部数组实现

- 默认容量10
- 每次扩容为之前的1.5倍
- 数据减少的时候容量不会减少
- 随机访问、尾部插入删除元素时间复杂度O(1)
- 中间插入、删除元素时间复杂度O(n)

### 2. LinkedList分析

- 内部双向链表实现
- 可实现队列和栈的功能
- 首尾节点插入删除元素时间复杂度O(1)
- 中间节点插入删除元素时间复杂度O(n)

### 3. HashMap分析

- 扩容条件：当前元素>数组长度*扩容系数
- 内部结构：数组+链表，当链表长度大于8且扩容达到64时，链表会转为红黑树
- hash()方法如何设计的：Key的hashCode与hashCode的高16位进行异或，减少hash冲突
- 为什么数组长度/扩容的容量为2的幂次：为了存取高效、减少碰撞、让数据均匀分布在每个链表中，所以元素对于数组的位置计数使用元素key的hash对数组长度进行取模操作，并使用位移操作进行计算。当length为2的幂次时，length的二进制位1000…00，那么length-1位111…11，这样在&hash的时候可以减小碰撞。

### 4. HashTable分析

### 5. LinkedHashMap分析

### 6. HashSet分析

### 7. LinkedHashSet分析

### 8. ArrayMap、SparseMap、与HashMap的对比

### 9. ConcurrentHashMap分析

### 10. SpareArray 的实现原理

### 11. ArrayBlockingQueue、LinkedBlockingQueue

## 并发相关

### 1. Java内存模型

- 主内存：所有的变量都存储在主内存中
- 工作内存：每个线程独立拥有，保存该线程使用的主内存的变量的副本拷贝
- 内存间的交互操作：8个指令
- 多线程环境下共享内存一致性：原子性、可见性、有序性
- 先行发生原则

### 2. volatile原理

### 3. Synchronized的原理

### 4. AQS原理

### 5. Condition原理

### 6. ReentrantLock 原理

可以设置是公平还是非公平，自旋锁

### 7. 公平锁与非公平锁

公平锁中维护了一个线程队列，当上一个线程释放锁后，队列中的线程会fifo的去拿锁

非公平锁没有这个队列，当上一个线程释放锁后，等待锁的线程会去抢占锁

### 8. ReentrantReadWriteLock原理

## 线程相关

### 1. 线程的启动和终止

**启动**：调用start()方法

**终止**：不建议用stop()方法。方法一：让线程的任务完成自动停止；方法二：使用一个标志位，当线程外部将标志改变，线程就停止运行；方法三：使用Thread.intercept()，中断线程，并且线程中处理InterceptException异常，在异常的处理中进行数据的保存并终止线程。

### 2. 线程间通信

- synchronized/volatile
- Wait+notify
- 管道通信

### 3. 等待/通知机制

### 4. 什么是深拷贝和浅拷贝

### 5. 多线程断点续传的实现原理

## 线程池相关

### 1. 使用线程池的原因

线程池可以减少创建和销毁线程的次数，从而减少系统资源的消耗

### 2. 线程池内部原理

当一个任务提交到线程池时
a. 首先判断核心线程池中的线程是否已经满了，如果没满，则创建一个核心线程执行任务，否则进入下一步
b. 判断工作队列是否已满，没有满则加入工作队列，否则执行下一步
c. 判断线程数是否达到了最大值，如果不是，则创建非核心线程执行任务，否则执行饱和策略，默认抛出异常

### 3. 线程池中的几种重要的参数及流程说明

- 核心线程个数

- 最大线程个数

- 线程执行完后多久销毁

- 时间单位

- 任务队列

- 创建任务的工厂

- 拒绝策略

### 4. 线程池中几种常⻅的工作队列

- ArrayBlockingQueue

- LinkedBlockingQueue

- SychonizedBlockingQueue

- ProitityBlockingQueue

### 5. 几种常⻅的线程池及使用场景

## IO相关

### 1. Socket

### 2. BIO/NIO

# Android基础知识点

## Activity相关

### 1. 典型状况下的生命周期

`onCreate()` -> `onStart()` -> `onResume()` --- `onPause()` -> `onStop()` -> `onDestory()`

### 2. 异常情况下的生命周期

- 异常终止时，在`onStop()`执行之前会调用`onSaveInstanceState()`
- 恢复数据，在`onStart()`之后会调用`onRestoreInstanceState()`

### 3. 异常情况下的数据保存

### 4. 各种情况下跳转到某个Activity时目标Activity及当前Activity的生命周期

### 5. Activity的启动模式及应用场景

- standerd：默认启动模式
- singleTop：栈顶复用，用于聊天界面、登录
- singleTask：栈内复用，用于主页面等
- singleInstance：单独栈，用于服务启动的页面

### 6. 进程和应用生命周期

进程分类：

- 前台进程
- 可见进程
- 服务进程
- 后台进程

### 7. Activity启动流程

1. A进程：startActivity()方法，通过AMS的代理类进入systm_server进程
2. system_server进程：通过AMS解析Activity、处理启动参数、调用Zygotefork目标进程、绑定新进程
3. system_server进程通过目标进程的Applicathread的代理APT的scheduleLaunchActivity()启动目标进程的Activity（本质是目标进程中的ApplicationThread去进行后续启动）
4. ApplicationThread调用ActivityThread启动Activity

## Service相关

### 1. Service的定义及作用

Android 的四大组件之一，后台运行、不可交互、运行在主线程中

### 2. Service两种启动方式 startService、 bindService 区别及生命周期

**startService**：

`onCreate()` --> `onStartCommand()` ------- `onDestroy()`

- 第一次startService的时候会执行onCreate()

- 每次startService会执行onStartCommand()

- Service内部调用stopSelf()或外部调用stopService()就会执行onDestroy()方法，结束service

**bindService**：

`onCreate()` --> `onBind()` ------- `onUnbind()` --> `onDestroy()`

- 第一次bindService的时候会执行onCreate()，onBind()

- bindService()中实现onServiceConnected()完成Client和Service的绑定

- 调用unbindService()将Client与Service断开连接，会执行onUnbind()方法
- 当所有Client都断开连接，service会执行onDestroy()

### 3. Service绑定服务的三种实现方式，扩展Binder类、使用Messenger、使用AIDL

### 4. 关于启动服务与绑定服务间的转换问题 先绑定服务后启动服务、先启动服务后绑定服务

### 5. 服务Service与线程Thread的区别

- Service是Android的组件，运行在主线程，不可以在Service中执行耗时任务，会造成主线程阻塞，最终导致ANR
- Thread是Java的线程，在Android中可以开启线程，完成耗时任务

### 6. Android 5.0以上的隐式启动问题及其解决方案

### 7. 如何保证服务不被杀死

- 前台服务
- 提升进程优先级
- 提升服务优先级
- 监听系统广播拉活
- APP互相拉活
- 多进程包活

### 8. IntentService的使用及原理

IntentService继承与Service。在intentService的onCreate中创建了一个HandlerThread，并且绑定了loop和handler。将handlerMessage方法中抽象出onHandleIntent方法，用于重写实现任务处理。onHandleIntent方法中的任务处理是在onCreate创建的HandlerThread中进行，不会占用主线程，最终实现在service中执行耗时任务。

## BroadcastReceiver相关

### 1. BroadcastReceiver定义及作用、应用场景

Android四大组件之一，接收Android系统或应用发送的广播信息，并处理

### 2. BroadcastReceiver的注册方式

**静态方式**：在AndroidManifest.xml文件中创建，开机后就可以接收广播

**动态方式**：在代码中注册，需要手动注销，只有在注册后才能接收广播

### 3. BroadcastReceiver注册与取消的时机

需要成对出现，在onCreate中创建就需要在onDestroy中取消；onResume对应onPause；onStart对应onStop

### 4. BroadcastReceiver的不同类型

普通广播，系统广播、有序广播、粘性广播、应用类广播

## Fragment相关

### 1. Fragment生命周期

Created: `onAttach()` --> `onCreate()`  --> `onCreateView()` -->  `onActivityCreated()`

Started: `onStart()`

Resumed: `onResume()`

Paused: `onPause()`

Stopped: `onStop()`

Destroyed: `onDestroyView()` --> `onDestroy()` --> `onDetach()`

### 2. Fragment的懒加载

Fragement在配合ViewPager使用的时候，每一个Fragment都会执行onAttach到onResume的生命周期方法，在此会调用接口拉取网络数据，但是多个fragment同时被创建并拉取数据浪费流量、影响性能。

可以使用Fragment的一个非生命周期的回调方法：setUserVisibleHint(boolean isVisibleToUser) 。切换ViewPager是当前的fragment可见是，这个方法会返回true，此时再调用fragment的网络请求。

### 3. Fragment之间的通信

### 4. FragmentPagerAdapter与FragmentStatePagerAdapter的区别

**fragmentPagetAdapter**:

使用add添加fragment，attach将添加到fragment展现出来，使用detach将fragment从视图中移除，此时fragment对象并未销毁。

适用于fragment页面不多且要保存各个页面的状态时

**fragmentStatePagerAdapter**：

使用add将fragment加入视图中，使用remove将fragment移除，会将fragment对象销毁。

适用于fragment数量很多，及时释放对象缓存内存压力

### 5. 为什么不建议直接通过使用new Fragment的方式传入数据

系统调用Fragment的时候是通过发射调用的，反射方法构造的fragment只会是那个无参的构造方法

## 序列化相关

### 1. 序列化与反序列化的定义及区别

### 2. Serializable中serialVersionUID及transient关键字的作用

**serialVersionUID**：
JAVA序列化的机制是通过判断类的serialVersionUID来验证的版本一致的。在进行反序列化时，JVM会把传来的字节流中的serialVersionUID于本地相应实体类的serialVersionUID进行比较。如果相同说明是一致的，可以进行反序列化，否则会出现反序列化版本一致的异常。

**transient**：
标记的成员变量不参与序列化过程，一般用于需要成员变量需要自定义序列化过程的时候。

### 3. 序列化:Parcelable和Serializable差异

| 对比     | Parcelable         | Serializable                     |
| -------- | ------------------ | -------------------------------- |
| 实现方式 | 实现Parcelable接口 | 实现Serializable接口             |
| 属于     | Android特有的      | Java自带的                       |
| 内存消耗 | 优秀               | 一般（通过反射实现，容易频繁GC） |
| 读写数据 | 内存中直接进行读写 | 通过IO流将数据写入硬盘           |
| 持久化   | 不可以             | 可以                             |
| 速度     | 优秀               | 一般                             |

## IPC相关

### 1. 在Android中什么样的情况下会使用多进程模式，如何开启多进程

当应用需要更大的内存是，多进程会分配更多内存；不可见的轻量级私有进程，在后台收发消息，或者做一些耗时的事情，或者开机启动这个进程，然后做监听。

**开启多进程**：在AndroidManifest.xml中对需要独立进程的组件添加process标签

**缺点**：

1. Application的多次重建。

2. 静态成员的失效。

3. 文件共享问题。

4. 断点调试问题。

### 2. Android为什么采用Binder做为IPC机制

### 3. IPC常用方式

   使用Bundle、使用文件共享、使用Messenger、使用AIDL、使用 ContentProvider、使用Socket

### 4. AIDL的语义

### 5. AIDL如何创建 AIDL生成Java文件详细分析

## View事件机制相关

### 1. View的坐标体系

### 2. View滑动的几种方式，使用ScrollTo/ScrollBy、使用动画、改变布局参数

### 3. 弹性滑动的原理及实现

### 4. View的事件分发机制，点击事件的传递规则，事件分发的源码解读

### 5. 处理滑动冲突的场景及解决方法

## View绘制相关

### 1. DecorView、Window、ViewRootImpl等概念

### 2. MeasureSpec概念

### 3. View的工作流程，measure过程、layout过程、draw过程

### 4. 自定义View需要注意的事项

### 5. Activity、Window、View三者之间的关系

## View动画相关

### 1. 常用动画View动画(补间动画)、属性动画与帧动画

### 2. 补间动画与属性动画区别

### 3. 插值器和估值器理解

插值器（Interpolator）：根据时间流逝的百分比计算当前属性值改变的百分比

估值器（TypeEvaluator）根据当前属性改变的百分比来计算改变后的属性值

### 4. 属性动画的工作原理

属性动画要求动画作用的对象提供该属性的set方法，属性动画根据你传递的该属性的初始值和最终值，以动画的效果多次去调用set方法，每次传递给set方法的值都不一样，确切来说是随着时间的推移，所传递的值越来越接近最终值。如果动画的时候没有传递初始值，那么还要提供get方法，因为系统要去拿属性的初始值。

## Handler相关

### 1. Handler机制之ThreadLocal

### 2. Handler机制之Looper、Handler、消息队列如何理解

### 3. Handler机制之Message的发送与取出

### 4. Handler机制之Message及Message的回收机制

### 5. Handler机制之循环消息队列的退出

### 6. Handler机制之内存泄漏

### 7. Handler机制之IdleHandle的理解及使用

## AsyncTask相关

### 1. AsyncTask的使用和注意事项

### 2. AsyncTask几个重要的方法 doInBackgound、onProgressUpdate、onPostExecute等

### 3. AsyncTask的工作原理及源码理解

## SharedPreference相关

### 1. 获取 SharedPreferences 对象过程中，系统做了什么

### 2. getXxx 方法做了什么

### 3. putXxx方法做了什么

### 4. commit/apply方法如何实现同步/异步写磁盘

## Bitmap压缩回收相关

### 1. Bitmap所占内存

bitmap宽 \* 高 \* 一个像素的字节数

### 2. 常用压缩图片方式

### 3. LruCache原理

内部通过LinkedHashMap维护一个缓存队列，当get/put元素的时候都会将元素放入队列的尾部，如果队列超过要求的大小就会将队列头部的元素删除掉以减小缓存。

### 4. DiskLruCache原理

### 5. LinkedHashMap原理

## ListView与RecyclerView相关

### 1. ListView的原理和复用机制

### 2. ListView和RecyclerView的区别

## 数据存储相关

### 1. 常用数据库框架GreenDao,官方Room

### 2. 数据库数据迁移问题

### 3. GreenDao中一对一，一对多，多对多关系

# Android开源框架知识点

## OkHttp相关

### 1. OkHttp的优点

### 2. OkHttp执行请求的整个流程

### 3. OkHttp中的拦截器

### 4. OkHttp中的同步请求与异步请求的理解及其源码

### 5. OkHttp中涉及到的设计模式

### 6. OkHttp底层网络请求实现，socket还是URLConnection

## Retrofit相关

### 1. Retrofit执行请求的整个流程

### 2. Retrofit中ConverterFactory、CallAdapterFactory的理解

### 3. Retrofit中CallAdapter的适配器模式

## RxJava相关

### 1. RxJava常用创建操作符 create、from、just、interval、range等

### 2. RxJava常用组合、合并操作符 combineLatest、join、merge、zip等

### 3. RxJava错误处理操作符 onErrorReturn、onErrorResumeNext、onExceptionResumeNext等

### 4. RxJava过滤操作符 filter、ofType、sample、take等

### 5. Rxjava背压相关理解

### 6. RxJava实际开发中的使用

网络请求轮询、网络请求嵌套回调、从磁盘 / 内存缓存中 获取缓存数据等

## Glide相关

### 1. Glide的执行流程

### 2. Glide的缓存机制

### 3. Glide图片转换

### 4. Glide带进度的图片加载功能

### 5. Glide内存、磁盘缓存，优先级使用

## ButterKnife相关

### 1. Java注解相关Annotation

### 2. Java注解相关之APT工具

### 3. ButterKnife注解框架原理

## EventBus相关

### 1. EventBus原理，及索引类的使用

## Android性能优化

### 1. 性能优化布局优化、绘制优化、线程优化等

### 2. ANR异常

   主线程执行了耗时操作，如BroadcastReceiver(前台广播10s,后台广播为60s)、 Service(前台20s,后台200s)没有处理完相关任务等

1. 耗时的网络访问
2. 大量的数据读写
3. 数据库操作
4. 硬件操作（比如camera)
5. 调用thread的join()方法、sleep()方法、wait()方法或者等待线程锁的时候
6. service binder的数量达到上限
7. system server中发生WatchDog ANR
8. service忙导致超时无响应
9. 其他线程持有锁，导致主线程等待超时
10. 其它线程终止或崩溃导致主线程一直等待

### 3. OOM异常:内存溢出的原因

### 4. 内存泄漏

   内存泄露的几种场景，如单例模式引出的泄露、静态变量导致的泄露、属性动画 导致的内存泄露等

## Android屏幕适配知识点

### 1. 今日头条适配方式

### 2. 宽高限定符适配方式

### 3. smallestWidth适配

## Android打包知识点

### 1. 打包的流程

1. AAPT工具进行资源编译
2. AIDL工具处理AIDL文件，生成相应的java文件
3. javac编译项目源码，生成class文件
4. dx工具将class文件转换dex文件
5. ApkBuilder工具将资源文件、dex文件打包生成apk文件
6. keyStore工具堆生成的帕克文件进行签名
7. zipAlign工具进行对齐处理

### 2. 安卓签名的理解

### 3. Gradle多渠道打包

## Android不同版本特性知识点

### 1. 广播在7.0、8.0、9.0下的适配

### 2. Android 6.0 权限下的适配

### 3. Android 7.0 应用共享文件(FileProvider)

## 网络知识点

### 1. 计算机网络三种体系架构，OSI体系架构(7层)、TCP/IP体系架构(4层)，五层体系架构 TCP的连接管理(三报文握手，四报文握手)

### 2. TCP与UDP的理解与区别

### 3. Http(HyberText Transfer Protocol)基本概念及报文结构

### 4. Http常⻅错误码

200 正确

201 永久重定向

202 临时重定向

304 客户端缓存

400 请求头不完整

401 权限验证错误

403 没有权限访问

404 文件不存在

500 服务器代码异常

503 网关错误

504 超时

### 5. Http1.0与Http1.1与Http2.0的区别

### 6. Http中get请求与post请求的区别

### 7. Http中cookie与session的区别

### 8. Http与Https的区别 Https加密算法相关面试问题，签名证书，公钥私钥、数字摘要的理解

## 设计模式知识点

### 1. 单例模式

### 2. Builder模式

### 3. 装饰模式

### 4. 策略模式

### 5. 模板方法

### 6. 观察者模式

## 算法知识点

### 1. 常⻅的八大排序方式

### 2. 时间复杂度的计算

### 3. 链表相关算法，链表翻转，链表合并等

### 4. 二叉树相关算法前序、中序、后序遍历(递归，迭代)

### 5. 红黑树与BL树

### 6. 给阿里2万多名员工按年龄排序应该选择哪个算法

### 7. GC算法(各种算法的优缺点以及应用场景)

### 8. 蚁群算法与蒙特卡洛算法

### 9. 子串包含问题(KMP 算法)写代码实现

### 10. 一个无序，不重复数组，输出N个元素，使得N个元素的和相加为M，给出时间复杂度、空间复杂度。手写算法

### 11. 万亿级别的两个URL文件A和B，如何求出A和B的差集C(提示：Bit映射->hash分组->多文件读写效率->磁盘寻址以及应用层面对寻址的优化)

### 12. 两个不重复的数组集合中，求共同的元素

### 13. 两个不重复的数组集合中，这两个集合都是海量数据，内存中放不下，怎么求共同的元素

### 14. 一个文件中有100万个整数，由空格分开，在程序中判断用户输入的整数是否在此文件中。说出最优的方法

### 15. 一张Bitmap所占内存以及内存占用的计算

### 16. 2000万个整数，找出第五十大的数字

### 17. 求1000以内的水仙花数以及40亿以内的水仙花数

### 18. 烧一根不均匀的绳，从头烧到尾总共需要1个小时。现在有若干条材质相同的绳子，问如何用烧绳的方法来计时一个小时十五分钟呢

### 19. 5枚硬币，2正3反如何划分为两堆然后通过翻转让两堆中正面向上的硬8币和反面向上的硬币个数相同

### 20.时针走一圈，时针分针重合几次

---

## 面试真题

### 1. 如何减少对第三方框架的耦合

- 使用工具类的方式：可以直接修改工具类里面的具体实现
- 使用静态工厂模式

### 2. 手写单例，DCL为什么要加Volatile关键字

```java
public class Singleton {  
    private volatile static Singleton singleton;  
    private Singleton (){}  
    public static Singleton getSingleton() {  
    if (singleton == null) {  
        synchronized (Singleton.class) {  
        if (singleton == null) {  
            singleton = new Singleton();  
        }  
        }  
    }  
    return singleton;  
    }  
}
```

singleton = new Singleton()，在线程内部有可能指令从排序，当一个线程正在执行这句话时，其他线程执行第一个if判断，如何指令重排序那么可能singleton已经指向分配的内存空间但未初始化完成，此时其他线程会判断singleton==null未false，直接获取singleton对象进行使用，产生异常。

如果加了volatile，禁止指令重排序就不会出现异常。

### 3. 直接在Activity Sleep 5000ms,再post一个runable会不会ANR

不会

### 4. 如何监听ANR

- FileObserver监听/data/anr/trace（FileObserver捕获ANR异常,缺点是Android5.0低权限应用不能监听变化“、data/anr/traces.txt”，只能在root之后才可以。）
- 查看/data/anr/trace

### 5. 组件化如何实现组件间通信

- 本地广播
- Intent Bundle 显性隐形
- 组件总线（处于基础层的模块）：有[得到DDComponentForAndroid](https://github.com/luojilab/DDComponentForAndroid)、[阿里Arouter](https://github.com/alibaba/Arouter)、[聚美Router](https://github.com/JumeiRdGroup/Router) 等等

### 6. 安装包优化

### 7. 如果有A,B,C,D,E五个步骤,每个步骤都需要操作对应请求,用哪种设计模式

### 8. 如果让你设计一个app,打算怎么设计

### 9. Serial使用的哪一种回收算法

采用复制算法

> 新生代收集器：Serial、ParNew、Parallel Scavenge；
>
> ​      老年代收集器：Serial Old、Parallel Old、CMS；
>
> ​      整堆收集器：G1；

### 10. Android主线程是怎么启动的

### 11. dex是如何转为机器码的

### 12. llvm编译是如何优化代码的

### 13. 静态类的静态方法能不能被子类重写，为什么

不能，走的invoke-static指令,只有走invoke-virtual指令的才可能实现多态

### 14. Linux的启动流程

### 15. looper的唤醒是在Java还是Native层,怎么做到的

### 16. 跨平台开发熟不熟悉

### 17. 如何提高海外用户的访问速度,假设服务器在深圳

### 18. 红包随机算法 是怎么做到的

额度为0.01到剩余平均值*2之间

### 19. 手写一个二叉树的深度度优先遍历,递归 非递归

### 20. Android中LocalServerSocket是干什么用的

### 21. binder的Native层代码

### 22. Linux有哪些RPC机制

### 23. 为什么android使用了Binder机制没采用共享内存

### 24. 如果让你设计一套进程间通信的机制,你会怎么设计

### 25. Linux的模块动态加载机制是怎么实现的

### 26. 一个物理屏划分为三个逻辑屏,是靠谁来分发事件的

### 27. ConcurrentHashMap是不是绝对的线程安全

### 28. 线程池是如何管理线程状态的

### 29. Kotlin的访问权限

### 30. Koltin为什么比Java更安全

### 31. Koltin比Java好在哪

### 32. 为什么操作数栈是Thread-Private

### 33. 计算二叉树的深度

### 34. 动态代理静态代理区别

### 35. 启动优化怎么做的

### 36. http有哪几种版本,版本间有什么区别。https跟http有什么区别

### 37. apk为什么要签名,v1跟v2签名的区别

### 38. dex到odex为什么不能在编译期优化

### 39. 热修复原理

### 40. 安装包优化有哪几种方式

### 41. 如何应对弱网环境

- 接口设计优化
- 图片优化
- 让用户感觉到快
- 先加载文字再加载图片
- 常用信息加入缓存机制、增量更新

### 42. android数据存储方式

### 43. 如果一个app无法访问网络,你怎么做数据存储

### 44. DVM跟JVM的区别

#### Java虚拟机

1、`java`虚拟机基于栈。
基于栈的机器必须使用指令来载入和操作栈上数据，所需指令更多更多。
2、`java`虚拟机运行的是`java`字节码。
`java`类会被编译成一个或多个字节码`.class`文件.

#### Dalvik虚拟机

1. `dalvik`虚拟机是基于寄存器的

2. `Dalvik`运行的是自定义的`.dex`字节码格式。

   `java`类被编译成`.class`文件后，会通过一个`dx`工具将所有的`.class`文件转换成一个`.dex`文件，然后`dalvik`虚拟机会从其中读取指令和数据.

3. 常量池已被修改为只使用`32`位的索引，以 简化解释器。

4. 一个应用，一个虚拟机实例，一个进程
   所有`android`应用的线程都是对应一个`linux`线程，都运行在自己的沙盒中，不同的应用在不同的进程中运行。每个`android dalvik`应用程序都被赋予了一个独立的`linux PID(app_*)

### 45. React Native跟原生开发的优劣

### 46. Android 沉浸式状态栏 怎么实现的

### 47. 事件处理函数有哪几个,父View 子View 监听同一个事件,重写哪些方法。在哪个View重写

### 48. ViewRootImpl接受事件吗

### 49. 利用logging监听方法耗时，会不会让app增大延迟

### 50. eventbus为什么要用CopyOnWriteList

### 51. 插件化怎么加载资源的

### 52. JVM怎么保证gc效率跟线程运行效率的

### 53. 如果android没用对应的view,flutter能运行吗

### 54. 接口暴露,但是不让别人调用,有哪些办法

### 55. 为什么采用flatbuffer? 比Json好在哪里

### 56. 如何处理Crash,NativeCrash呢?Google是怎么做到的?如果上报过程中再次产生Crash能不能捕捉到

### 57. uncaughtException是被谁调用的,如果再次崩溃能不能捕获到

### 58. Linux是怎么知道app崩溃的,如果想要在被kill前 做一些耗时操作,该怎么做

### 59. 考虑设计一个crash捕捉模块

### 60. 100万个数字求100个最大值

海量数据TopK的问题，使用堆解决，堆的插入、查找时间复杂度为O(logN)，具体实现，用优先队列

### 61. 手写快速排序算法

### 62. 如何防止DNS劫持

### 63. 如果让你实现一个调试器,你会怎么设计?静态调试?动态调试呢

### 64. 一个应用程序安装到手机上的过程发生了什么

### 65. RecyclerView的缓存机制

### 66. 生产者和消费者模型如何理解

要求：保证生产者不会在缓冲区满时加入数据，消费者也不会在缓冲区空时消耗数据

- 生产者持续生产，直到缓冲区满，**满时阻塞**；缓冲区不满后，继续生产；
- 消费者持续消费，直到缓冲区空，**空时阻塞**；缓冲区不空后，继续消费；

实现：

- `wait()`/`notify()`方式；
- `await()`/`signal()`方式；
- `BlockingQueue`阻塞队列方式；
- `PipedInputStream`/`PipedOutputStream`方式；

### 67.六大设计原则

- 依赖倒置
- 开放关闭
- 接口隔离
- 单一职责
- 迪米特
- 里式替换

### 68. LeakCanary监控原理解析

### 69. Android 项目中 asset 目录和 res 目录有什么区别

- 引用方式不同
- 是否压缩
- 是否可以访问多层文件夹下的文件

### 70. SparseArray原理

安卓提供了一个名为SparseArray的数据结构，用来替代小型的以int为key的HashMap，SparseArray牺牲了一些运行性能，用以换取内存节省。

### 71.  invalidate()、requestLayout() 区别

### 72. ArrayList 怎么实现线程安全

- Collections.synchronizedList()
- 使用Vector
- 使用CopyOnWriteArrayList

### 73. RelativeLayout与LinerLayout的区别

### 74. 一个无限单向链表如何计算长度，如果有环如何计算长度

### 75. Tinker 为什么需要重启

### 76. TCP怎么做长连接

### 77. 如果子View已经处理了事件，父View怎么拦截子View事件

### 78. 线程状态转换图

### 79. onNewIntent() 调用时机

### 80. setContentView()后面的流程

### 81. WindowManager.addView()，View.getParent()是谁

### 82. 有多个线程1、2、3、4，1、2、3 并行完后与 4 串行，至少 3 种方式实现

### 83. TCP三次握手、四次挥手

### 84. Android系统启动流程

### 85. epoll 机制的原理
