# 第一阶段

## 安装go语言环境

因为上服务计算课的原因，这里直接贴上之前的博客地址，就不重复了

[安装环境博客](https://gitee.com/caoxy7/homework/blob/master/GoReport/firstWork/first.md)

## 前后端分离开发的理解

所谓前后端分离是一种架构模式而不是一种技术，它旨在将前后端分离，前端人员不用关心业务处理是怎么回事，后端人员不用在意界面是什么样的，从而减少了前后端人员的交流，使得开发者不用面面精通，以此压榨整个公司的的运行效率。看上去和流水线有异曲同工的意思。

## 微服务架构的理解

先随便写一笔：即将原先冗余的一个大架构下的服务分开为小的细碎的各个服务。

## 基础知识复习

- RPC（remote procedure call）远程调用过程:调用函数解决问题时，需要调用的函数在服务端而不是本地，需要通过网络请求，协议来实现该过程。

大致流程如下：
```
// Client端 
//    Student student = Call(ServerAddr, addAge, student)
1. 将这个调用映射为Call ID。
2. 将Call ID，student（params）序列化，以二进制形式打包
3. 把2中得到的数据包发送给ServerAddr，这需要使用网络传输层
4. 等待服务器返回结果
5. 如果服务器调用成功，那么就将结果反序列化，并赋给student，年龄更新

// Server端
1. 在本地维护一个Call ID到函数指针的映射call_id_map，可以用Map<String, Method> callIdMap
2. 等待服务端请求
3. 得到一个请求后，将其数据包反序列化，得到Call ID
4. 通过在callIdMap中查找，得到相应的函数指针
5. 将student（params）反序列化后，在本地调用addAge()函数，得到结果
6. 将student结果序列化后通过网络返回给Client
```

[REST](https://www.zhihu.com/question/28557115)
