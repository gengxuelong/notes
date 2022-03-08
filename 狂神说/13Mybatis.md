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
	insert into mybatis.user (id,name,pwd) values (#{id},#{name},#{pwd});
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

## 4.错误排查

1. namespace 用的是类全名
2. 标签不要匹配错
3. 在mapper注册哪里，mapper元素的resource属性的值是用/ 而不是用.    ，最终指向UserMapper.xml文件 

**读错要从后往前读**

4. 同为static 的变量和代码块和静态方法执行顺序无规律，sqlSessionFactory  为空。应将代码块和静态方法合并
5. 输出的xml文件中存在乱码
6. maven中xml文件么法导出，用build的xml代码解决

## 5.Map和模糊查询扩展

### 1.万能的Map

假设我们的实体类或者数据库库中的表，字段或者参数过多，我们应当用Map。

在Mapper中

#### addUser2

```java
int addUser2(Map<String,Object> map);//用map就不用关系数据库的表中都有哪些字段
```

```xml
//对象中的属性可以直接取出来，，传入的Map时，传递的是map的key
<insert id = "addUser2" parameterType = "map">
	insert into mybatis.user (id,pwd) values (#{userid},#{passWord});
</insert>
```

测试

```java
@Test
public void addUser2(){
    SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
	Map<String,Object> map = new HashMap();
    map.put("userid",4);
    map.put("password","20000");
    int number = userMapper.addUser2(map);
    if(number > 0){
        System.out.println("修改成功");
    }
    sqlSession.commit();
    sqlSession.close();
}
```

####  getUserById2()

```java
User getuserById2(Map<String,Object> map);
```

```xml
<select id = "getUserById2" parameterType = "map" resultType = "com.gxl.pojo.User">
	select mybatis.user where id = #{helloId},name = #{name};
</select>
```

测试

```java
@Test
public void getUserById2(){
    SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
   Map<String,Object> map = new HashMap();
    map.put("helloId",4);
    map.put("password","20000");
    int number = userMapper.selectUserById2(map);
    if(number > 0){
        System.out.println("修改成功");
    }
    sqlSession.commit();
    sqlSession.close();
}
```

总： Map传递参数，直接在SQL中取出key即可

只有一个对象传递参数，直接在SQL中取出属性即可

只有一个基本类型的参数的情况下，在SQL中直接取用。如果是多个参数，只能用map，或者注解

### 2.模糊查询怎么写：

```java
List<User> getUserLike(String value);
```

```xml
<select id = "getUserLike" resultType = "com.gxl.pojo.User">
	select * from mybatis.user where name like #{value}
</select>
```

```java
@Test
public void getUserLike(){
    SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper userMapper = sqlSession.getMapper(UserMapper.class);
  	List<User> userList = userMapper.getUserLike("%李%");
    for(User user : userList){
        System.out.println(user);
    }
    
    
    sqlSession.commit();
    sqlSession.close();
}
}
```

1. java代码执行的时候，传递通配符% %
   - 也可： select mybatis.user where name like "%"#{value}"%"
2. 在SQL拼接中使用通配符，如上。

## 6.配置之属性优化，配置解析

### 1.核心配置配置文件

- Mybatis-config.xml  //官方建议命名
  - properties 属性
  - settings 设置
  - typeAliases 类型别名
  - environments 环境配置
    - transactionManager 事务管理器
    - DataSource 数据源
  - mappers 映射器

了解：

​         typeHandles 类型处理器

​		objectFactory  对象工厂

​		plugins  插件

​		databaseProvide 数据库厂商标识

新建一个子项目： Mybatis02

将Mybatis01 中的 工具类 、实体类、和dao4包以及测试包转移到Mybatis02中（似乎把代码重新复制额一份）

### 2。环境变量（environments）

可以配置多种环境，但是每个SqlssionFactory实例只能选择一种环境。

```xml
<environments default="test">
    <environment id="development">
      <transactionManager type="JDBC"/>
      <dataSource type="POOLED">
        <property name="driver" value="${driver}"/>
        <property name="url" value="${url}"/>
        <property name="username" value="${username}"/>
        <property name="password" value="${password}"/>
      </dataSource>
    </environment>
    
    <environment id = "test">
        <transactionManager type="JDBC"/>
      <dataSource type="POOLED">
        <property name="driver" value="${driver}"/>
        <property name="url" value="${url}"/>
        <property name="username" value="${username}"/>
        <property name="password" value="${password}"/>
      </dataSource>
    </environment>
  </environments>
```

- environments 的default属性是决定该项目当前用的是哪种环境。学会使用多种运行环境的切换
- 事务管理器（transactionManager)： 只有两个值： JDBC  和 MANAGED  .只用JDBC，第二个几乎没用。如果使用spring+mybatis 就完全不需要配置这个
- 数据源（dataSource) : 连接数据库 ，dbcp ,c3p0,druid ,hikari   
  - 三种内建的数据类型 ： type = UNPOOLED   POOLED   JND    ，分别为： 无池连接、有池连接、正常连接
    - 池：起到 用完可以回收 的作用
      - 默认是有池类型 POOLED

