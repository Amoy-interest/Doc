## 数据库mycat+mysql-slave+mysql-master部署记录

- Mycat简介

  MyCat是一个开源的分布式数据库系统，是一个实现了MySQL协议的服务器，前端用户可以把它看作是一个数据库代理**（类似于Mysql Proxy）**，用MySQL客户端工具和命令行访问，而其后端可以用MySQL原生协议与多个MySQL服务器通信，也可以用JDBC协议与大多数主流数据库服务器通信，其核心功能是分表分库，即将一个大表水平分割为N个小表，存储在后端MySQL服务器里或者其他数据库里。

- 项目中Mycat的使用

  通过mycat逻辑库的方式连接mysql-slave和mysql-master实现读写分离，mycat核心的分表分库功能由于项目的数据量尚未达到一定的规模，所以尚未利用，可作为一个拓展点为以后数据量增大采用。

- 部署方式

  在之前mysql的基础上，进一步部署mycat+mysql-slave+mysql-master的结构，将数据库和后端项目放在同一`docker-compose.yml`中,互相之间借助于docker-compose的network进行通信。

- 部署中遇到的问题

  - mycat中的mysql-connector-java-5.1.35.jar与mysql8.0的兼容问题，需要将其替换为mysql-connector-java-8.0.20.jar，可以在Dockerfile中添加

    ```
    COPY ./mysql-connector-java-8.0.20.jar /usr/local/mycat/lib/
    RUN rm -rf /usr/local/mycat/lib/mysql-connector-java-5.1.35.jar && chmod 777 /usr/local/mycat/lib/mysql-connector-java-8.0.20.jar
    ```

  - 后端与mycat的通信问题

    后端在使用mycat这一container进行连接时，必须与mycat放在同一network下，即mycat指定了固定ip的情况下，后端也应该有相同的配置。

  - mysql-master和mysql-slave的主从关系

    mysql-master中应该为mysql-slave生成一个有访问权限的账号

  - 从库遇到1062错误时slave停止，并且重启时始终重复错误再次停止，需要在mysql-slave的配置文件中加入`slave_skip_errors = 1062`以跳过错误

