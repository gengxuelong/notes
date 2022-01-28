# 微服务，SpringBoot

## 1.SpringBoot概述

### 简介1

SpringBoot 用来快速构建Spring项目

### Springboot概述：

基于约定有与配置的思想。

2014年1。0.0发布，SpringBoot是Spring的顶级项目

Spring官方网站：spring.io

可以通过SpringBoot开发任何应用的后台

SpringBoot用于：可以构建一切。用来构建项目

springcloud ：项目之间，配置一切

springcloud Data flow  数据的连接



SpringBoot：使用最少的配置来启动spring

#### Spring的缺点

- 写配置文件的时候挺麻烦的
- 依赖繁琐，引入依赖是，选择兼容的版本特别麻烦

SpringBoot 功能—：

- 自动配置
- 起步依赖，简化依赖配置
- 辅助功能，如嵌入式服务器，

SpringBoot并不是对spring功能的增强，而是一种快速使用spring的方式

## 2.SpringBoot快速入门

需求： 搭建springboot工程，定义HelloController.hello（） 方法，返回Hello SpringBoot

如果用spring实现：

- 首先要搭建maven工程
- 引入一堆的左边，spring的坐标，springMVC的坐标
- 写个controller，搞个注解，写个方法
- 最后对springMVC进行配置
- 配置完了之后引入Tomcat插件，
- 就可以启动和访问了

SpringBoot实现步骤;-

- 创建maven项目

- 导入springboot的起步依赖

- 定义Controller

- 编写引导类

- 启动测试

  

创建模块，maven模块，
    GroupId：com.itheima
    ArtifactId :springboot-helloworld
     ..多看官方的文档

进入pom文件中:

秩序写两个东西：一个负责坐标，一个负责依赖

```xml
<parent>
 	<groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.1.8.RELEASE</version>
</parent>


<dependencies>
	<dependcy>
    	<groupId>
        	org.springframework.boot
        </groupId>
        <artifactId>
        	spring-boot-starter-web
        </artifactId>
    </dependcy>
</dependencies>
        	
```

在Java文件目录中就可以写代码了：

```Java
package com.itheima;
import org.springframework.web.bind.annotation.requestMapping;
import org.springframework.web.bind.annotation.RestController;
@RestController
public class HelloController{
    @RequestMapping("/hello")
    public String hello(){
        return "hello Spring boot!";
    }
}
```

再写一个引导类。结构单一固定

是SpringBoot项目的入口

```Java
package com.itheima;
import org.springframework.boot.SpringApplication;
@SpringBootApplication
public class HelloApplication{
    public static void main(Stirng[] args){
        SpringApplication.run(HelloApplicaiton.class[,args]);
    }
}
```

小结：

- SpringBoot在创建项目的时候，使用jar的打包方式 
- SpringBoot的引导类，是项目的入口，运行main方法就可以启动项目了
- 使用Spingboot和spring构建的项目，业务大妈编写方式完全一样

### SpringBoot 快速入门

需求： 使用idea快速构建SpringBoot工程，定义HelloController.hello（）方法，返回："hello springboot"

1. 打开idea
2. 创建模块--》选择Spring Initializr
3. ...
4. 选择web，勾选Spring Web
5. 

