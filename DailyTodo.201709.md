# 201709 DailyTodo
## 20170911
### 1. 面审加乐观锁
### 2. 有钱用撤销可配
### 3. 修复核心没有的数据
### 4. 修复auditPasstime数据
### 5. 增加竞对／车竞对新老核心分流标识区分
### 6. 小金库开发

## 20170906 
### 1. 无状态／有状态
### 记一次生产事故
发版本过于频繁，导致覆盖， 比如A打tag，准备晚上11点发版本， B在7点发了另外一个版本没通知A，结果A晚上11点发版本的时候覆盖B的版本。 第二天发现这个问题，准备重新发一个版本包含A和B，但是C刚刚把代码merge到了master，导致，刚刚发的版本包括了没有被测试的C的版本，线上直接报错....  
原因：  
总结：
### http://git.oschina.net/zhou666/spring-cloud-7simple/tree/master

## 20170904 
### 1. 确定电销页面，会有什么值传过来，如何区分3c与车交叉
### 2. 确认确认借钱的2个接口是和谁对接
### 3. 简单写相应的接口和返回参数

### 4. 总结一篇log4j的用法
[【系统日志】log4j配置学习总结](https://my.oschina.net/giegie/blog/840331)
### 5. 需要看的博客
[基于Redis实现分布式应用限流](https://my.oschina.net/giegie/blog/1525931)  
[彻底理解ThreadLocal](http://blog.csdn.net/lufeng20/article/details/24314381/)  
[spring+spring mvc +mybatis+druid 实现数据库主从分离](http://blog.csdn.net/zhouzhiwengang/article/details/51087920)  
[JAVA中静态块、静态变量加载顺序详解](http://blog.csdn.net/mrzhoug/article/details/51581994)
### 6. chan