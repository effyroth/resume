java

    jvm
      gc
        cms
        g1
            region
      tool
        jmap: 生成heapdump文件
        jstack: 线程dump
        visualvm: 可视化分析
    spring
      aop
        proxy
      boot
        autoconfig
    mybatis
      generator
      xml
        sql analyse
    jdk8
      stream
      lambda
    thread safe
      synchronize
      lock
        timeout
        reentry
            fair：先排队
            unfair：先抢
        readwrite
        乐观:先执行,后抢锁
        悲观:先抢锁,后执行
      atomic
        cas
    红黑树
        balance
    容器
        list
        map
    lombok
    maven
        profile
        plugin
    reflect
    annotation
    
web
    
    http
        url
        header
        body
    rest
    servlet
    session
    token
    飞冰
    
rpc
    
    thrift

mysql

    btree
    index
      区分度
    transaction
      事务级别
        未提交读（READ UNCOMMITTED）
        已提交读（READ COMMITTED）
        可重复读（REPEATABLE READ）
        串行化（SERIALIZABLE）
        数据库默认隔离级别：RR（Repeatable Read，可重复读）
    分库分表
    读写分离
      master slave
      主从延迟
    ha
      异地灾备
    mvcc
    binlog
        databus
        canal
        offset
  
cache

      redis
        分布式锁
            redlock
            setnx
      memcache

linux

     awk
     crontab
     epoll

bigdata

      hadoop
      hive
      hbase
        行存储
      cdh
      flume
      spark
        内存
        延迟计算
      hue
      oozie
      sqoop
  
log

    slf4j
  
search

      es
        logstash
        kinbana
      solr
  
tracer

    zipkin

mq

    kafka
        topic
            patition
                replica
                segment
                hash
        consumer group
            offset
        消息投递语义
            At most once：最多一次，消息可能会丢失，但不会重复
            At least once：最少一次，消息不会丢失，可能会重复
            Exactly once：只且一次，消息不丢失不重复，只且消费一次（0.11中实现，仅限于下游也是kafka）
        幂等性
    rabbitmq

网关

      nginx
      spring-cloud-gateway
        鉴权
        授权
        限流
        路由

架构

    扩展性
        分布式
            无状态
            soa
            zookeeper
                临时节点
                    ha
                顺序节点
                    lock
                curator
                消息通知
    高并发
        缓存
    高可用
        lvs
        降级
        重试
    一致性
        paxos
        事务
    限流
        令牌桶
    降级
        histrix
  
云计算
    
    docker
    kubernates
    
流程规范

      confluence
      jira
      gitlab
      sonar
      jenkins
      abtest
      
tool
    
    idea
    datagrip
    xshell
    
爬虫
    
    jsoup
  
算法
  
    快排
    堆排序
    kmp
  
