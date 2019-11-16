[TOC]



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

`onCreate()` -> `onStart()` -> `onResume()`	---	`onPause()` -> `onStop()` -> `onDestory()`

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

### 2. Service两种启动方式 startService、 bindService 区别及生命周期

### 3. Service绑定服务的三种实现方式，扩展Binder类、使用Messenger、使用AIDL

### 4. 关于启动服务与绑定服务间的转换问题 先绑定服务后启动服务、先启动服务后绑定服务

### 5. 服务Service与线程Thread的区别

### 6. Android 5.0以上的隐式启动问题及其解决方案

### 7. 如何保证服务不被杀死

### 8. IntentService的使用及原理

## BroadcastReceiver相关

### 1. BroadcastReceiver定义及作用、应用场景

### 2. BroadcastReceiver的注册方式，静态方式、动态方式

### 3. BroadcastReceiver注册与取消的时机

### 4. BroadcastReceiver的不同类型，普通广播，系统广播、有序广播、粘性广播、应用类广播

## Fragment相关

### 1. Fragment生命周期

### 2. Fragment的懒加载

### 3. Fragment之间的通信

### 4. FragmentPagerAdapter与FragmentStatePagerAdapter的区别

### 5. 为什么不建议直接通过使用new Fragment的方式传入数据

## 序列化相关

### 1. 序列化与反序列化的定义及区别

### 2. Serializable中serialVersionUID及transient关键字的作用

### 3. 序列化:Parcelable和Serializable差异 

## IPC相关 

### 1. 在Android中什么样的情况下会使用多进程模式，如何开启多进程 

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

### 1. 获取 SharedPreferences 对象过程中，系统做了什么?

### 2. getXxx 方法做了什么?

### 3. putXxx方法做了什么?

### 4. commit/apply方法如何实现同步/异步写磁盘?

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

### 4. SharedPreferences使用及源码，commit与apply()方法的区别

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

### 12. 两个不重复的数组集合中，求共同的元素。

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

### 47. 事件处理函数有哪几个,父View 子View 监听同一个事件,重写哪些方法。在哪个View重写?

### 48. ViewRootImpl接受事件吗?

### 49. 利用logging监听方法耗时，会不会让app增大延迟

### 50. eventbus为什么要用CopyOnWriteList

### 51. 插件化怎么加载资源的

### 52. JVM怎么保证gc效率跟线程运行效率的

### 53. 如果android没用对应的view,flutter能运行吗

### 54. 接口暴露,但是不让别人调用,有哪些办法

### 55. 为什么采用flatbuffer? 比Json好在哪里?

### 56. 如何处理Crash,NativeCrash呢?Google是怎么做到的?如果上报过程中再次产生Crash能不能捕捉到?

### 57. uncaughtException是被谁调用的,如果再次崩溃能不能捕获到?

### 58. Linux是怎么知道app崩溃的,如果想要在被kill前 做一些耗时操作,该怎么做?

### 59. 考虑设计一个crash捕捉模块

### 60. 100万个数字求100个最大值

海量数据TopK的问题，使用堆解决，堆的插入、查找时间复杂度为O(logN)，具体实现，用优先队列

### 61. 手写快速排序算法

### 62. 如何防止DNS劫持

### 63. 如果让你实现一个调试器,你会怎么设计?静态调试?动态调试呢?

### 64. 一个应用程序安装到手机上的过程发生了什么？

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
