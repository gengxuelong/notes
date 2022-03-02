# javaweb核心

## 1.企业开发简介

### javaEE规范的介绍

 java企业版本

目前最新的版本是javaEE8

javaEE非凡是很多java开发技术的总称，一共包含13个技术规范

包括：

​	JDBC , JNDI,RMI ,IDL/CORBA, JSP , Servlet ，XML , JTA , JTS , JavaMail ,JAF

### web概括和资源分类

- web在计算机领域代表网络

- 像我们使用的www ，他是万维网的缩写

- 网络相关技术的出现都是为了让我们在网络世界中获取资源，这些资源存放的地方我们把它叫做网站
- 通过输入网站的地址（网址） ，就可以访问网站中提供的资源（部分局域网和广域网）

资源的分类

- 静态资源：资源是一成不变的，不同的人呢不同的时间访问的内容一样，我们编写的HTML、css、JavaScript都是属于静态资源

- 动态资源：网站中提供给人们展示的资源是有程序产生的，在不同的时间或者不同的人由于身份不同，所看到的内容是不一样的。作为开发者来说，我们编写的JSP、servlet等都属于动态资源

### 系统结构

在之前开发的都是java工程呢个，这些工程在企业中成为项目或者产品，他都是有系统架构的

- 基础结构划分：
  - CS结构
  - BS结构
- 技术选型划分
  - Model1模型
  - Model2模型
  - MVC模型
  - 三层架构+MVC模型
- 部署方式划分：
  - 一体化结构
  - 垂直拆分结构
  - 分布式结构
  - 微服务结构

先分析基础结构划分：

- CS 结构： 客户端 + 服务器的方式 。PC应用 手机应用  + 服务器 Client Server

- BS结构：浏览器 + 服务器的方式。Browser Server  

我们该阶段javaweb都是BS结构的

## tomcat

### 服务器的介绍

服务器是计算机的一种，性能由于一般计算机

内存 ： 256G 或 512G 。硬盘5000T 3000T

作用：在网络中为其他客户机提供计算或者应用服务。

- 而这里我们所说的服务器，其实就是web程序，或者应用服务器。把本质是一个软件，通过和硬件相结合，从而达到我们来发布应用的功能，让普通客户机访问我们的应用。
- 天猫服务器，就是一个大型应用服务器，客户机通过应用 或者浏览器访问服务器
- 常用的应用服务器：
  - weblogic  实现了javaEE规范，重量级服务器，又称javaEE容器
  - websphereAS  重量级服务器
  - JBOSSAS  重量级服务器，免费的
  - Tomcat 实现了JSP/servlet规范，是一个轻量级服务器，开源免费。

重量级服务器概念： 实现了所用13个javaEE规范的服务器。

### tomcat介绍

tomcat是Apache软件基金会的Jakarta醒目组中的一个核心项目

![](D:\截图\JavaEE\5.png)

### tomcat的基本使用

tomcat 下载后的安装：

直接解压就可以了

#### tomcat的基本使用

1. 启动
   - startup.bat    windows下的启动执行文件
   - startup.sh      Linux下的启动执行文件
2. 停止
   - shutdown.bat  Windows下关闭执行文件
   - shutdown.sh   Linux下关闭执行文件

进入tomcat的bin目录点击相应的可执行文件就行了

- 点击startup.bat 启动窗口。出行小黑窗。
- 叉掉小黑窗，就把服务器关了。或者点击shutdown.bat可执行文件

3. 启动问题
   - 启动后窗口一闪而过：没有配置jdk环境变量
   - java.net.BindException : 端口8080 被占用
4. 部署自己的项目
   - 在webapps目录下创建一个文件夹
   - 将资源放在该文件夹里
   - 启动tomcat，输入正确的路径

- 新建文件夹hello
- 在hello目录下新建HTML文件：hello.html

```html 
<h1>
    hello tomcat
</h1>
```

- http://localhost:8080/hello/hello.html 就可以访问到

### tomcat控制台乱码解决问题

乱码原因：cmd默认的编码格式是gbk； tomcat的配置信息中设定的默认编码格式是utf-8;

解决方案：

1. 进入tomcat的conf目录，找到logging.properties 配置文件

