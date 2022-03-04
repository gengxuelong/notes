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
      > PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
      > "http://mybatis.org/dtd/mybatis-3-config.dtd">
      > <configuration>
      > 
      > <environments default="development">
      >  <environment id="development">    //development 开发
      >    <transactionManager type="JDBC"/>  //事物管理
      >    <dataSource type="POOLED">
      >      <property name="driver" value="com.mysql.jdbc.Driver"/>
      >      <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL = true &amp; useUnicode = true &amp; characterEncoding = UTF-8"/>
      >      <property name="username" value="root"/>
      >      <property name="password" value="root"/>
      >    </dataSource>
      >  </environment>
      > </environments>
      > 
      >     //每一个Mapper.xml都需要在Mybatis核心配置文件中注册
      >     <mappers>
      >         //resource中指的是target中的路径，target中会生成class文件，指定java类没有问题，但不会生成xml文件，无法指引成功。解方法见测试 错误点2
      >      	<mapper resource = "com/kuang/dao/UsrDaoMapper.xml"></mapper>
      >     </mappers>
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
    }
        
        //既然有了SqlSessionFactory ,顾名思义，我们就可以得到SqlSession 的实例了。Sqlsession完全包含了面向数据库执行了SQL命令所需的方法。
     public static SqlSession getSqlSession() {
            return SqlSessionFactory.openSession();
    }
}
```



### 2.3编写代码

-  实体类
- Dao接口
- 接口实现类    : 由原来的UserDaoImpl转换为xml的Mapper配置文件

创建一个包： pojo

在pojo包内创建一个类：User  //实体类

创建dao包，在dao包内创建接口： UserDao      //dao 等价于mapper

​                      在dao包内创建UserDao的实现类,这是jdbc中常用的途径，而Mybatis的作用就是避免几乎一切jdbc代码和实现自动配置。

```java
public interface UserDao{
    public List<User> getUserList();
}
```

​                      在dao包下创建一个UserMapper.xml文件。  //mapper 完全等于Dao

内容在文档中

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
  PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
//命名空间，绑定一个dao/mapper接口
<mapper namespace="com.kuang.dao.UserDao">
    //查询语句  ，id对应的是方法名字
  <select id="getUserList" resultType = "com.kuang.pojo.User" >//返回的应该是List<User> ,但所有的集合都写成其泛型的类型
    select * from mybatis.user
  </select>
</mapper>
```

对比于UserImpl:

```java
public class UserImpl implements UserDao{
    public List<User> getUserList(){
        //执行SQL语句
        String sql = "select * from mybatis.user";
    }
}
```

### 2.4测试

注意点： 错误点1: Type interface com.kuang.dao.UserDao is not known to the MapperRegistry   .Mapper注册表中没发现UserDao 这个Mapper 。需要在Mybatis-config.xml 文件中添加上注册。

​                错误点2：maven不会自动在target红色文件夹中生成xml文件，需要人为写代码规定其过滤条件

在总项目的pom.xml和分项目的pom.xml 中都写上:

   ```xml
   //在build中配置resources，来放置我们的资源到处失败的问题
   <build>
   	<resource>
       	<directory>src/main/resources</directory>
           <includes>
               <include>**/*.properties</include>
               <include>**/*.xml</include>
           </includes>
           <filtering>true</filtering>
       </resource>
       <resource>
       	<directory>src/main/java</directory>
           <includes>
           	<include>**/*.properties</include>
               <include>**/*.xml</include>
           </includes>
           <filtering>true</filtering>
       </resource>
   </build>
   ```



- Junit测试

写在text/java 文件夹里面。这是Maven项目的规范

并且让绿色的java文件夹和main/java这个蓝色的文件夹做到一一对应。

com.kuang.dao  UserDaoTest

```java
public class UserDaoTest{
    public void test(){
        //获取SqlSession 对象
        SqlSession sqlSession = MybatisUtils.getSqlSession();
        //执行SQL
        //方式一
        UserDao userDao = SqlSession.getMapper(UserDao.class);
        List<User> userList = userDao.getUserList();
        //方式二
        List<User> userList = sqlSession.selectList("com.kuang.dao.UserDao.getUserList");
        
        
        for(User user : userList){
            System.out.println(user);
        }
        //关闭SqlSession
        sqlSession.close();
    }
}
```