### 3。属性（properties）

我们可以通过properties属性来实现引用配置文件

这些元素都是可以外部配置且可以动态替换的，既可以在典型的java属性文件中配置，亦可以通过properties元素的子元素类传递

**在xml中，元素之间是有固定顺序的**

db.properties  ：编写一个数据库配置文件

//只有在xml文件中&才需要转移：   \&amp;

```properties
driver = com.mysql.jdbc.Driver 
url = jdbc:mysql://localhost:3306/mybatis?useSSL = true & useUnicode = true & characterEncoding = UTF-8     
username = root
password = root
```

将该文件放在resource目录下，在Mybatis-config.xml中引用的时候就不需要写全路径了。

```xml
<!--引用外部properties文件-->
<properties resource = "db.properties">
	<property name = "username" value = "root"/>
    <property name = "pwd" value = "root"/>
</properties>//优先级：优先使用外部配置文件
//也可以自闭合，如果没有property属性要写的话
<properties resource = "db.properties"/>
```

总配置文件引入 .properties文件后，就可以全程用"${driver}"  这样的写法实现元素值得引用- 

- 可以直接引入外部配置文件
- 可以在其中增加一些属性配置
- 如果两个地方冲突，优先使用外部配置文件

## 7.配置之别名优化，类型别名typeAliases

为java类型设置短的名字，只和xml配置有关，存在的意义在于减少类完全限定名的冗余

```xml
<typeAlises>
	<typeALias type = "com.gxl.pojo.User" alias = "User"/>  //在Mybatis-config.xml中设定，在该模块任何xml位置都能用。
</typeAlises>
```

```xml
<select id = "getUserById" resultType = "User">
 	select * from mybatis.user where id = #{id}
</select>
```

也可以指定一个包名，mybatis 会在包名下搜索需要的java bean(Java类)，扫描实体类的包后，类的别名默认就是这个类名的首字母小写，也可以完全是类名（首字母大写） 。但是官方建议小写，让人一眼看出是扫描包名的别名。

```xml
<typeALiases>
	<package name = "com.gxl.pojo"/>
</typeALiases>
```

```xml
<select id = "getUserById" resultType = "user">
 	select * from mybatis.user where id = #{id}
</select>
```

如果实体类比较少，使用第一种方式。

如果实体类比较多，使用第二种方式。

第一种方式可以DIY（自定义）.第二种方式只能用类名或者类名首字母小写。

但是可以借助@Alias 注解给扫描包的类进行起别名。

## 8。设置 settings

这是Mybatis中极为重要的调整设置。他们会改变Mybatis的运行时的行为

目前只需记忆：

logImpl      : 日志的具体实现

| logImpl | SLF4J \| LOG4J(deprecated since 3.5.9) \| LOG4J2 \| JDK_LOGGING \| COMMONS_LOGGING \| STDOUT_LOGGING \| NO_LOGGING |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

## 8.配置之映射说明

不重要的配置：

- typeHanders  类处理器
- objectFactory  对象工厂
- plugins 插件
  - mybatis-generator-core
  - mybatis-plus
  - 通用mapper

### 映射器：mappers

方式： 

- 资源路径

  - ```xml
    <mappers>
    	<mapper resource = "org/mybaits/PostMapper.xml"/>
    </mappers>
    ```

  - 

