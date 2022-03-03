# MyBatis 

## 1.什么是myBatis  

- JDK 1.8 
- Mysql  5.7
- maven  3.6.1
- IDEA

回顾：

-  JDBC   Mybatis 是对JDBC 的简化
- Mysql 
- java 基础
- Maven
- Junit

ssm 框架 ： 配置文件。最好的方式就是看官网文档，Mybatis有中文文档

### 1. 简介

#### 1.1 什么是Mybatis

- Mybatis是一款优秀的持久层框架
- MyBatis 是一款优秀的持久层框架，它支持自定义 SQL、存储过程以及高级映射。MyBatis        免除了几乎所有的 JDBC 代码以及设置参数和获取结果集的工作。MyBatis        可以通过简单的 XML 或注解来配置和映射原始类型、接口和 Java POJO（Plain Old        Java Objects，普通老式 Java 对象）为数据库中的记录。

- MyBatis本是apache的一个[开源项目](https://baike.baidu.com/item/开源项目/3406069)iBatis，2010年这个[项目](https://baike.baidu.com/item/项目/477803)由apache software foundation迁移到了[google code](https://baike.baidu.com/item/google code/2346604)，并且改名为MyBatis。2013年11月迁移到[Github](https://baike.baidu.com/item/Github/10145341)。

1. 在github 获取Mybatis jar包或者原码 ，原码可以在idea中直接运行，是纯java语言开发的

2. 在Maven仓库获取MyBatis jar包

   > <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis -->
   > <dependency>
   >     <groupId>org.mybatis</groupId>
   >     <artifactId>mybatis</artifactId>
   >     <version>3.5.9</version>
   > </dependency>

#### 1.2持久层

数据持久化，

- 持久化就是将程序的数据在持久状态和瞬时状态转化的过程

- 内存： 断电即失
- 数据库（jdbc），io 均是文件持久化
- 生活中： 冷藏，罐头
- 为什么需要持久化： 有一些对象，不能让他丢掉
- 内存太贵了

#### 1.3 持久层

Dao 层    Service层     Controller层

- 完成持久化工作的代码块
- 层界限十分明显

#### 1.4 为什么需要Mybatis ？ JDBC也能做

- 帮助程序员将数据存入到数据库中

-  方便
- 传统JDBC代码太复杂了，简化。框架。
- 不用Mybatis也可以，更容易上手。技术没有高低之分，使用技术的人才有高低之分
- 优点：
  - 简单易学：本身就很小且简单。没有任何第三方依赖，最简单安装只要两个jar文件+配置几个sql映射文件。易于学习，易于使用。通过文档和源代码，可以比较完全的掌握它的设计思路和实现。
  - 灵活：mybatis不会对应用程序或者数据库的现有设计强加任何影响。 sql写在xml里，便于统一管理和优化。通过sql语句可以满足操作数据库的所有需求。
  - 解除sql与程序代码的耦合：通过提供DAO层，将业务逻辑和数据访问逻辑分离，使系统的设计更清晰，更易维护，更易单元测试。sql和代码的分离，提高了可维护性。
  - 提供映射标签，支持对象与数据库的orm字段关系映射。
  - 提供对象关系映射标签，支持对象关系组建维护。
  - 提供xml标签，支持编写动态sql。 

最重要的第一点： 使用的人多！学习他就是为了用，没人用当然就不去学。

## 2.第一个Mybatis 程序

思路： 搭建环境-》 导入Mybatis -》 编写代码 -》 测试

### 2.1 创建父模块

SQL语句： 

> CREATE DATABASE 'mybaits';
>
> USE 'mybatis';
>
> CREATE TABLE 'user'(
>
> 'id' INT(20) NOT NULL PRIMARY KEY,
>
> 'name' VARCHAR(30) DEFAULT NULL,
>
> 'pwd' VARCHAR(30) DEFAULT NULL
>
> )ENGINE = INNODB DEFAULT CHARSET = utf8;
>
> INSERT INTO 'user' ('id','name','pwd') VALUES
>
> (1,'haha','1234),
>
> (2,'SS','12345'),
>
> (3,'aa','123456')

1. 新建项目，新建一个maven项目，一个普通的maven项目
2. 删除src目录，成为一个父工程
3. 导入maven依赖，两个必须的依赖： mysql驱动，Mybatis    ，还有junity。都在Maven仓库里面。用xml标签让程序自己加载

### 2.2创建另一个模块

new一个module，

这个模块自动是第一个建立模块的子模块。这是我们想要的结果

- 编写Mybatis的核心配置文件

  - 在子模块的resource目录下新建xml文件： Mybatis-config.xml ：

    - 里面将Mybatis官网下的配置代码粘贴到这里面即可。

    - > ```xml
      > <?xml version="1.0" encoding="UTF-8" ?>
      > <!DOCTYPE configuration
      >   PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
      >   "http://mybatis.org/dtd/mybatis-3-config.dtd">
      > <configuration>
      >     
      >   <environments default="development">
      >     <environment id="development">
      >       <transactionManager type="JDBC"/>
      >       <dataSource type="POOLED">
      >         <property name="driver" value="com.mysql.jdbc.Driver"/>
      >         <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL = true &amp; useUnicode = true &amp; characterEncoding = UTF-8"/>
      >         <property name="username" value="root"/>
      >         <property name="password" value="root"/>
      >       </dataSource>
      >     </environment>
      >   </environments>
      >  
      > </configuration>
      > ```

- 编写Mybatis的工具类

com.kuang.dao包

com.kuang.utils包

在utils 包下： 

```java
//sqlSessionFactory --> sqlSession
public class MybatisUtils {
    private static SqlSessionFactory sqlSessionFactory;
    static{
        try{
            //使用Mybatis的第一步，获取sqlSessionFactory 的对象
            String resource = 'mybatis-config.xml';
            InputStream inputStream = Resources.getResourceAsStream(resource);
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        }catch (IOexception e){
            e.printStackTrace();
        }
        
        //既然有了SqlSessionFactory ,顾名思义，我们就可以得到SqlSession 的实例了。Sqlsession完全包含了面向数据库执行了SQL命令所需的方法。
        public static SqlSession getSqlSession() {
            return SqlSessionFactory.openS
        }
    }
}
```



