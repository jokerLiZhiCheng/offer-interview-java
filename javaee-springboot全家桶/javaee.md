# spring

## 一、spring容器

### spring中的bean是线程安全的吗？
    spring容器本身并没有提供线程安全的策略，是否线程安全要分单例、原型两种情况讨论
    原型bean：每次调用创建新对象，不存在线程安全问题
    单例bean：线程共享，因此存在线程安全问题。若bean为无状态对象也不存在线程安全问题
    （如controller、service），否则需要通过ThreadLocal解决线程安全问题

### spring怎样开启事务，事务里有哪些属性
    开启方式：1.编程式事务管理
            2.基于TransactionProxyFactoryBean的声明式事务
            3.基于@Transactional的声明式事务管理
            4.基于Aspectj AOP配置事务
    事务属性：传播行为（propagarion）、隔离级别（isolation）、超时时间（timeout）、
            是否只读（readonly）、回滚规则（rollbackfir）、不回滚规则（noRollbackFor）

### spring事务的隔离机制
    同mysql：读未提交、读已提交、可重复读、串行化

### spring事务的传播行为
    propagation_required:当前存在事务，则加入该事务，不存在则创建    
    propagation_required_new:新建一个独立的事务，互不影响
    propagation_nested:和new类似
    propagation_supports:仅支持当前事务，若当前不存在事务，则以非事务方式执行
    propagation_not_supported:以非事务方式执行，当前存在事务就挂起
    propagation_mandatory:强制以事务方式执行，若不存在事务则抛出异常
    propagation_never：强制以非事务方式执行，若存在事务则抛出异常

spring事务传播机制和隔离级别 [https://blog.csdn.net/qq_17085835/article/details/84837253]()

### spring中bean作用域
    singleton:容器仅存在一个bean实例
    prototype：每次调用getBean都会创建新的实例
    request：每次http请求创建新的bean
    session：同一个http session共享一个bean
    globalSession：作用域Portlet应用环境
    
### 在一个service里，无事务的方法a()调用了有事务的方法b(),若调用方法a是否会开启事务？
    不会，因为在调用注解方法时，spring会扫描该bean的调用方法上是否存在@transactional注解，若存在则为该bean创建代理子类，
    注解也是在该代理类上启动，但若该方法的调用是被同类其他方法调用，则该方法的调用并没有通过代理类，而是直接使用bean对象，
    也就不会开启事务。


# 基础

## http

### 用户输入一个网址的请求过程
    1.用户输入域名
    2.DNS解析域名得到ip地址
    3.客户端与服务器建立连接（TCP三次握手）
    4.客户端发起http请求
    5.服务器接收请求，根据端口号、路径找到对应资源文件，返回源代码给客户端
    6.客户端拿到数据（html页面源代码），开始解析页面以及请求资源
    7.客户端渲染页面
    8.服务器断开连接（四次挥手）

一次完整的http请求过程[https://blog.csdn.net/u013777975/article/details/80496121?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-3.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-3.control]()
    
### http无状态
    指的是：http本身是一个无状态的连接协议，即同一个接口不同人调用返回的结果是相同的，但我们是有需要记录用户的状态信息需求的
    因此Cookie、Session诞生了。