2. 找到语句：

   > java.util.logging.ConsoleHandler.encoding = UTF-8

3. 更改为： gbk

### idea 集成tomcat

一共就三个步骤

1. 点击idea的上方“运行” 按钮。点击EditConfigurations
2. 点击Defaults ->tomcat server -> Local
3. 点击configure-》Tomcat Home -》 选择tomcat所在路径

### Linux安装Tomcat

1. 上传压缩包到/home 路径 put d:/apache-tomcat-9.0.29.tar.gz
2. 解压压缩包：tar -zxvf ...gz
3. 进入bin目录下：cd apache-tomcat-9.0.29/bin
4. 启动tomcat服务器： ./startup.sh
5. 使用浏览器测试 http://192.168.203.139:8080/

> 在CRT中按下Alt + t 进入上传页面  sftp>

上传成功后，文件进入~目录下，返回元连接页面，在将他移动到home目录

> mv apache-... /home/

### javaWeb 项目的创建

idea2020 版本创建javaEE项目，先创建一个一般的java项目。再右击项目，点击第二个 “添加框架支持”，点击web即可

创建java Enterprise 项目

项目组成详解：

- src  ：存放源代码
- web ： 存放项目相关资源的（HTML css，JSP，图片等）
- WEB-INF ：存放相关配置（web.xml）

### idea发布项目

点击编辑配置

在 on update action    on frame deactivation 两个下拉框中，均选成 Update resources .这用我们更改代码后，Tomcat会自动重新加载。

项目访问路径名为 /myweb

则访问时：

localhost:8080/myweb/

省略了index.jsp.index.jsp是默认调用页面

项目路径名为 /时，则访问时只需要

localhost：8080

- 访问路径在 谢盖配置  -》 部署 页面
- 这个页面中还有我们项目打成的war包

### 通过war包发布项目

在项目的web目录下大war包

- 在该目录下进入cmd，输入命令：jar -cvf myewb.war .       //点代表当前路径

  //将当前目录打成压缩包

- 将打好的war包剪切到tomcat的webapps路径下

- 启动tomcat服务，自动启动war包通过林岚器验证结果

- localhost:8080/myweb/

### tomcat的配置文件

主配置文件： server.xml

<Connector port = "8080" protacol = "HTTP/1.1"  connectionTimeout = "20000"  redirectPort = "8443"/>

8080端口： tomcat服务默认端口号，访问url后必须手动写：8080

80端口号：HTTP协议采用的默认端口号。访问url地址后不用写80 

配置文件在tomcat的conf目录下

当以后发布正式的项目的时候，的把端口号改为80 ，这样人家访问的时候就不用输入端口好了	

### tomcat配置虚拟目录

虚拟目录的作用是：

发布任何目录下的项目，而不只是webapps目录下

 步骤：

1. 编辑server.xml配置文件，找到<Host>标签

2. 加入一下内容：

   > <Context path = "/my" docBase = "d:/my"/>
   >
   > path 是在地址栏中输入的路劲，docBase是项目存在的真实路径。（是项目文件，不是压缩包，这会儿没自动解压功能了）

### tomcat配置虚拟主机

虚拟主机的作用： 可以指定访问路径的名称

1. 编辑server配置文件，找到<Engine>标签，

2. 加入一下内容

   > <Engine ...>
   >
   > <Host name = "www.webdemo.com" appBase = "webapps" unpackWAR = "true" autoDeploy = "true">
   >
   > ​	<context path = "" docBase = "webdemo"/>
   >
   > </Engine>

   - name : 访问虚拟主机的名称
   - appBase : 项目存放的路径
   - unpackWARs : 是否自动解压war包
   - autoDeploy : 是否自动发布

3. 在windows中修改host文件

   > host  
   >
   > 1. ​    127.0.0.1 www.webdemo.com

- host文件在哪里呢：c:/windows/System32/driver/etc   目录

在浏览器中：

www.webdemo.com:8080

## 3.HTTP协议

### http协议的介绍

- 超文本传输协议

- http协议是基于TCP/IP 协议的；

- 超文本： 比普通文本更加强大

- 传输协议： 客户端和服务器的通信规则（握手规则）

 浏览器刷新一次页面，就是重新发起一次请求

