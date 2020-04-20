## Tomcat套娃式架构设计精讲及源码剖析准备笔记

### 一 tomcat有个宏观的认识
#### tomcat主要功能
* HTTP服务器(socket通讯、http协议解析)
* Servlet容器  

#### 架构图

#### 组件
 * Server 代表一个tomcat实例, 可以有多个service.
 * service 有一个或多个Connector(监听不同端口)， 一个Servlet容器
 * Engine 引擎是Servlet容器Catalina的核心
 * host  虚拟主机
 * context 上下文(部署的应用)
 * Wraper 

### 二 学习源码的体会
* 聚焦: 主要学习主线，后细节
* 学习tomcat架构思维、设计技巧。
* 一定要画图、做笔记， 分享。
