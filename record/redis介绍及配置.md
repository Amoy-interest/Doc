* Redis
  * 开源Key-Value数据结构的内存存储系统，可用作数据库、缓存和消息代理。
  * 支持的数据结构
    * 字符串String
    * 哈希Hash
    * 列表List
    * 集合Set
    * 有序集合ZSet
  * 应用场景
    * 热点数据存储
    * 限时业务
    * 计数器
    * 排行榜
    * 分布式锁
    * 等等
* 本项目使用情况
  * 借助redis解决计数器问题
    * 利用redis作为缓存去存储博文、用户的各种计数信息，redis内数据不存在时，从mysql中导入数据，这样再对博文进行点赞等相关操作时，就可以直接在redis中修改存储数据。本项目通过制定定时任务每隔一段时间将redis内的数据落地。
* Springboot配置redis
  * https://www.cnblogs.com/caizhaokai/p/11037610.html