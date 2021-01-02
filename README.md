# offer-interview-java

## java se

## juc
### 1.使用线程池优点：
    减少创建和销毁线程的次数
    根据系统承受能力，调整线程池工作线程数目，防止程序卡死
### 2.常用线程池接口
    Executor：java线程池顶级接口，提供一系列线程执行方法
        |-- ExecutorService:线程池主要接口
            |--ThreadPoolExecutor:线程池实现类
            |--ScheduledExecutorService:负责线程调度
                |--ScheduledThreadPoolExecutor:和定时器类似，解决任务重复执行问题
### 3.工具类Executors

### 4.


## 计算机网络

## linux

## mysql
### 1.字符串拼接
使用方法：
concat(str1,str2,...)
注：参数中有一个为null，concat返回就为null
例子：
```sql
select concat(last_name, ' ', first_name) as Name from employees
```

### 2.常用聚合函数
sum():求和，count():计算总行数，max()\min():最大\最小值，avg():求平均值，round():保留几位小数

### 3.update语句
以下代码为从牛客网复制的最基本update语句用法：
```sql
update titles_test set to_date=NULL, from_date='2001-01-01' where to_date='9999-01-01'
```

java面试题整理
