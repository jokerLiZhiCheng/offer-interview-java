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