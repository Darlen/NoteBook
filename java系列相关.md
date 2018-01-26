# java系列相关
## 基础相关
- 动态代理／cglib
- [浅谈Java中父类与子类的加载顺序详解](http://www.jb51.net/article/37881.htm)

```
父类子类静态方法／变量／静态块等加载顺序:
父类的静态成员变量—->父类静态代码块—->子类静态成员变量—->子类静态代码块
—->父类构造代码块—父类无参构造方法—子类构造代码块—子类构造方法
```
- hashmap/concurrenthashmap/threadpoolexecutor/java内存模型／事务传播类型／事务隔离级别
- [JSP与Servlet区别简述](http://blog.csdn.net/epm_kf6_10/article/details/48602117) :JSP在本质上就是Servlet,但是两者的创建方式不一样。Servlet都是由JAVA程序代码构成，用于流程控制和事务处理，通过Servlet来生成动态网页很不直观。而JSP由HTML代码和JSP标签构成，可以方便地编写动态网页.  
- [ThreadLocal实现方式](http://blog.csdn.net/zhangerqing/article/details/43095147) 
- 线程池的实现
- 7. hashmap（源码）／concurrentHashMap（源码）／reentrantlock（源码）／threadLocal（源码）／线程池（实现原理）／mybatis／spring
  - Hashmap:
  
```
a. key == null , putForNullKey
b. hash = hash(key)
c. bucket = indexFor(hash, length)
d. 遍历table 
e. addEntry
```
  -  ConcurrentHashMap: [源码解析](http://www.infoq.com/cn/articles/)
  
 ```
1. 获取size  : 
如果我们要统计整个ConcurrentHashMap里元素的大小，就必须统计所有Segment里元素的大小后求和。
Segment里的全局变量count是一个volatile变量，那么在多线程场景下，我们是不是直接把所有
Segment的count相加就可以得到整个ConcurrentHashMap大小了呢？不是的，虽然相加时可以获取每个Segment的count的最新值，但是拿到之后可能累加前使用的count发生了变化，那么统计结果就不准了。
所以最安全的做法，是在统计size的时候把所有Segment的put，remove和clean方法全部锁住，但是这种做法显然非常低效。 因为在累加count操作过程中，之前累加过的count发生变化的几率非常小，
***
所以ConcurrentHashMap的做法是先尝试2次通过不锁住Segment的方式来统计各个Segment大小，如果统计的过程中，容器的count发生了变化，则再采用加锁的方式来统计所有Segment的大小。
***
那么ConcurrentHashMap是如何判断在统计的时候容器是否发生了变化呢？使用modCount变量，在put , remove和clean方法里操作元素前都会将变量modCount进行加1，那么在统计size前后比较modCount是否发生变化，从而得知容器的大小是否发生变化。
2. Put: 
由于put方法里需要对共享变量进行写入操作，所以为了线程安全，在操作共享变量时必须得加锁。Put方法首先定位到Segment，然后在Segment里进行插入操作。插入操作需要经历两个步骤，第一步判断是否需要对Segment里的HashEntry数组进行扩容，第二步定位添加元素的位置然后放在HashEntry数组里。
是否需要扩容。在插入元素前会先判断Segment里的HashEntry数组是否超过容量（threshold），如果超过阀值，数组进行扩容。值得一提的是，Segment的扩容判断比HashMap更恰当，因为HashMap是在插入元素后判断元素是否已经到达容量的，如果到达了就进行扩容，但是很有可能扩容之后没有新元素插入，这时HashMap就进行了一次无效的扩容。
如何扩容。扩容的时候首先会创建一个两倍于原容量的数组，然后将原数组里的元素进行再hash后插入到新
的数组里。为了高效ConcurrentHashMap不会对整个容器进行扩容，而只对某个segment进行扩容。
```  
- 类加载机制
- Jointpoint/pointcut/advice/aspect/….around
- 八大基本类型的长度
- 链表／数组
- JDK8的新特性
- Executors／ExecutorService
- 继承／封装／多态



## 集合相关
- 集合框架：collection/list／queue／map／。。。
[常见的Java集合框架面试题目及回答](http://blog.csdn.net/cocacola456/article/details/66971148)




## IO／网路相关
- 1. [Java 网络IO编程总结（BIO、NIO、AIO均含完整实例代码）](http://blog.csdn.net/anxpp/article/details/51512200)
- [Java Socket编程----通信是这样炼成的](http://www.cnblogs.com/rocomp/p/4790340.html)
- TCP／Socket编程
- [http和https的作用与区别](http://www.cnblogs.com/qiangxia/p/5261813.html) :证书／端口／协议／是否加密传输／状态  
- 7层网络结构




---

## 多线程／并发编程相关
- 1. [Java并发编程系列](http://www.cnblogs.com/paddix/p/5374810.html)
- 2. [死磕Java并发系列](https://www.jianshu.com/nb/12860760) 
- 3. [阻塞／非阻塞，异步与同步](http://www.linuxidc.com/Linux/2015-07/120338.htm) 

```
同步和异步关注的是消息通信机制 (synchronous communication/ asynchronous communication)
所谓同步，就是在发出一个*调用*时，在没有得到结果之前，该*调用*就不返回。但是一旦调用返回，就得到返回值了。
换句话说，就是由*调用者*主动等待这个*调用*的结果。

而异步则是相反，*调用*在发出之后，这个调用就直接返回了，所以没有返回结果。换句话说，当一个异步过程调用发出后，调用者不会立刻得到结果。而是在*调用*发出后，*被调用者*通过状态、通知来通知调用者，或通过回调函数处理这个调用。
``` 
- [线程间的通信](https://mp.weixin.qq.com/s/ALxAKVyjYjxxVd1OPRtq2w) 
- 多线程：原子性
- [多线程之间的通信](https://mp.weixin.qq.com/s/ALxAKVyjYjxxVd1OPRtq2w)
thread.join(), object.wait(), object.notify(), CountdownLatch, CyclicBarrier, FutureTask, Callable，yield    
wait/notify/notifyAll和sleep/yield/join
 
  - 如何让两个线程依次执行？
  - 那如何让 两个线程按照指定方式有序交叉运行呢？
  -  四个线程 A B C D，其中 D 要等到 A B C 全执行完毕后才执行，而且 A B C 是同步运行的
  - 三个运动员各自准备，等到三个人都准备好后，再一起跑
  - 子线程完成某件任务后，把得到的结果回传给主线程
  - [线程的状态转换图](https://www.cnblogs.com/bhlsheji/p/5099362.html)![线程的状态转换图](http://p21g8hcmx.bkt.clouddn.com/%E7%BA%BF%E7%A8%8B%E7%8A%B6%E6%80%81%E8%BD%AC%E6%8D%A2%E5%9B%BE.png) 
- [深入分析volatile的实现原理](https://www.jianshu.com/p/fb334c1f35ea)
- synchronize／reentranlock ／lock
  - [Synchronized（对象锁）和Static Synchronized（类锁）的区别
](http://blog.csdn.net/cs408/article/details/48930803)  
- Java存储模型
- CountdownLatch／semaphone／cycleBarrier
- lock与synchronized区别
[Java中的ReentrantLock和synchronized两种锁定机制的对比
](http://blog.csdn.net/fw0124/article/details/6672522)
- 可重入锁ReentrantLock／readwriteLock/Lock/Condition
-  具体实例  
  - [Sql语句中IN和exists的区别及应用](http://www.cnblogs.com/liyasong/p/sql_in_exists.html)
  - [高并发电商架构](http://blog.jobbole.com/85461/)
  - [ 电商那些年，我摸爬打滚出的高并发架构实战精髓](http://blog.csdn.net/u010327957/article/details/52788068)
  - [大话程序猿眼里的高并发](https://blog.thankbabe.com/tag/#高并发架构)

- 系列
 - [Java并发编程系列](http://www.cnblogs.com/paddix/p/5374810.html)
 - [死磕Java并发系列](https://www.jianshu.com/nb/12860760)    
  
  
  
---
## JDK等源码相关：
- 1. 线程池的相关实现 ThreadPoolExecutor／Executors／线程池的实现
- 2. 线程：ThreadLocal／blockingqueue／
- 3. 集合：hashmap／concurrentHashMap／
- 4. spring 源码研究
- 5. mybatis源码研究
- 6. Spring相关  
  - 6.1 spring的生命周期  
  - 6.2 [aware接口](http://blog.csdn.net/taiyangdao/article/details/51004137)  
  - 6.3 beanPostProcessor  
  - 6.4 [Spring 中JDKProxy和CGlibProxy的区别](http://blog.csdn.net/voyage_mh1987/article/details/5755729)  
  
```
 jdk：InvocationHandler, Proxy.newProxyInstance  , 必须是接口；      
 cglib：MethodInterceptor
```  

## JVM相关
- 1. [GC专家系列1：理解Java垃圾回收](https://segmentfault.com/a/1190000004233812)
- 2. [深入理解Major GC, Full GC, CMS](http://blog.csdn.net/iter_zc/article/details/41825395)
- 3. [JVM 新生代老年代](http://www.cnblogs.com/E-star/p/5556188.html)
- 4. [一份关于jvm内存调优及原理的学习笔记](http://www.cnblogs.com/RUN-TIME/archive/2016/04/29/5445115.html)
- 5. [JVM中线程的状态转换图](http://blog.csdn.net/zolalad/article/details/38903179)
- 6.  [JVM性能调优监控工具jps、jstack、jmap、jhat、jstat、hprof使用详解](https://my.oschina.net/feichexia/blog/196575)
- JVM原理

## Spring相关
- factorybean与beanfactory
-  Spring中应用的设计模式：resolvable/wrap/adpter/factory
- Javase 中自定义事件：事件类型／自定义事件监听器／自定义事件发布者
context:annotation-config 
context:component-scan 
<context:component-scan>的扫描行为可以进一步定制，默认情况下它只关心@Component、 @Repository、@Service和@Controller四位大员 


## 数据库相关
- [SQL经典面试题目总结](http://blog.csdn.net/a724888/article/details/68931086)
- [mysql多索引：最左原则](http://www.cnblogs.com/codeAB/p/6387148.html)  
- [MySQL 对于千万级的大表要怎么优化？](https://www.zhihu.com/question/19719997)
- 如何理解互联网？ 技术上，文化上-开发，分享、交互、自由、连接
- db2 实例
- 



## 微服务／大数据
- 1. [最全大数据面试题](https://zhuanlan.zhihu.com/p/24383239)
- [restful api 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
- 幂等性
- dubbo雪崩：超时和重试机制
- 微服务理解：技术（单体架构有模块化解耦、可独立部署、技术多样性等诸多优点）与业务方向  
- SOA/分布式概念
- [SOA与微服务](https://www.zhihu.com/question/37808426/answer/93335393)

## 设计模式
- [瀑布模型与敏捷模型](http://zhaisj.blog.51cto.com/219066/46187/)
- 工厂／抽象工厂／单例模式／适配器模式／装饰模式／观察模式／外观模式／策略模式。。。


```
瀑布：强调文档／没有迭代与反馈／不适应客户需求不断变化                     
敏捷：迭代／客户参与／小版本
```  
-  [SOA 与微服务架构区别](https://www.zhihu.com/question/37808426/answer/93335393)  

## MQ消息队列相关
- 1. [RocketMQ与Kafka对比（18项差异）](http://blog.csdn.net/damacheng/article/details/42846549)
- 2. [Kafka High Availability](http://www.infoq.com/cn/articles/kafka-analysis-part-2/)
- 3. [Kafka offset存储方式与获取消费实现](http://www.aboutyun.com/thread-21104-1-1.html)
- 4. kafka分区与消费者关系
- 5. [消息队列设计的精髓](https://mp.weixin.qq.com/s?__biz=MjM5MDE0Mjc4MA==&mid=2650993240&idx=1&sn=bb2c943ee7aeabc3b5962056534d36b5)
- kafka与其他mq的区别
- kafka是如何保障可用性的	

## 其他
- zk的watcher机制／zk的master选举／zk的分布式锁／zk的节点类型 
- 查看cpu／内存使用情况，如果cpu过高，内存过高，如何处理
- 高并发电商架构
- 老年代满了会出现什么情况／新生代满了会出现什么情况
- Kafka的repla机制
- Zk的master选举
- Redis选举复制
- redis的用处
- 事务的隔离级别／数据库的隔离级别

```
事务隔离级别：readUncommit／readCommit／repeatable read／serialable
脏读、不可重复读、幻读：http://blog.csdn.net/gaoshan_820822/article/details/4582561
不可重复读和幻读的区别：很多人容易搞混不可重复读和幻读，确实这两者有些相似。但不可重复读重点在于update和delete，而幻读的重点在于insert。
http://www.cnblogs.com/itcomputer/articles/5133254.html
```
- 

### 


************************