2-1 spring boot配置文件

## profile使用

yml文件中支持在单个文件通过spring.profiles属性来定义多个不同的环境配置。

示例

```yml
server:
	port: 8881
	
---
spring:
	profiles: test

server:
	port: 8882

---
spring:
	profiles: prod
	
server:
	port: 8883
```



问题：

如果是多个文件如何区分profile呢？



## 自定义参数

1. 在application.yml文件中增加自定义配置

```yml
my:
	name: eric
	age: 21
```

2. 在Java类中使用

```java
@Component
public class Book{
    @Value("$(my.name)")
    private String name;
    
    @Value("$(my.age)")
    private String age;
    
}
```



问题：如何使用自定义配置类？自定义配置文件位置？自定义配置类内部类配置？

## 参数引用

直接在yml文件中相互引用参数

```yml
my:
	name: eric
	message: hello,${my.name}
```



## 随机数使用

```yml

my:
	# 随机字符串
	name: ${random.value}
	# 随机int
	age: ${random.int}
	# 随机long
	number: ${random.long}
	# 10以内随机数
	count1: ${random.int(10)}
	# 10-20范围内随机数
	count2: ${random.int[10,20]}
```

## 命令行参数

直接在命令行中指定应用的参数

```shell
java -jar xxx.jar --server.port=8909
```

注意：--开头的参数配置才生效



## 多环境配置

多环境配置文件格式：

application-{profile}.properties

比如

application-dev.properties	开发环境

application-test.properties	测试环境

application-prod.properties	生产环境

至于具体哪个配置文件会生效，需要在application.properties文件中通过spring.profiles.active属性来配置

```properties
# application.properties
spring.profiles.active=dev
```

以上配置使得开发环境的配置文件生效

## 加载顺序

1. 命令行参数
2. SPRING_APPLICATION_JSON中的属性。SPRING_APPLICATION_JSON是以json格式配置在系统环境变量中的内容。
3. java系统属性，即System.getProperties()获得的内容
4. 操作系统环境变量