​	注意：JavaScript css  图片资源会自动发起请求

### 协议的请求

1. 请求的组成部分
   1. 请求行
   2. 请求头
   3. 请求空行
   4. 请求体（get没有，post有）
2. 请求方式
   1. get
   2. post 

**注意： 只有post请求方式才有请求体**

get方式：

请求行：

> GET d login.html?username = aaa&password = 123 HTTP/1.1

请求头

 Host : localhost : 8080   // 请求的主机

User-Agent：                    //使用的浏览器

Accept:                                 //支持的资源类型，没显示全面

Accept-Language :            //支持的语言

Accept-Encoding :              //支持的压缩方式

Connection ： keep-alive     //持续链接

Referer  :                               //请求资源的路径

Cookie ：                                 //Cookie相关

Upgrade-Insecure-Requests : 1   //

if-Modified-Since : ...

if-None-Match : ...

请求空行：就是一个换行

请求体： get方式的请求没用请求体



POST方式：

请求行：

POST login.html HTTP/1.1

请求头

。。。和get相似。

请求空行  ： 就是一个换行

请求体：

username = aaa&password = 123

### http协议的响应

- 响应的组成部分
  - 响应行
  - 响应头
  - 响应空行
  - 响应体

- 相应行：POST HTTP/1.1 OK
- 响应头
  - Accept-Ranges : bytes    //数据的单位
  - ETag : ...                //该响应在服务器中惟一的标识
  - Last-Modified：。。    //最后修改时间
  - Content-Type : text/html
  - Content-Length : 2060
  - Date  : ..
  - Keep-Alive : timeout = 20  //超时时间
  - Connection : keep-alive

- 响应空行  ： 一个换行
- 响应体： 资源文件 



响应行：请求方式  HTTP/版本号  状态码 状态描述

常见的状态码：

- 200  一切正常
- 302 / 307 请求重定向 ，两次请求，地址栏发生变化
- 304  请求支援未发生变化，使用缓存
- 404 请求资源未找到
- 500 服务器错误



响应头

- 。。。
- 。。。需要时查阅百度

响应空行： 普通的换行

响应体： 将资源文件发送给浏览器进行解析，包括html文件，css。js文件

## 4.动态资源案例

### 发布静态资源

案例效果：

在浏览器中输入http://localhost:8080 出现一个页面

实现步骤：

- 创建一个javaweb项目
- 将静态页面所需要的资源导入到项目的web目录中
- 修改web.xml配置文件，修改默认主页
- 将项目部署到tomcat中
- 启动tomcat
- 打开浏览器查看页面

web_test1项目

修改默认主页：

在web.xml 文件中，

> <welcaome-file-list>
>
> ​		<welcaome-file>/news/news.html</welcome-file>// news目录在web目录下
>
> </welcome-file-list>

## 发布动态资源

- servlet是javaEE规范之一

- servlet是运行在java服务器上的程序，用于接收和相应来自客户端基于http协议的请求

- 如果想实现servlet饿得 功能，可以通过实现javax.servlet.Servlet 接口或者继承他的实现类
- 核心方法：service（） ，任何客户端的请求都会经过这个方法

### servlet快速入门发布动态资源

1. 创建一个javaweb项目。
2. 将静态页面所需要的资源导入到项目的web目录下
3. 修改web.xml配置文件，修改为默认主页
4. 在项目的src路径下编写一个类，实现servlet接口
5. 重写service方法，输出一句话即可
6. 配置web.xml配置文件，配置servlet相关资源
7. 将项目部署到tomcat中
8. 启动tomcat服务
9. 打开浏览器测试功能

web_text2 

修改默认主页

> <welcome-file-list>
>
> ​	<welcome-file>/html/frame.html</welcome-file>
>
> </welcome-file-list>

在src目录下：

创建一个包

建立一个studentServlet类

```java
public class StudentServlet extends Servlet{
    //重写所有方法。servlet是个接口
    //只关注service方法
    public void service(ServletRequest eservletRequest,ServletResponse servletResponse) throws ...
    {
        System.out.print("这是我的第一个动态案例")；//在控制台中输出
    }
}
```