- 使用映射器接口实现类的完全限定类名

  - ```xml
    <mappers>
    	<mapper class = "org.mybatis.builder.PostMapper"/> 此时的mapper.xml 和 mapper 接口需要在一个包里，并且接口和实现xml 需要用一样的名字。
    </mappers>
    ```

  - 接口和Mapper配置文件必须重名

  - 接口和Mapper配置文件必须在同一包下

- 将包内的映射器接口实现全部注册为映射器

  - ```xml
    <mappers>
    	<package name = "org.mybatis.builder"/>
    </mappers>
    ```

  - 使用包扫描要求和第二种方式一样，必须重名，必须在同一个包下

练习实践：

- 将数据库的配置文件外部引入
- 实体类别名
- 保证UserMapper接口和UserMapper.xml命名一致，并放在同一个包下。

## 9.声明周期和作用域

- 开始执行  Mybatis-config.xml 配置文件

- 是为了创建SqlSessionFactoryBuilder对象：一旦创建Factory，就不需要他了。局部变量

- 接着建造SqlSessionFactory 对象   ：说变了就可以想象成数据库连接池，一点出现，就必须持续存在，没有任何理由销毁他的对象最简单的就是使用单例模式或者静态单例模式

- 生产SqlSession对象
  - 每个线程都应该有一个SqlSession 实例，相当于一个连接数据库的请求。最佳作用域是放在一个方法里面，用完之后赶紧关闭，方式资源浪费。线程不安全，不能共享数据。

- 生成Sql Mapper 

- 结束

这里面的每一个Mapper，就代表一个业务。

## 10。解决属性名和字段名不一致的问题。ResultMap 结果集映射

新建一个项目，测试实体类字段不一致的情况。

mybatis03 项目

直接拷贝mybatis02

实体类的属性和数据库的字段不一样

```java
public class User{
	private int id;
    private String name;
    private String password;
    
    ...
}
```

```xml
select * from mybatis.user where id = #{id}
```

查出后发现password属性值为null

完整的语句应该是：

select  id,name,pwd from mybatis.user where id = #{id}

类型处理器：  如果实体类的属性和字段一致，则自动映射。如果不一致，则pwd无法和实体类中的password对应

解决防范：

- 起别名：

  - select id,name pwd as password from mybatis.user where id = #{id}

- 使用 resultMap来解决。结果集映射

  - ``` 
    id  name  pwd
    id  name  password
    ```

  - ```xml
    <mapper namespace = "com.gxl.dao.UserMapper">
    	<resultMap id = "UserMap" type = "User">
        	<result column = "id" property = "id"/>
            <result column = "name" property = "name"/>
            <result column = "pwd" property = "password"/>
        </resultMap>>   //column 为数据库字段    property 为实体类属性
      	<select id = "getUserById" resultMap = "UserMap">
        	select * from mybatis.user where id = #{id}
        </select>
    </mapper>
    ```

  - ResultMap 的设计思想：只是简单描述关系。

  - resultMap最优秀的地方就是： 当你对它相当了解的时候，不必要显示地用到它们。既：名字相同的对应是默认的，我们没必要写一遍。

  - resultMap代替resultType

## 11.日志工厂

新建一个项目：mybatis-04；没有-可能会有不好的结果

如果一个数据库操作出现异常，我们需要排错，日志就是最好的助手，

曾经：sout   debug

现在： 日志工厂

| logImpl | SLF4J \| LOG4J(deprecated since 3.5.9) \| LOG4J2 \| JDK_LOGGING \| COMMONS_LOGGING \| STDOUT_LOGGING \| NO_LOGGING |
| ------- | ------------------------------------------------------------ |
|         |                                                              |

- LOG4J
- STDOUT_LOGGING

具体使用哪一个日志实现，在设置中设定。

STDOUT_LOGGING 标准日志输出

在mybatis核心配置文件中配置 settings元素

```xml
<settings>
	<setting name = "logImpl" value = "STDOUT_LOGGING"/> //STDOUT_LOGGING 标准日志，什么周边都不需要配置
</settings>
```

## 12.log4j的实现

1. LOG4G  我们可以控制日志信息 输入到控制台或者文件，或者GUI组件

2. 我们也可以控制日志输出的格式

3. 可以定义每一条日志信息的级别

4. 更令人感兴趣的是我们可以通过一个配置文件来灵活的进行配置，而不需要修改应用的代码



