# JVM

##  java内存模型

### 简述java内存模型
    

### as-if-serial规则
    as-if-serial语义指的是：不管编译器和处理器怎么重排序，单线程的程序执行结果不能被改变（即编译器和处理器不会对存在数据依赖关系的操作做重排序）

### happen-before规则（8大原则）
    1.程序顺序原则：单线程内写在前面的操作 happen-before 于写在后面的操作
    2.锁定规则：对一个锁的解锁 happen-before 于随后对这个锁的加锁
    3.volatile变量规则：对volatile变量的写操作 happen-before 于后续对这个valatile变量的读操作
    4.线程启动（start）规则：线程的start启动方法 happen-before 于该线程的其他任意操作
    5.线程中断（interrupted）规则：对线程interrupted（）方法的调用 happen-before 于该线程的代码检测到中断事件的发生
    6.线程终止（join）规则：线程中的所有操作 happen-before 于对线程的终止检测
    7.对象finalize规则：对象的初始化 happen-before 于finalize方法
    8.传递性规则：A-B,B-C，可以推出A-C

### as-if-serial和happen-before区别
    as-if-serial:保证单线程程序的执行结果不变
    happen-befor:保证正确同步的多线程程序的执行结果不变

### 简述原子性操作
    一个操作或多个操作，要么全部执行并且执行过程不会被任何因素打断，要么就都不执行，这就是原子性操作

### 简述线程的可见性
    可见性指当一个线程修改了共享变量时，其他线程能够立即得知修改。volatile、synchronized、final都能保证可见性

### 简述有序性
    即虽然多线程存在并发和指令优化等操作，在本线程内观察该线程的所有执行操作是有序的
    
### 简述volatile关键字的作用
    1.保证变量对所有线程的可见性
    当一条线程修改了变量值，新值对于其他线程来说是立即可以得知的
    2.禁止指令重排序优化
    对volatile变量进行写操作，生成的汇编指令会带有lock前缀，相当于一个内存屏障，编译器不会将后面的指令重排到内存屏障之前
    
### java创建线程的方式
    1.继承thread父类
    2.实现runnable接口
    3.实现Callable接口
    
### 简述java线程的状态
    线程有6种状态：new、runnable、block、waiting、timed_waiting、therminated
    new：线程被创建未启动，此时还未调用start方法
    runnable：运行状态，表实线程正在执行
    blocked：阻塞状态，正在等待获取锁
    waiting：等待状态，线程运行Object.wait()/Thread.join()会进入该状态
    timed_waiting：限期等待，由thread.sleep(long)/Object.wait(long)指定等待时间
    terminated：结束状态，线程调用完run方法进入该状态
    
### 简述线程通讯的方式
    1.volatile关键字修饰变量，保证所有线程对变量访问的可见性
    2.synchronized关键字，确保多线程同一时刻只能有一个执行
    3.wait/notify方法
    4.IO通讯
    
### 简述线程池
    