在web.xml 文件中：

//servlet 的声明

> <servlet>
>
> ​	<servlet-name> sutdentServlet</servlet-name>
>
> <serlet-class>com.itcast.servlet.StudentServlet</servlet-class>
>
> </servlet>

//servlet的映射

> <servlet-mapping>
>
> ​	<servlet-name>studentServlet</servlet-name>
>
> <url-pattern>/srudentServlet<url-pattern>	
>
> <servlet-mapping> 

### servlet执行流程

地址栏中输入路径

通过映射 和 地址栏中的路径 找到servlet名称

通过 servlet名称 和 servlet的声明 找到相应的实现类

最后执行service方法

## 5.servlet

### servlet 介绍

servlet介绍

资料中有javaEE的文档

servlet是一个接口，是运行在网络中的java小程序

下面有两个实现类：

- Httpservlet
- GenericServlet

在接口中定义了一些方法

init方法   service方法   destroy方法

getServletConfig方法

getServletInfo方法

用于接收和相应来自客户端的基于http协议的请求

### servlet快速入门

步骤

1. 创建一个web项目
2. 创建一个类继承GenericServlet
3. 重写service方法
4. 在web.xml 中配置servlet
5. 部署并启动项目
6. 通过浏览器测试



GenericSerlvet 和 HttpServlet 均是抽象方法，不过大部分类已经实现了

项目servlet_demo1

```java
public class ServletDemo01 extends GenericServlet{
    @Overrides
    public void service(request,response){
        System.out.print("...");
    }
}
```

### Servlet 执行过程

- 客户端浏览器  
- tomcat服务器
- servlet_demo1 
- web.xml
- servletDemo01类

1. 发起请求
2. 解析地址
3. 找到对应的应用
4. 找到应用的web.xml
5. 解析请求资源地址url
6. 找到应用的资源
7. 执行service方法，响应给服务器

### servlet关系视图

入口为servlet接口

实现类：GenericServlet   HttpServlet  抽象类

ServletRequest接口，处理请求

ServletRequest 接口，处理相应

HttpServletRequest 接口 ，继承ServletRequest  .response 同理

HttpServlet  的参数为HttpServletRequest 和HttpServletResponse  

GenericServlet 的参数为ServletRequest和ServletResponse 。

ServletConfig接口：用于初始化Servlet的参数

ServletContext 接口：用于多个servlet之间信息的共享

### Servlet的实现方式

1. 实现Servlet接口，实现所有的抽象方法，该方法支持最大程度的自定义
2. 继承GenericServlet抽象类，必须重写service方法，启发方法可以选择性重写。该方法让我们开发Servlet变得简单，但这种方式和http协议无关
3. 继承HttpServlet抽象类。需要重写doGet 和doPost方法。该方法表示请求和相应都需要http协议相关

前两种实现过了

HttpServlet快速入门

步骤： 将重写Service方法换为重写doget方法

HttpServlet虽然是抽象类，但是没有抽象方法，继承后不会报错

service方法的作用相同，仍然为相应客户端请求，但是遇到get方法的请求，就调用doGet方法，。。所以service方法不用再理会

因为doGet和doPost 方法内容逻辑一般一模一样，所以在doPost方法中直接调用doGet方法就行了。

以后多采用第三种方式

### servlet的生命周期

出生  -》 活着 —》死亡

- 出生： 请求第一次到达Servlet时，对象创建出来，并且初始化成功，只出生一次，将对象放入内存中
- 活着： 服务器提供服务的整个过程，该对象一直存在，每次都是执行service方法
- 死亡： 当服务停止时，活着服务器宕机是，对象死亡

出生对应的是init方法

死亡对应的是destroy方法



结论： Servlet对象只会创建一次，销毁一次，所以Servlet对象只有一个实例。如果一个对象实例在应用中格式唯一的存在，那么我们就称他为单例模式

### Servlet线程安全问题

模拟用户登录功能来查看Servlet线程是否安全

1.  定义一个用户名的成员变量
2. 获取用户名
3. 将用户名相应给服务器