1. 先导入LOG4G 的包，在maven资源包网站 搜索log4g  ，获得包的依赖。

   - ```xml
     <!-- https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-core -->
     <dependency>
         <groupId>org.apache.logging.log4j</groupId>
         <artifactId>log4j-core</artifactId>
         <version>2.17.1</version>
     </dependency>
     ```

2. 在resource目录下创建log4j.properties文件，在百度上随便找一个   log4j的配置文件

   - ```properties
     ### 配置根 ###
     log4j.rootLogger = debug,console,file
     
     ### 设置输出sql的级别，其中logger后面的内容全部为jar包中所包含的包名	 ###
     log4j.logger.org.apache=dubug
     log4j.logger.java.sql.Connection=dubug
     log4j.logger.java.sql.Statement=dubug
     log4j.logger.java.sql.PreparedStatement=dubug
     log4j.logger.java.sql.ResultSet=dubug
     ### 配置输出到控制台 ###
     log4j.appender.console = org.apache.log4j.ConsoleAppender
     log4j.appender.console.Target = System.out
     log4j.appender.console.layout = org.apache.log4j.PatternLayout
     log4j.appender.console.layout.ConversionPattern =  %d{ABSOLUTE} %5p %c{ 1 }:%L - %m%n
     
     ### 配置输出到文件 ###
     log4j.appender.fileAppender = org.apache.log4j.FileAppender
     log4j.appender.fileAppender.File = logs/log.log
     log4j.appender.fileAppender.Append = true
     log4j.appender.fileAppender.Threshold = DEBUG
     log4j.appender.fileAppender.layout = org.apache.log4j.PatternLayout
     log4j.appender.fileAppender.layout.ConversionPattern = %-d{yyyy-MM-dd HH:mm:ss}  [ %t:%r ] - [ %p ]  %m%n
     
     ### 配置输出到文件，并且每天都创建一个文件 ###
     log4j.appender.dailyRollingFile = org.apache.log4j.DailyRollingFileAppender
     log4j.appender.dailyRollingFile.File = logs/log.log
     log4j.appender.dailyRollingFile.Append = true
     log4j.appender.dailyRollingFile.Threshold = DEBUG
     log4j.appender.dailyRollingFile.layout = org.apache.log4j.PatternLayout
     log4j.appender.dailyRollingFile.layout.ConversionPattern = %-d{yyyy-MM-dd 
     ### 配置输出到邮件 ###
     log4j.appender.MAIL=org.apache.log4j.net.SMTPAppender
     log4j.appender.MAIL.Threshold=FATAL
     log4j.appender.MAIL.BufferSize=10
     log4j.appender.MAIL.From=chenyl@yeqiangwei.com
     log4j.appender.MAIL.SMTPHost=mail.hollycrm.com
     log4j.appender.MAIL.Subject=Log4J Message
     log4j.appender.MAIL.To=chenyl@yeqiangwei.com
     log4j.appender.MAIL.layout=org.apache.log4j.PatternLayout
     log4j.appender.MAIL.layout.ConversionPattern=[framework] %d - %c -%-4r [%t] %-5p %c %x - %m%n
     
     ### 配置输出到数据库 ###
     log4j.appender.DATABASE=org.apache.log4j.jdbc.JDBCAppender
     log4j.appender.DATABASE.URL=jdbc:mysql://localhost:3306/test
     log4j.appender.DATABASE.driver=com.mysql.jdbc.Driver
     log4j.appender.DATABASE.user=root
     log4j.appender.DATABASE.password=
     log4j.appender.DATABASE.sql=INSERT INTO LOG4J (Message) VALUES ('[framework] %d - %c -%-4r [%t] %-5p %c %x - %m%n')
     log4j.appender.DATABASE.layout=org.apache.log4j.PatternLayout
     log4j.appender.DATABASE.layout.ConversionPattern=[framework] %d - %c -%-4r [%t] %-5p %c %x - %m%n
     log4j.appender.A1=org.apache.log4j.DailyRollingFileAppender
     log4j.appender.A1.File=SampleMessages.log4j
     log4j.appender.A1.DatePattern=yyyyMMdd-HH'.log4j'
     log4j.appender.A1.layout=org.apache.log4j.xml.XMLLayout
     ```