你可能遇到的问题：

1. 配置文件没有注册
2. Maven导出资源问题
3. 绑定接口有错误
4. 方法名不对
5. 放回类型不对

.. SqlSession 是线程不安全的，因此每个线程都应该有一个自己sqlSession .每次收到一个http请求，就应该打开一个SQLSession，返回一个响应，就关闭他。关闭响应特别重要

官方建议方式：

SqlSession sqlSession;

try{

代码

}catch(Excection e){

}finally{

SqlSession.close();

}



Maven项目pom.xml的规范词：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>Mybatis_6</artifactId>
    <version>1.0-SNAPSHOT</version>
    <name>Mybatis_6</name>
    <packaging>war</packaging>
    
    
    <dependencies>
    
        
        
    </dependencies>
    
    <build>
    
        
    </build>
    
    
    
</project>
```

## 3.增删改查的实现

所有的操作只和接口陪配置文件有关，

### 1.namespace  : 接口类全名（用.)

namespace中的包名要和mapper接口的包名完全一致

### 2.select 

选择，查询语句，和数据库中的SQL语言中的select一模一样

- id ： 就是对应的namespace中的方法名
- resultType就是Sql语句的返回值的类型，要么是基本类型，要么就是class 
- parameterType :  参数类型

在Mapper中：

```java
public interface UserMapper{
    //查询全部用户
    List<User> getUserList();
    //根据id查询用户
    User getUserById(int id);
}
```

在xml实现文件中：

```xml
<select id = "getUserById" resultType = "com.gxl.pojo.User" parameterType = "int">
		select * from mybatis.user where id=#{id}     // #{id} 指的是你接口方法参数叫做“id”，这样就可以动态表示你所输入的id值了
</select>
```

测试类：

仍然在UserDaoTest类中：

```java
public class UserDaoTest{
    @Test
    public void getUserByid(){
        SqlSession sqlSession = MybatisUtils.getSqlSession();
        UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
        User user = userMapper.getUserById();
        println(user);
        
        sqlSession.close();
    }
}
```

一个方法对应一个SQL语句

### insert一个用户：

```java
//insert 一个用户，Mapper中
public int addUser(User user);
```

```xml
//对象中的属性可以直接取出来
<insert id = "addUser" parametertype = "com.gxl.pojo.User"> //insert没用返回类型的属性
	insert into mybatis.user(id,name,pwd) values (#{id},#{name},#{pwd});
</insert>
```

测试：

```java
//增删改需要提交事务
@Test
public void addUser(){
    SqlSession sqSession = MybatisUtils.getSqlSession();
    UserMappper userMpper = sqlSession.getMapper(UserMapper.class);
    int number = userMapper.addUser(new User(12,"haha","2020"));
    if(number >0）{
        System.out.println("增加成功");
    }
    //提交事务
       sqlSession.commit();
       
    
    sqlSession.close();
}
```

### 修改用户

```java 
int updateUser(User user);
```

```xml
<update id = "updateUser" parameterType = "com.gxl.pojo.User">
	update mybatis.user set name = #{name},pwd = #{pwd} where id = #{id};  //;可有可无
</update>
```

测试：

```java
 SqlSession sqSession = MybatisUtils.getSqlSession();
    UserMappper userMpper = sqlSession.getMapper(UserMapper.class);
    int number = userMapper.update(new User(12,"heihei","2020"));
    if(number >0）{
        System.out.println("增加成功");
    }
    //提交事务
    sqlSession.commit();
    sqlSession.close();
```

### 删除一个用户

```java
int deleteUser(int id);
```

```xml
<delete id = "deleteUser" parameteType = "int">
	delete from mybatis.user where id = #{id};
</delete>
```

测试

```java
 SqlSession sqSession = MybatisUtils.getSqlSession();
    UserMappper userMpper = sqlSession.getMapper(UserMapper.class);
    int number = userMapper.deleteUser(1);
    if(number >0）{
        System.out.println("增加成功");
    }
    //提交事务   非常重要
     sqlSession.commit();
       
    
    sqlSession.close();
```

 总： insert delete update select ,增删改查   CRUD

编写接口 ，编写xml和SQL，编写测试