```java
public ServletDemo04 extends HttpServlet{
    private String username ;
    public void doGet(req,resp){
        username = req.getParameter("username");
        Thread.sleep(3000);
        printWriter pw = resp.getWriter();
        pw.println("welcome"+username);
        pw.close();
    }
}

servlet 配置 和 映射
```

结论： Servlet是线程不安全的。

解决： 定义类成员要谨慎，如果是公用的，并且只会在初始化赋值，其他时间都是获取的话，那么是没问题的，如果不是公用的，或者每次使用都用可能对其重新赋值，就要考虑线程安全问题了，可以将其定义在doGet方法里，或者使用同步代码块

将变量定义在方法内部，使其为局部变量

### servlet映射方式

1. 具体名称的方式，访问的资源路径必须和映射完全相同
2. /开头 + 通配符   。只要符合目录结构即可，不用考虑结尾是什么
3. 通配符 —— 固定格式结尾  。只要符合固定结尾格式即可，不用考虑前面的路径

演示：

ServletDemo05

```xml
<!-- 指定名称的方式-->
<servlet>
	<servlet-name>servletDemo05</servlet-name>
    <servlet-class>com.itheima.servlet.ServletDemo05</servlet-class>
</servlet>
<servlet-mapping>
	<servlet-name>servletDemo05</servlet-name>
    <url-pattern>/servletDemo05</url-pattern>
</servlet-mapping>

<!-- /开头 + 通配符 -->
<servlet>
	<servlet-name>servletDemo05</servlet-name>
    <servlet-class>com.itheima.servlet.ServletDemo05</servlet-class>
</servlet>
<servlet-mapping>
	<servlet-name>servletDemo05</servlet-name>
    <url-pattern>/servlet/*</url-pattern>// 目录前面只要是/servlet/，后面是什么都无所谓了
</servlet-mapping>
<!--通配符 + 固定格式结尾 -->
<servlet>
	<servlet-name>servletDemo05</servlet-name>
    <servlet-class>com.itheima.servlet.ServletDemo05</servlet-class>
</servlet>
<servlet-mapping>
	<servlet-name>servletDemo05</servlet-name>
    <url-pattern>*.do</url-pattern>//路径最后的部分只要是以.do结尾，最后部分其他的写的啥不重要，路径只要是找对项目了，路径也随意
</servlet-mapping>

```

配置的优先级问题： 越是具体的优先级越高，越是模糊的通用的优先级越低。

第一种 》 第二种 》 第三种

### Servlet多路径映射

