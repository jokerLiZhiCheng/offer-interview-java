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
    
spring事务传播机制和隔离级别 [https://blog.csdn.net/qq_17085835/article/details/84837253]()