3. 配置log4j的为日志的实现

   - ```xml
     <settings>
     	<setting name = "logImpl" value = "LOG4J"></setting>
     </settings>
     ```

   - 

4. 直接测试运行。

   ```java
   static Logger logger = Logger.getLogger(UserDaoTest.class);
   public void testLog4j(){
       logger.info("info:进入testLog4j");
       logger.debug("debug : 进入了testLog4j")；
       logger.error("error:进入了testLog4j");       //均相当于System.out.println();
   }
   ```

   简单使用：

   1. 在要使用Log4j 的类中，导入类，import org.apache.log4j.Logger;

   2. 日志对象，参数为当前类的class

      - ```java
        static Logger logger = Logger.getLogger(userDaoTest.class);
        ```

   3. 日志级别
      1. info
      2. debug
      3. error
      
      

## 13.Limit实现分页

分页 是一种常见的应用。

减少数据的处理量，让效率更高。

使用Limit分页：

  ```sql
  select * from user limit 0,2;   //每页显示两个，从第零个开始查
  select * from user limit 2,2;
  select * from user limit 4,-1;//从第四个开始，到最后一个结束
  select * from user limit 2;  //从0 开始，显示两个
  ```

使用mybatis实现分页，核心就是SQL。

1. 接口
2. Mapper.xml
3. 测试

```java
public interface UserMapper{
    User getUserById();
    List<User> getUserByLimit(Map<String,Integer> map);
}
```

```xml
<select id = "getUserByLimit" parameterType = "map" resultType = "User">
	select * from mybatis.user limit #{startIndex},#{pageSize}
</select>
```

```java
@Test
public void getUserByLimit(){
    SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper mapper = sqlSession.getSqlMapper(User.class);
    Map<String ,Integer> map = new HashMaper<Stirng,Integer>();
    map.put("startIndex",0);
    map.put(pageSize,2);
    List<User> userList = mapper.getUserByLimit(map);
    for(User user : userList){
        System.out.println(user);
    }
    
    sqlSession.close();
}
```

## 14.RowBounds分页

RowBounds类，利用java的面向对象的思想，而不是用limit这种SQL语言。不过在这里面向对象没有limit优秀

```java
List<User> getUserByRowBounds();
```

```xml
<select id = "getUserByRowBounds" resultMap = "UserMap">
	select * from mybatis.user
</select>
```

测试

```java
@Test
public void getUserByRowBounds(){
    SqlSession sqlsession = MybatisYtils.getSqlSession();
    RowBounds rowBounds = new RowBounds(1,2)；//从第1个数据开始查看（还有第0个）；每页显示2个
    List<User> userList = sqlSession.selectList("com.gxl.dao.UserMapper.getUserByRowBounds",null,rowBouds) ;
    for(User u: userLsit){
        sout(u);
    }
}
```

不再使用SQL实现分页。

- 接口
- mapper.xml
- 测试

### 分页插件：

进入maven仓库网站。没找到

直接百度：Mybatis PageHelper

了解就好，万一公司的架构师说要使用，你需要知道它是什么

## 15.使用注解开发

除了mybatis外的其他东西都是用注解开发，但是mybatis主要使用配置文件。

面向接口编程。而不是面向对象编程。

- 根本原因： 解耦，可拓展，提高复用性

- 关于接口更深层次的理解：定义与实现的分离
- 接口的本身反应了系统设计人员对系统的抽象理解

使用注解开发：

要将mybatis文档倒背如流！

```java
public interface UserMapper{
    @Select("select * from mybatis.user where id = #{id}")
    User selectUserById(int id);
}
```

新建一个项目：mybatis-05

完全拷贝



编写接口

```java
public interface UserMapper{
    @Select("select * from mybaits.user")
    List<User> getUsers();
}
```

绑定接口（之前是绑定配置文件）在mybatis-config.xml 文件中

```
<mappers>
	<mapper class = "com.gxl.dao.UserMapper"/>
</mappers>
```

测试：

```java
@Test
public void getUsers(){
    SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper mapper = sqlSession.getMapper(UserMapper.class);
    List<User> userList = mapper,getUsers();
    for(User u : userList){
        sout(user);
    }
    sqlSession.close();
}
```

使用注解可以让代码变得简洁。但是对于稍微复杂的diamante使用注解就显得力不从心。如： 实体类属性和数据库字段不一样的时候 注解就没法处理