我们可以给一个servlet配置多个映射(使用通配符），从而根据不同的路径实现不同的功能

场景分析：

如果访问的资源路径是/vip   商品打九折

如果访问的资源路径是/vvip 商品价格打五折

如果访问的资源路径是其他  商品不打折

ServletDemo06  

1. 定义一个商品金额

2. 获取访问资源路径

   > String path = req.getRequestURI();
   >
   > path = path.substring(path.lastIndexOf("/"));

3. 条件判断

   > if("/vip".equals(path)){
   >
   > ​	System.out.print("商品原价为：" + money + "优惠后： " +(money*0.9));
   >
   > }

多映射配置：

```xml
<servlet>
	<servlet-name>servletDemo05</servlet-name>
    <servlet-class>com.itheima.servlet.ServletDemo05</servlet-class>
</servlet>
<servlet-mapping>
	<servlet-name>servletDemo05</servlet-name>
    <url-pattern>/itheima/*</url-pattern>
</servlet-mapping>

```

### Servlet创建时机

更改创建时机

1. 第一次访问时创建
   1. 优势： 减少对服务器内存的浪费，提高了服务器启动的效率
   2. 弊端：如果有一些要在应用加载时就做的初始化操作，无法完成
2. 服务器加载时创建
   1. 提前创建好对象，提高首次执行的效率，可以完成一些应用加载时要做的初始化操作
   2. 弊端：对服务器内存占用较多，影响了服务器启动的效率

修改Servlet创建时机。在servlet标签中，添加<load-on-startup>标签

> <load-on-startup>1</load-on-startup>

//正整数代表服务器加载时创建Servlet对象。值越小，优先级越高。负整数或者不写代表第一次创建

优先级越高的Servlet越先创建

### 默认的Servlet

默认的servlet是有服务器提供的一个servlet，他配置Tomcat的conf目录中的web.xml中。

他的映射路径是<url-pattern>/</url-pattern>,我们在发送请求时，首先会在我们项目中的web.xml中查找映射配置，找到则执行，但是当找不到对应的servlet路径是，就去找默认的servlet，有默认的servlet处理。所以，一切都是Servlet

当我们输入错误路径后，错误的信息就是tomcat服务器的默认servlet发送个服务器的

tomcat服务器也是通过java编写的。

## 6.ServletConfig

### ServletConfig 的介绍

ServletConfig是Servlet的配置参数对象，在Servelet规范中，允许为每一个Servlet都提供一些初始化的配置，所以，每个Servlet都有一个自己的ServletConfig。

作用: 在servlet初始化的时候，把一些配置信息传送给Servlet

相当于Servlet的专属保姆

声明周期和Servlet完全相同

配置信息以键值对的形式存在

### ServletConfig的配置方式

每一个Servlet都有一个ServletConfig

在<servlet>标签中，通过<init-param>标签来配置，有两个子标签。

- param-name 
- param-value

要是配置多个参数值，需要写多个init-param 标签

 

```xml
<servlet>
	<servlet-name>servletDemo05</servlet-name>
    <servlet-class>com.itheima.servlet.ServletDemo05</servlet-class>
    <init-param>
    	<param-name>encoding</param-name>
        <param-value>UTF-8</param-value>
    </init-param>
    <init-param>
    	<param-name>desc</param-name>
        <param-value>This is ServletConfig</param-value>
    </init-param>
    
</servlet>

```

### ServletConfig 的常用方法

String getInitParameter(String name)

Enumeration<String> getInitParameterNames()  获取所有参数名称的枚举

String getServletName()  获取Servlet的名称

ServletContext  getServletContext()    获取ServletContext对象

```java
public class ServeltDemo07{
    //1. 声明servletConfig 对象
    private ServletConfig config;
    //2. 通过init方法，来对ServletConfig对象进行赋值
    public void init(ServleConfig config) {
        this.config = config;
    }
    protected void doGet(req,resp){
         		//3.演示config的方法
        String encodingValue = config.getInitParameterNames();
        while(keys.hasMoreElements()){
            String key = keys.next
                Element();
            String value = config.getInitParameter(key);
            System.out.println(key + "," + value);
            String name = config.getServletName();
            ServletContext context = Config.getServeltContext();
            System.out.pirntln(context);
            
        }
    }
}
```

> idea快捷键： .var 生成变量接盘

## 7.ServletContext

### ServletContext 的介绍

ServletContext是应用上下文对象（应用域对象）。每一个应用中只有一个ServletContext对象

并不会服务于某一个Servlet的

作用：可以配置和获取应用的全局初始化参数，可以实现Servlet之间的数据共享

这个对象的生命周期： 随着应用的加载二创立，随着应用的毁灭而毁灭

#### 域对象：

域对象指的是对象有作用域，也就是有作用范围。域对象可以实现数据的共享，不同作用范围的域对象，共享数据的能力也不一样。

在Servlet规范中，一共有四个域对象。ServletContext就是其中一个，他也是web应用中最大的作用域，也叫做application域，他可以实现整个应用之间的数据共享。

### ServletContext的配置方式

- 在web-app标签中，通过<context-param>标签来配置，有两个子标签
  - <param-name>
  - <param-value>

没配置一个键值对，就要写一个context-param 标签

```xml
<web-app>
	<context-param>
    	<param-name>
            globalEncoding
        </param-name>//名字随便起
    </context-param>
    <param-value>
    	UTF-8
    </param-value>
    
    <context-param>
    	<param-name>
            globalDesc
        </param-name>//名字随便起
    </context-param>
    <param-value>
    	hello hello
    </param-value>
</web-app>
```

ServletContext常用的方法

- String getInitParameter(String name)  根据名称获取全局配置的参数
- String getContextPath()  获取当前应用的访问虚拟目录
- String getRealPath(Stirng path)  根据虚拟目录获取应用部署的磁盘绝对目录

```java
doGet（）{
    1. 获取ServletContext对象
        ServletContext context = getServletContext();//底层调用的还是config的getServletContext（） 
    2.常用方法展示
        String value = context.getInitParameter("globalDesc");
    String path = context.getContextPath();
    String realPath = context.getRealPath("/");//项目的根路径。根路径就是web目录
    String c = context.getRealPath("/WEB-INF/c.txt");
    String b = context.getRealPath("/b.txt");
    String a = context.getRealPath("/WEB-INF/classes/a.txt");//获取在src目录下的文件的绝对路径（发布后的绝对路径，out目录中）
}
```

### ServletContext常用方法-传递数据

- void setAttribute(String name,Object value)    向应用域中存储数据
- Object getAttribute（String name)  通过名称获取应用域对象中的数据
- void removeArribute(Stirng name)   通过名称移除应用域对象中的数据

