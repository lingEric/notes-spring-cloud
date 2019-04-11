1-1 spring cloud 简介

spring cloud是一个基于spring boot实现的微服务架构开发工具。它为微服务架构中涉及的配置管理、服务治理、断路器、智能路由、微代理、控制总线、全局锁、决策竞选、分布式会话和集群状态管理等操作提供了一种简单的开发方式。

spring cloud包含了多个子项目：

* spring cloud config: 配置管理工具，支持使用git存储配置内容，可以使用它实现应用配置的外部化存储，并支持客户端配置信息刷新，加密/解密配置内容等。
* spring cloud netflix：核心组件，对多个Netflix oss开源套件进行整合。
  * eureka：服务治理组件，包含服务注册中心，服务注册与发现机制的实现。
  * hystrix：容错管理组件，实现断路器模式，帮助服务依赖中出现的延迟和为故障提供强大的容错能力。
  * ribbon：客户端负载均衡的服务调用组件。
  * feign：基于ribbon和hystrix的声明式服务调用组件。
  * zuul：网关组件，提供智能路由，访问过滤等功能。
  * archaius：外部化配置组件
* spring cloud bus：事件、消息总线，用于传播集群中的状态变化或事件，以触发后续的处理，最常用的用于动态刷新配置等。
* spring cloud cluster：针对zookeeper、redis、hazelcast、consul的选举算法和通用状态模式的实现。
* spring cloud cloudfoundry: 与pivotal cloudfoundry的整合支持。
* spring cloud consul:服务发现与配置管理工具。
* spring cloud stream:通过redis、rabbit或者kafka实现的消费微服务，可以通过简单的声明式模型来发送和接受消息。
* spring cloud aws:用于简化整合amazon web service的组件。
* spring cloud security:安全工具包，提供在zuul代理中对oauth2客户端请求的中继器。
* spring cloud sleuth:spring cloud 应用的分布式跟踪实现，可以完美整合zipkin。
* spring cloud zookeeper: 基于zookeeper的服务发现与配置管理组件
* spring cloud starters: spring cloud 的基础组件，它是基于spring boot风格项目的基础依赖模块。
* spring cloud CLI:用于在groovy中快速创建spring cloud应用的spring boot CLI插件。