注解开发的核心就是使用java的类反射。

- 本质为： 反射机制实现
- 底层为： 动态代理

## 16.mybatis的详细执行流程

1. 通过resources对象获取加载全局配置文件。mybatis-config.xml 的所有内容都装载sqlSession 里面，打断点debug一下可以发现
2. 实例化SqlSessionFactoryBuilder 构造
3. 解析配置文件流 ，使用XMLConfigBuilder对象解析xml文件流，将信息都放在configuration中。所有的配置信息都放在Configuration对象里
4. 实例化SqlSessionFactory
5. 创建transactional 事务管理器
6. 创建excutor执行器。这是mybatis的核心的核心
7. 创建SqlSession
8. 实现 CRUD       回滚到步骤5
9. 查看是否执行成功 
   1. 是： 结束
   2. 否： 回滚到 步骤5

## 17.注解实现增删改查

### 自动提交事务

我们可以在工具类创建的时候实现自动提交事务。事务在增删改中都涉及，查 的时候不用管

```java
return sqlSessionFacroty.openSqlSession(true); 就可以得到自动提交事务的SQLSession，默认是不自动提交的。之后增删改后都不用commit了
```

通过id查询：

```java
@Select("select * from mybatis.user where id = #{id})
User getUserById(@Param（“id”） int id）);// 方法存在多个参数，每个参数前面必须加@Param("value"),"value" 中的value 才是注解中要用到的引用
```

```java
@Test
public void getUserById(){
     SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper mapper = sqlSession.getMapper(UserMapper.class);
   User user = mapper.getUserById(2);
    sqlSession.close();
}
```

```java
@Insert("insert into mybatis.user(id,name,pwd) values(#{id},#{name}.#{pwd})")
int addUser(User user);
```

```java
@Test
public void addUser(){
     SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper mapper = sqlSession.getMapper(UserMapper.class);
    int number = mapper.adddUser(new User(111,"name","pwd_hahaha");
    sqlSession.close();
}
```

```java
@Update(update user set name = #{name},pwd = #{pwd} where id = #{id})
int updateUser(User user);
```

```java
@Test
public void addUser(){
     SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper mapper = sqlSession.getMapper(UserMapper.class);
    int number = mapper.updateUser(new User(1,"name","pwd_hahaha");
    sqlSession.close();
}
```

```java
@Delete("delete from mybatis.user were id = #{uid}")
int deleteUserById(@Param("uid") int id);
```

```java
@Test
public void addUser(){
     SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper mapper = sqlSession.getMapper(UserMapper.class);
    int number = mapper.deleteUserByI(2);
    sqlSession.close();
}
```

注意： 我们必须一定要将Mapper接口注册到核心配置文件中

映射.xml 文件有捷径：

```xml
<mappers>
	<mapper resource = "com/gxl/dao/*.xml"/>   //可以一次注册整个包的.xml文件。或者。。。/*Mapper.xml
</mappers>
```

关于@Param（）注解：

- 无论基本类型的参数或者String类型的参数都需要佳航
- 引用类型不需要加
- 如果只有一个基本类型 可以忽略，建议都加上
- 我们在SQL中引用的就是我们这里param中设定的属性名

#{} 和${} de 区别：

- 都可以进行数据传递，甚至替换一下也无伤大雅。
- 但是#{} 能很大程度的防止SQL注入，既传入的数据是作为单独的字符串，不会和邻近相互作用拼接

## 18.LomBok的使用

工作中必须用

他是一个java库，是一个插件，是一个构建工具

再也不用写getter  setter or equal function，只需要加一个注解就可以了。都能夹什么注解呢：在idea中的plugins中，输入lombok，如果已经安装过插件，在右端会看到对它的介绍，会显示所有可以用的注解

使用：

1.  在IDEA中安装LomBok插件。
2. 在项目中导入jar包。。包在Maven仓库网站里。scope是作用域的意思，这个属性不用写，默认作用域所有环境

- @Data ： 无参构造  getter and setter  tostring  hashcode  equals 
- @AllArgsConstructor  全参构造
- @NoArgsConstructor   无参构造
- @Getter   放在类上对所有属性生成getter方法，放在属性上，给单个属性生成getter方法