```java
//设置共享数据
context.setSttribute("username","张三");

//获取共享数据（另一个Servlet中)
Object value = servletContext.getAttribute("username");
System.out.println(value);

//删除共享数据
context.removeAttribute("username");

```

### 8.注解开发

### Servlet3.0 的规范

Servlet的配置：

- 基于配置文件，javaEE7,Servlet2.5
- 基于注解，javaEE8,Servlet3.0开始

基于注解，就可以不需要web.xml文件，用注解就实现了Servlet的声明和映射

### 自动注解开发的实现的步骤

1. 创建一个web项目
2. 定义一个类，继承自HttpServlet，
3. 重写doGet和doPost方法，
4. 在类上使用@WebServlet注解配置Servlet
5. 部署并启动项目
6. 通过浏览器测试

web.xml 文件虽然不需要了，但是WEB-INF文件夹还是很需要的，如果项目没有，需要手动创建，大小写都不能错

```java
//注解开发：
@WebServlet("/serveltDemo01")
public class ServletDemo01 extends HttpServelt{
    
}
```

###  WebServlet注解 的详解

注解的本质就是一个接口

### 手动创建容器

不去在注册文件中注册，也不使用注解注册

1. 定义一个类 ，继承 HttpServlet

2. 重写doGet 和doPost

3. 定义一个类，实现ServletContainerInittializer 接口

   - 注册配置servlet的功能类
   - 完成Servlet的创建和配置

4. 在src目录下创建WETA-INF 的包

5. 在META-INF包下创建一个services的包

6. 在services包下创建一个javax.servelt.Servlet.ContainerInitializer的文件

7. 文件中的内容为：容器功能注册实现类的全类名

8. 在容器功能注册实现类中onStartup方法中完成注册Servlet

   >public void onStartup(..){
   >
   >​	//完成Servlet的创建和配置
   >
   >//1.创建ServletDemo02的对象
   >
   >  ServletDemo02 servletDemo02 = new ServletDemo02();
   >
   >// 2. 在ServletContext对象中添加Servlet，并得到Serve两天的动态配置对象
   >
   >ServeltRegistration.Dynamic registration = servletContext.addServlet("ServeltDemo02",servletDemo02);
   >
   >//3.配置Servlet
   >
   >registration.addMapping("/servletDemo02");
   >
   >registration.setLoadOnStartup(1);//Servlet加载时机
   >
   >}

9. 部署并启动项目

10. 通过浏览器测试

## 9.学生管理系统

### 案例效果介绍

将输入的学生信息保存到文件中

### 案例实现

实现步骤

1. 创建一个web项目
2. 创建一个用于保存学生信息的HTML文件
3. 创建一个类，继承HttpServlet
4. 重写doGet 和doPost方法
5. 在web.xml 文件中谢盖默认主页和配置Servlet
6. 在doGet方法中接受表单数据并保存到文件中，并响应给浏览器结果
7. 部署并启动项目
8. 通过浏览器测试

```html
<body>
    <form action = "#" method = "get" autocomplete = "off">
        学生姓名:<input type = "text" name = "username"><br/>
        学生年龄:<input type = "number" name = "userage"><br/>
        学生成绩:<input type = "number" name = "userscore"><br/>
        <button type = "submit">
            保存
        </button>
        
    </form>
</body>
```

