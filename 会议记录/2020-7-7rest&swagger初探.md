### summary

- 尝试使用swagger editor 编辑api文档 ，尝试将swagger文档部署到spring项目并运行。
- 和助教，组员一起讨论图片存储以及点赞，评论，转发高并发情况下技术难点。
- 待做：
  - 将api文档部署到docker aws上方便组员直接访问
  - 学会在idea上直接写api
  - 吴和莫讨论各个api如何设计
  - 尝试使用redis数据库和mysql数据库结合
  - 设计数据库，写后端程序

### rest

- 好处：把前端和后端的代码隔离
- JSON格式编写的REST风格的API
- - URI 使用/表示层级关系 
  - 使用-或_分割英文单词 
  - 使用?用来过滤资源
  - ,或;可以用来表示同级资源的关系
- REST是Representational State Transfer的缩写  表述性状态转移化 

### swagger

- 帮助开发人员设计，构建，记录和使用RESTful Web服务

- Swagger工具集支持自动文档，代码生成和测试用例生成

- [Swagger：Rest API的描述语言](https://zhuanlan.zhihu.com/p/21353795)

- 前端经常抱怨后端给的接口文档与实际情况不一致。后端又觉得编写及维护接口文档会耗费不少精力，经常来不及更新。

- 使用swagger editor

  https://blog.csdn.net/benben_2015/article/details/90046046

- 如何尝试进行编辑？

  https://blog.csdn.net/benben_2015/article/details/90046046

- host: localhost
  basePath: /api

  还有schema: https 

  加上去之后看上去非常丑  所以我删掉先

- 如何保存？别人如何查看api文档？

  网上找到的都是放到一个spring 后端项目里面  然后跑起来 能够在某个网址上查看

  能够保存为 json / yaml 文件 但是我想的是保存为离线文档？

  好像确实都只能配一个项目然后进行查看。好奇怪。。。

- Q：

  - responses 中想用不同字符串 比如"success" "fail" 来表示状态 swagger怎么写？
  
  - 接下来要干啥？

  - 尝试写几个不同的接口  然后统一吗

  - 打了电话给助教  对swagger 他得建议是
  
    一边写api 一边配置一下docker 把api文档提供服务给小组成员 让小组成员能够去进行访问。
  
    其实也可以后端直接生成api。如果前端暂时对数据没有要求得话。
  
    （其实我觉得现在前端是暂时没有要求得吧。
  
  
  
  
  
  