```xml
<welcome-file-list>
	<welcome-file>
    	/addStudents.html
    </welcome-file>
</welcome-file-list>
<servlet>
	<servlet-name></servlet-name>
    <servlet-class></servlet-class>
</servlet>
<servlet-mapping>
	<servlet-name></servlet-name>
    <url-pattern></url-pattern>
</servlet-mapping>
```

```java 
doGet(req,resp){
    String username = req.getParameter("username");
    Stirng age = req.getParameter("age");
    String score = req.getParameter("score");
    
    BufferedWriter bw = new BufferedWriter(new FileWriter("d:/stu.txt",true));
    bw.write(username + "," + age +"," + score);
    bw.newLine();
    bw.close();
    
    //响应给客户端
    PrintWriter pw = resp.getWriter();
    pw.println("Save success");
    pw
}
```

## 10 ，请求对象

### 请求对象的介绍

请求： 获取资源。在BS架构中，就是客户端浏览器想服务器发送的询问

请求对象： 就是在项目当中用于发送请求的对象

ServletRequest 和HttpServletRequest都是接口。我们只需要知道各个方法的功能是什么，具体的实现类tomcat会帮我们创建建。

ServletConfig 和 ServletContext也都是接口

### 获取各种路径的方法

- String getContextPath()   获取虚拟目录名称
- String getServletPath ()   获取Servlet映射路径
- String getRemoteAddr()  获取访问者ip地址
- String getQueryURL()  获取请求的消息数据
- String getRequestURI() 获取统一资源标识符.,不完整，从虚拟目录名称开始
- StringBuffer getRequestURL()  获取统一资源定位符，完整的路径，ip 端口号 和URI

URI是"共和国"

URL 是"中华人民共和国"

URI范围更大

参数和url之间用 ? 隔开

### 获取请求头信息的方法

- String getHeader(Stirng name)  根据请求头获取一个值
- Enumeration<String> getHeaders(String name)  根据请求头名称获取多个值
- Enumeration<String> getHeaderNames()  获取所有请求名称

```java
@WebServlet("/servletDemo02")
public class ServletDemo02 extends HttpServlet{
    protected void deGet(req,resp){
       String connection=  req.getHeader("connection");
        //名称不区分大小写
    Enumeration<String> values =     req.getHeaders("accept-encoding");
        while(values.hasNextElements()){
String value = values.nextElement();
        }
    Enumeration<String> names =     req.getHeaderNames();
        while(names.hasNext
             elements()){
            String name = names.nextElement();
            String calue = req.getHeader(name); 
        }
        
    }
}
```

### 获取请求参数信息的方法

- String getParameter(String name) 根据名称获取数据
- String[]  getParameterValues(String name)   根据名称获取所有数据
- Enumeration<Stirng> getParameterNames() 获取所有名称
- Map<String ,String[]> getParameterMap()  获取所有参数的键值对

> 要实现多选，要有相同的name值

```java
@WebServlet("/servletDemo03")
public class ServletDemo03 extends HttpServlet{
    @Override
    protected void doGet(req,resp){
        String name = req.getParameter("username");
        sout(username);
        String[] values = req.getParameterValues("hobby");
        for(Stirng hobby : values){
            sout(hobby);
        }
        Enumeration<String> names = req.getParameterNames();
        while(names.hasNextElements()){
            String name = name.nextElement();
            String value = req.getParameter(name);
            sout(value);
        }
        Map<Stirng,Stirng[]> map = req.getParameterMap();
        for(String key : map.get(key)){
            String[] values = map.get(key);
            sout(key+":");
            for(String value : values){
                sout (value);
            }
        }
    }
}
```

### 获取参数手动封装对象

将我们参数封装成一个对象，这样当我们再次使用这些参数的时候就更加方便

方式：

- 手动封装方式
- 反射封装方式
- 工具类封装方式 

```java
public class Student{
    private String username;
    private String password;
    private String[] hobby;
    
  	public Student(){
        
    }
    public Student(Stirng username,Stirng password,String[] hobby){
        this.username = username;
        this.password = password;
        this.hobby = hobby;
    }
    
    getter and setter;
    
    public String toString(){
        return "Student{" +
            "username = "+username +..... 自动生成
    }
}
```

### 通过放射进行封装
