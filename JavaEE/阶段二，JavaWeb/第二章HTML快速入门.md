## 1.HTML快速入门

当打开一个网站时，首先映入眼帘的就是一个个华丽的网页

#### 网页的构成：

- html : 用来之作网页基础内容和基本结构
- css：用来之作网页的梅花效果
- javaSript  :  用来之作网页的动态效果

### HTML的介绍

html ：超文本标记语言

- 超文本：比普通文本更加强大
- 标记： 就是标签。可以使用一系列的标签，将网络上的文档格式统一，是分散的资源连接成一个逻辑整体
- 2014年10月，HTML5规范终于制作完成了

#### HTML的组成

HyperText Markup Language :超文本标记语言

- HTML页面是有一系列元素组成的，二元素是通过标签创建出来
- 属性：
  - 标签中来可以拥有属性，属性可以为标签提供更多的信息。
  - 属性只能添加到开始标签中，格式为：属性名 = 属性值
  - 例如 align 属性，代表对齐方式，我们乐意在开始抱歉中添加该属性，就能让内容在不同的位置显示了

元素举例：

\<h1 align = 'cneter' > 今天是个好日子\</h1>

开始标签，，结束标签，，内容，，属性

合起来就是元素

### HTML入门案例

案例效果：打开浏览器进入后，显示一个标题。同时上岗导航栏显示：入门案例，而且有idea的图标

实现步骤：

1. 在项目下的web目录中新建一个HTML文件
2. 修改<title>  标签中的内容：01-入门案例
3. 在<body> 标签中编写一个<h1> 标签，内容为：这是我的第一个HTML入门案例
4. 在<h1> 标签中指定align ，属性为center
5. 通过浏览器打开查看

 新建一个java项目，新增一个文件夹，命名为web，

在web文件夹中新建一个HTML文件。(初始会有一些基础标题)

在代码区域滑动一下鼠标，就会出现各个浏览器的图标。点击其中一个浏览器就好了。本地电脑的首先安装

### HTML概念小结

组成部分：

- 开始标签
- 结束标签
- 内容
- 属性

## 2.HTML基本语法

### 注释和标签规范

注释就是用来解释说明程序的

格式：

<!--  -->

idea快捷键：Ctrl + shift+/

#### 标签的书写规范

1. 标签的分类：

- 开始标签和结束标签 <h1></h1>
- 自闭和标签  <br/>换行 ，<hr/> 直线

2. 标签的嵌套：

正确的嵌套格式：

\<h1><u></u></h1>

3. 块级元素和行内元素
   - 块级元素 ：在页面中以块的形式展现，自己独占一行，后面的内容会自动换行。。<p>  <hr>  <div>
   - 行内元素 ：在页面中以行的形式展现，不会换行 。<b> 加粗  <i>斜体  <u>下划线  <span>

4. div  和span

   - \<div> 是一个通用的内容容器，没有特殊语义。一般用来对其他元素进行分组，用于样式化相关的需求

     </div>

   - <span>  : 是一个通用的行内容器，没有特殊的语义，一本被用来编织元素以达到me中样式

   - div和span的作用都是布局页面

### 属性和特殊字符

#### 属性： 

- 定义：
  - 可以提供一些额外信息，这些信息不会直接显示在内容中。但可以改变标签的样式或者提供数据使用

- 定义格式：
  - 属性名 = 属性值
- 属性的规范
  - 同一个标签中属性的名称必须唯一
  - 不区分大小写，建议使用小写
  - 属性值可以使用单引号或者双引号括起来，建议使用双引号
- 常用的属性
  - class ： 定义元素的类名，用来选择和访问特定的元素
  - id : 定义元素的唯一标识，在整个文档中必须唯一
  - name： 定义元素的名称，一般用于表单数据提交到服务器
  - value ： 定义元素内显示的默认值，一般用于表单标签中
  - style：定义元素的CSS样式

> <body>
>
> </body>

#### 特殊字符：

空格： 在文本解释中，连续的若干空格只能解释成一个空格

用：     \&nbsp;           表示一个空格



 换行： 文本解释中，无法识别换行。若想实现换行，s使用\<br/>  标签



<  符号：   \&lt;

\>符号  ：    \&gt;

"         :       \&quot;

'            :      \&apos;

&       :       \&amp;

## 3.新闻文本案例

### 效果演示和分析

新闻部分在中间显示，距离左右侧相同

分段布局

加粗字体

分割线

### 样式控制演示

1. div样式布局

   - 在<head>标签中通过<style>标签来控制样式

   - 样式格式

     > <style>
     >     标签名{
     >         属性名1: 属性值;
     >         属性名2: 属性值;
     >         ...
     >     }
     > </style>

   - 例如：

     > <style>
     >     div{
     >         border : 1px solid red;
     >         width : 60%;
     >         height : 500px;
     >         margin(外边距) : auto;//自动均匀分布
     >     }
     > </style>

### 文本标签演示

- p   段落标签

- h  标题 1-6

- hr   水平线<hr/>  属性：size   color
  - \<hr size = "4" color = "red"/>

- ul   无序列表...属性：type（disc 实心圆 、circle空心圆、square实心方块）
  - \<ul type="circle" >
        <li>java</li>
        <li>html</li>
    </ul>
    ​               

- ol  有序列表...属性：type（1  数字  、A或a 字母、 I或i 罗马数字）；start  起始位置（数字   起始位置）

- li   列表条目

- em  文本着重、斜体。。。同 i

- i    文本斜体

- strong   文本着重、粗体    同 b 

- b    加粗文本

- font    表示字体，可以设置样式(已过时)
  - 属性：size    color
- br  换行

### 案例实现

 实现步骤：

- 创建一个HTML文件
- 使用四个div标签划分区域（标题，作者，副标题，正文）
- 使用style标签设置div样式，宽度为60%,外边距为自动
- 使用<h1>  标签加入标题
- 使用font标签加入作者信息，颜色设置为灰色，字体大小为2
- 使用hr标签加入水平线
- 使用h3标签加入副标题
- 使用p标签家兔正文段落
- 使用ol标签加入有序列表
- 使用b标签加入部分文字加粗



## 4头条页面案例

### 效果演示和分析

![](D:\截图\JavaEE\2.png)

目前都是先用图片代替

学习图片和超链接和浮动知识

### 样式控制演示，浮动

浮动：

三个div

div默认自己独占一行

想要实现三个div并列排在一行

分为   ：   左浮动   和   右浮动

可以通国给div标签夹class属性，来控制不同的div样式

.left{

width : 20%;

float : left ;

}

.center {

width : 	60%;

float : left;

}

.right {

width : 20%;

float : left;

}

**属性值都需要用双引号引着**css**值并不用**

```html
<style>
    .left{
        width : 20%;
        float : left;
        height : 500px;
    }
    .footer{
        clear : both;//清楚浮动效果。之前设置了浮动，之后可能会默认浮动
        text-align : center;//文本的对齐方式。居中显示,居左 居右
        background : blue;
        
    }
</style>
```

css属性：

- float： left  right none 浮动

- clear : both    清楚浮动
- text-align : left right center   文本对齐方式
- background ： blue 等    背景颜色

### 图片标签的演示

img标签

属性：

- src  必须的属性，表示图片的地址
- title  鼠标悬停（hover）时显示文本
- alt  图形不显示时的替换文本
- height
- width

###  超链接表现

a标签：超链接

属性：

- href属性 ，表示超链接指向的URL 地址
- target： 页面打开方式
  - _self  当前页
  - _blank  新标签页

```html
<img src = "..." title = "广告" alt = "找不到图片了" height = "150px" width = "120px"/>
<a href = "..." target = "_blank">传智播客</a>
//给一张图片添加超链接
<a href = "..." target = "_self">
	<img src = "..." height = "200px" width = "200px" /> 
</a>
```

对超链接进行样式控制

```html
<style>
    a{
        //去掉超链接的下划线
        text-decoration : none ;
        //超链接文字的颜色
        color : black;
    }
    // 鼠标悬浮时的样式
    a:hover{
        color : red;
    }
</style>
```

**跳转地址还可以是自己写的其他页面。在idea中输入href = “”之后就会哟自动提示**

### 案例实现

实现步骤:

- 创建一个HTML文件
- 使用六个div标签划分区域（顶部图片，导航图片，左侧图片，中间正文，右侧广告图片，底部页脚超链接）
- 使用style标签设置div样式
- 使用img标签插入顶部图片
- 使用img标签插入左侧图片
- 完成中间正文内容填充
- 使用img标签插入广告图片
- 使用a标签插入页脚超链接

**高度一般不设置，让他随着内容进行填充**

让href = "#"   表示不进行任何跳转

### 案例效果演示和分析

输入框

单选框，性别

多选框，爱好

出生日期，日历

所在城市，下拉框

案例分析：

首先进行页面的布局，然后使用表单标签完成表单项

### 背景图片的演示

background ：url ("图片路径")    //添加背景

## 样式控制和演示

浮动：

左浮动，，，右浮动

div样式布局：

- 可以通过给div标签加上class属性控制不同和div，

  - > .left{
    >
    > width ： 20%；
    >
    > float : left;   // right 
    >
    > }

六个部分

<style>
    //给div标签添加边控
    div{
        border : 1px solid red;	
    }
    .left{
        width : 20%;
        float : left;
    }
    .center{
        width : 20%;
        float : left;
    }
    .right{
        width : 20%;
        float : left;
    }//通过class属性值对不同的div标签进行分别限制
</style>

### 背景图片演示

background ： url 

<style>
    background : url("../img/bf.jpeg");
</style>

### 表单标签

标签名：form

作用：表示表单标签

属性：

- action 属性，用于提交数据的路径
- method属性，提交表单的方式（get  post）
- autocomplete 属性 ，是否记录补全（on  off）.如果on，输入时会提醒之前输入的内容

```html
 <form action = "#" method = "get" autocomplete = "on">
     用户名 ： <input type = "text" name = "username"/>
     <button type = "submit">
         提交
     </button>
     
</form>
```

form 是表单标签。像是 输入框、下拉框、单选复选框等等都是表单项。表单项想要可以被提交，就必须放在表单表现内

> get方式：会把数据显示到地址栏中，地址栏url长度有限制
>
> post方式: 不会显示数据在地址栏中。安全，长度没有限制。请求数据在请求项中

### 表单标签的演示

表单项标签:

- label
  - 作用： 表单元素说明，配合表单项标签使用
  - 属性： for属性，属性值必须和lable辅助的表单项的id属性值一致。必须填
- input :
  - 表单项标签，多种输入类型来接受用户数据
  - 属性：
    - type属性，数据的类型
    - id属性，唯一标识
    - name属性，提交服务器的标识
    - value属性，默认数据值
    - placeholder属性，默认提示信息
    - required属性，是否必须有数据

- button 

  - 作用：按钮标签，不同的按钮用不同的作用

  - 属性

    - type属性，按钮的功能  	

      （submit，reset，button）reset是重置的意思

演示：

```html
 <form action = "#" method = "get" autocomplete = "on">
     <label for = "username" >用户名</label>
     <input id= "username" type = "text" name = "username" required/>
     <button type = "submit">
         提交
     </button>
     
</form>
```

lable : 点击lable字样后，光标就会进入对应的input中

### 表单项input标签type属性的取值

type的值很多歌，一共有十五个

- text  普通文本
- password  密码框，以小黑点代替数字
- email   有幸框，有简单验证，没有@符号无法提交
- radio，单选框，，选项必须具有相同的name属性值，value属性设置是只提交的值，checked属性代表默认选中
- checkbox，复选框，，选型必须具有相同的那么属性值，value属性设置实质提价的值，checked属性代表默认选中

```html
<form action = "#" method = "get" autocomplete = "off">
    <label for = "username">用户名</label>
    <input type = "text" id = "username" name = "password"/>
    <button type = "submit">
        提交
    </button>
    <button type = "reset">
        重置
    </button>
    //单选框
    <lable for ="gender" >性别：</lable>
    <input type = "radio" id = "gender" name = "gender" value = "man"/>男
    <input type = "radio" name = "gender" value = "woman"/>女<br/>  //第二个选框不写id。
    //想要达到单选功能，nmae属性必须相同
    //男  女只是提示语，没有其他功能，value的值才是真正要提交的内容
    
    多选框：
    <label for = "hobby">爱好</label>
    <input type = "checkbox" id = "hobby" name = "hobby" value = "youxi"/> 游戏
    <input type = "checkbox" id = "hobby" name = ”hobby" value = "音乐"/>音乐
</form>
```

### 表单项标签type属性演示2

其余属性值

- date 日期框 
- time 时间框
- datetime-  时间日期框
- number  数字框
- range滚动条数值框     min最小值，max 最大值 step步进值
- search 可清楚文本框
- tel 电话框
- url 网址框
- file  文件上传框
- hidden 隐藏域 value属性设置实际提价的值 ,不会再页面中显示

```html
<body>
    <label for = "birthday">sheng ri</label>
    <input type = "date" id = "brithday" name = "birthday"/><br/>
    
     <label for = "time">当前时间：</label>
    <input type = "time" id = "time" name = "time"/><br/>
    
     <label for = "insert">注册时间</label>
    <input type = "datetime-local" id = "insert" name = "insert"/
          <br/>
    
     <label for = "age">年龄</label>
    <input type = "number" id = "age" name = "age"/>
    
     <label for = "range">心情值</label>
    <input type = "range" id = "range" name = "range" min = "1" max = "10" step = "1"/>
  
     <label for = "search">可清除而文本</label>
    <input type = "serch" id = "search" name = "search"/>
    
    
</body>
```

###  其他常用表单项标签

- select标签名    作用：表示下拉列表标签    属性：与input标签常见属性相似
- optgroup    作用 ：表示下拉雷彪分组标签  属性： label属性，设置分组名称
- option   作用： 表示下拉列表项标签
- textarea  表示文本域标签  属性：rows属性代表行数，cols属性代表列数

```html
<body>
    <form action = "#" method = "get" autocimplete = "off">
        <option>--请选择城市--</option>
        <optgroup label = "直辖市">
			  <option>北京</option>
            <option>上海</option>
        </optgroup>
        <optgroup label = "省会城市">
       <option>杭州</option>
            <ooption>武汉</ooption>
       </optgroup>
    <br/>
        
        个人介绍：
        <textarea name = "desc" row = "5" cols = "20" ></textarea>
    </form>
</body>
```

### 案例实现

步骤：

1. 创建一个HTML页面
2. 使用两个div标签划分区域（顶部公司图标。中间注册信息）
3. 通过style标签设置样式
4. 使用img标签插入丁粗公司图片
5. 使用表单标签填充注册信息

```html
<head>
    <style>
        body{
            background : url("../img/bg.png");
           
        }
        .center{
            //背景颜色
           	background : white;
            width : 400px;
            text-align : center;
            margin : auto;
          
        }
        
    </style>
</head>
<body>
	<div>
        <img src = "../img/logo.png">
    </div>
    
    <div class = "center">
        <div>
            注册详情
        </div>
        	<hr/>	
        <form action ="#" method = "get" autocomplete = "off" >
            <div>
                <label for = "username" >姓名:</label>
                <input type = "text" id = "username" name = "username" value = "" placeholder = "在此输入姓名" required/>
            </div>
            
            
            
            
            <button type = "submit">
                注册
            </button>
            <button type = "reset">
                重置
            </button>
            
            <div>
                
            </div>
        </form>
    </div>

</body>
```



## css 快速入门

### css的介绍和组成部分

css   ： 层叠样式表

用于设置和布局网页的一种计算机语言，告知浏览器如何解析页面元素

#### 组成部分：

- 选择器：选择HTML元素的方式，可以使用标签名 、class属性名、 id值等多种方式
- 样式说明：用于给HTML元素设置具体的样式，格式是： 属性名 ： 属性值

具体格式

> 选择器 {
>
> ​	属性名 ： 属性值；
>
> ​	属性名 ： 属性值；
>
> ​	。。。
>
> }

### css 的 入门案例

![](D:\截图\JavaEE\4.png)	实现步骤：

1. 新建一个HTML文件
2. 在body标签内编写一个h1标签，内容为： 今天开始变漂亮
3. 在body标签中编写一个style标签
4. 为h1标签设置样式：颜色为红色，字体大小为100px；
5. 通过浏览器打开页面查看效果

```html
<html lang = "en">
	<head>
        <meta charset = "UTF-8">
        <title>入门案例</title>
        <style>
            h1{
                color : red;
                font-size : 100px;
            }
        </style>
        
    </head>
    
    <body>
        <h1>
            今天开始变漂亮
        </h1>
        
    </body>
    
</html>
```

#### 浏览器开发者工具

在页面中，点击右键，再 点击 "检查"

在右侧弹出的页面就是开发者工具，默认右边，放下边更合适（点击三个点的标识 可以更换位置）

开发者工具分为两个部分:左侧部分和右侧部分

- 左侧：
  - 最左边有个小箭头标识，点击后就可以在页面中选择元素了
  - Element 就是元素的显示，就是显示各个层级的标签。其实就是HTML源码
  - console  控制台
  - source 源代码，所有的代码和目录层级均显示
  - network 是网络的使用情况
  - memory 是内存的使用情况
- 右侧：
  - 只需要关注styles ，就是样式的控制还可以进行临时修改。只是临时修改，不会影响源代码的情况。一刷新就又恢复原样

### css小结

css层叠样式表，可以为HTML元素添加一些样式

## css 基本语法：

#### css的引入方式：

1. 内联样式，在标签中通过style属性引入，（属性值均需要有双引号）。只能控制当行标签

2. 内部样式：在head标签中通过style标签来控制样式，只能影响当前文件

3. 外部样式： 

   > 在head标签中通过link标签引入独立的css文按，可以影响不同的文件
   >
   > 引入格式：
   >
   > ​	<link rel = "stylesheet" href = "css文件路径">

举例：

```html
<head>
    <link rel = "stylesheet" href = "css/01.css"/>  //HTML文件与css文件夹在同一目录才这样写路径。
</head>
<body>
    <div>
        hello world
    </div>
</body>
```

```css
div{
    color : red;
    font-size : 100px;
}
```

验证路径是否写对：

按Ctrl键鼠标点击路径，如果有跳转则正确

推荐第三种方式，灵活性更高

### css的注释：

注释格式：

/*  ddddd */

```css
/* sdsds
sdsds
*/
div{
    
}
```

css的注释可以在css文件中写，也可以在style标签中写

### css的选择器

如果想对不同的标签进行不同的控制，就需要使用选择器

基本选择器：

- 元素选择器   : div{}
- 类选择器： .center{}
- id选择器 ： #username{}

```html
<head>
    <style>
        div{
            color : red;
        }
        .div_2{
            color : blue
        }
        #d1{
            color : pink;
        }
    </style>
</head>
<body>
    <div>
        hello 
    </div>
    <div class = "div_2">
        world
    </div>
    
    <div id = "d1">
        hhh
    </div>
</body>
```

有优先级:越通用，优先级越低

 				越精确，优先级越高

### 属性选择器

符号：[]

作用： 根据指定属性匹配元素

实例：

[type]{}     // 选中标签中带有type名称的元素

[type = text] {}  //

### 伪类选择器：

- 标签名：link       未访问的状态     a:link{}
- 标签名：visited 已访问的状态   a:visited{}
- 标签名 ： hover   鼠标悬浮状太    a:hover{}
- 标签名 ： active  已选中的状态    a:active{}

> 一般和a标签搭配使用

```html
<head>
    <style>
        a{
            text-decoration :none;
            取消下划线
        }
        a:link{未访问的状态
            color : blank;
        }
        a:visited{已经访问过的状态，既之前被点过
            color : blue;
        }
        a:hover {鼠标悬浮
            color : red;
        }
        a:active{//已选中，点击瞬间
            color : yellow;
        }
    </style>
</head>
<body>
    <a href = "https://www.aidu.com" target = "_blank" >百度一下</a>
    
</body>
```

### 组合选择器：

- 后代选择器
  - 符号： 空格
  - 作用：使用空格结合读个选择器，基于第一个选择器，匹配第二个选择器的所有元素
  - 示例：.center li{}
- 分组选择器 
  - 符号： ，（逗号）
  - 作用：可以同时并列匹配多个元素 
  - 示例：div,span,p{}

```html
<head>
    <style>
        .center li{
            color : red;
        }
        span,p{
            color : blue;
        }
    </style>
</head>
<body>
    <div class = "top">
        <ol>
            <li>aa</li>
            <li>bb</li>
        </ol>
    </div>
    <div class = "center">
        <ol>
            <li>cc</li>
            <li>dd</li>
        </ol>
    </div>
     <span>span</span>
    <br/>
    <p>
        nihao
    </p>
</body>
```

###  css小结

- 三种引入方式
  - 内联样式
  - 内部样式
  - 外部样式

- css的注释：
  - 和java的多行注释一样
- css的选择器：
  - 基本选择器：可以通过元素。类。id来选择元素
  - 属性选择器：通过属性选择元素
  - 伪类选择器
  - 组合选择器，
    - 后代选择器
    - 分组选择器

## 8.头条案例实现

### 案例效果和分析

### 边框样式

- border 设置所有边框
- border-top
- border-left
- border-right
- border-bottom
- border-radius  设置板框的弧度

属性值：

- solid  实线
- double  双实线
- dotted  原点
- dashed  虚线

```html
<head>
    <style>
        #d1{
            border 5px solid black;
            
        }
    </style>
</head>
```

### 文本样式

- color  文字颜色  属性值：颜色单词（red） RGB值（#ff0000)
- font-family  字体     属性值：微软雅黑，宋体
- font-size    字体大小   像素点（20px）
- text-decoration   文字下划线   
  - none 无
  - underline 下划线
  - overline 上划线
  - line-through  删除线
- text-align   文字水平对齐方式
  - left  居左
  - center  居右
  - right 居右
- line-align  行间距、行高
  - 像素点 20px
- vertical-align 文字垂直对齐方式  
  - top 居上
  - bottom  居下
  - middle 居中
  - 百分比调节

```html
<head>
    <style>
        div{
            color : red;
            font-family : 宋体;
            font-size : 25px;
            text-decoration : underline;
            text-align : center;
            line-height : 60px;
            
        }
        span{
            vertical-align : top;
            vertical-align : 50%;//垂直居中
            
        }
    </style>
    
</head>
```

### 顶部和导航条的实现

1. 创建HTML文件
2. 创建顶部div
3. 通过三个a标签实现登录、注册、更多  三个超链接
4. 设置顶部样式（背景色、行高、文字对齐方式、字体大小、超链接颜色、悬浮、和去除下划线）
5. 创建导航条《div》标签
6. 通过img标签引入logo图片
7. 通过两个<a>标签实现首页。科技两个超链接
8. 通过font标签实现正文两个字的显示
9. 设置导航条的样式（行高）

```html
<head>
    <style></style>
    <link  src = "stylesheet" href = "../css/o1.css"/>
</head>
<body>
    <!-- 顶部登录注册更多 -->
    <div class = "top">
        <a href = "#" >登录&nbsp;&nbsp;</a>
          <a href = "#" >注册&nbsp;&nbsp;</a>
          <a href = "#" >更多&nbsp;&nbsp;</a>
    </div>
    <!-- 导航条-->
    <div class = "nav">
        <img src = "../img/logo.png"/>
        <a href = "#">首页&nbsp;&nbsp;</a>/
         <a href = "#">科技&nbsp;&nbsp;</a>/
        <font color = "gray">正文</font>
        <hr/>
    </div>
</body>
```

> 在idea中创建css文件: 新建一个普通的File文件，命名时以.css 结尾

> ```css
> .top{
>     background : black;
>     line-height : 40px;
>     text-align : right;
>     font-size : 20px;
> }
> a{
>     text-decoration : none;
>     color : black;
> }
> .top a{
>     color : white;
> }
> a:hover{
>     color : red;
> }
> .nav{
>     line-height : 40px;
> }
> ```

### 左侧分享和中间政委和右边广告的实现

步骤：

1. 创建左侧分享的div标签
2. 通过a标签嵌套img标签和span标签实现图片和文字的显示
3. 设置左侧分享样式（宽度。文字水平对齐。浮动、图片大小、文字的垂直对齐）

```html
<body>
    <div class = "left">
        <a href = "#">
        	<img src = " "/>
            <span>&nbsp;评论</span>
        </a>
        <hr/>
        <a href = "#">
        	<img src = " "/>
            <span>&nbsp;转发</span>
        </a>
        <a href = "#">
        	<img src = " "/>
            <span>&nbsp;评论</span>
        </a>
        <a href = "#">
        	<img src = " "/>
            <span>&nbsp;空间</span>
        </a>
        <a href = "#">
        	<img src = " "/>
            <span>&nbsp;微博</span>
        </a>
        <a href = "#">
        	<img src = " "/>
            <span>&nbsp;微信</span>
        </a>
    </div>
    
</body>
```

```css
.left{
    width : 20%;
    text-align : center;
    float : left;
}
.left img{
    width : 38px;
    heght : 38px;
}
.left span{
    vertical-align : 50%;
    //middle 这个属性值很容易无效
}
/* 中间正文的样式*/
.center {
    width : 60%;
    float : left;
}
.right{
    width : 20%;
    float : left;
}
```

### 底部页脚超链接的实现

步骤：

1. 创建底部页脚div标签

2. 通过a标签实现超链接

3. 设置底部页脚样式（浮动，背景色，文字水平对齐，行高，超链接颜色）

   ```css
   .footer{
       clear : both;   //清除浮动效果
       background : blue;
       text-align : center;
       line-height : 25px;
   }
   .footer a{
       color : white;
   }
   ```

## 9.登录页面案例

### 案例效果与分析

css的盒子模型 是重点

首先要进行页面的布局，然后使用表单标签完成表单项

### 表格标签

标签名    作用   属性

- table 
  - 表格标签
  - 属性：
    - width 宽度
    - height 高度
    - border 边框
    - align 对齐方式

- tr  
  - 行标签
  - 属性：
    - align 对齐方式

- td 
  - 单元格标签（列标签） 
  - 属性
    - rowspan  合并行
    - colspan  合并列

- th  表头标签（自带加粗和居中）
- thead  表头语义标签
- tbody   标体语义标签
- tfoot 标脚语义标签

实现表格:

```html
<table width= "400px" border = "1px" align = "center"  >//align 是报个居中显示
    <tr>
    	<th>姓名</th>
        <th>性别</th>
        <th>年龄</th>
        <th>数学</th>
        <th>语文</th> 
    </tr>
    
    <tr align = "center">
    	<td>张三</td>
        <td rowspan = "2">男</td>
        //张三的性别占了两行，下面的哪一个格子注释掉
        <td>23</td>
        <td colspan = "2">90</td>
      <!--  <td>90</td>  -->
    </tr>
    
    <tr align = "center">
    	<td>李四</td>
       <!-- <td>男</td> -->
        <td>24</td>
        <td>99</td>
        <td>93</td>
    </tr>
    
    
</table>
```

语义化标签：head body  html也都是语义化标签

表格的语义化标签没啥用，只有标识作用。遇到认识就好

### 样式控制

样式名称    作用   属性值

- background-repeat   控制背景重复
  - no-repeat   不重复
  - repeat-x 水平重复
  - repeat-y  垂直重复
  - repeat  水平+垂直重复

- outline  控制轮廓   
  - double  双实线
  - dotted  圆点
  - dashed   虚线
  - none    无
- display    控制元素
  - inline   内联元素（无换行，无长宽）
  - block  ：块级元素 （有换行）
  - inline-block :内联元素（有长宽）
  - none ： 隐藏元素 

```html
<head>
<style>
	//背景图片重复
    body{
        background : url("../img/bg.jpg");
        backgorund-repeat : repeat-x;
        //默认为repeat
    }
    //轮廓的控制,轮廓就是边框状态.input输入状态下闪动的也是轮廓
    input{
        outline : double;
    }
    //元素显示的控制
    div{
        display : inline ;// 将div从块级元素变为内联元素。inline不能设置长和宽。none表示无法显示
    }
</style>
    
</head>
<body>
    用户名：<input type = "text"/>
    <div>
        春季
    </div>
    <div>
        夏季
    </div>
    <div>
        秋季
    </div>
    <div>
        冬季
    </div>
</body>
```

### 盒子模型--css的灵魂

万物皆盒子

盒子模型：是通过设置边框和元素内容的边距，从而实现布局的方式。分为内边距和外边距两种方式。

外边距：

- margin-top    上外边距  
  - margin-top : 50px;
- margin-left   
- margin-right
- margin-bottom
- margin  通用上下作用外边距
  - margin ： 50px;
- margin   单独  上右下左   外边距
  - margin ： 70px 34px 30px 65px;
- margin  自动计算外边距并水平居中
  - margin ： auto;

```html
<head>
    <style>
        .wai{
            border : 1px solid red;
            width : 200px;
            height : 200px;
            //内边距。设置内边距会导致外框的变化非常不方便。通产选择设置外边距
        }
        .nei{
            border : 1px solod blue;
            width : 100px;
            height : 100px;
            //设置外边距
            margin-top : 50px;
            margin-left : 50px;
            margin-right : 50px;
            margin-bottom : 50px;
            
            margin : 50px;
            
            margin : 50px 50px 50px 50px;  // 上右下左
            
            
            
           
        }
    </style>
</head>
<body>
    <div class = "wai">
        <div class = "nei">
            
        </div>
    </div>
</body>
```



内边距：padding  ...  形式和margin一模一样

### 登录页面案例的实现-顶部图片和表单的实现

1. 创建一个HTML文件
2. 创建三个div标签划分区域（顶部公司图标，中间表单，底部页脚）
3. 在顶部div标签中用img标签引入图片
4. 在中间表单div标签中通过表单标签和表格标签填充表单项
5. 设置样式（背景图片、背景色、宽度、外边距、弧度、文字水平对齐）

```html
<head>
  <link rel = "stylesheet" href = "../css/login.css"/>
</head>
<body>
    //顶部公司图标
    <div>
        <img src = "../img/logo.png"/>
    </div>
    //中间表单
	<div class = "middle">
        <form action = "#" method = "get"  autocomplete = "off">
            <table width = "100%">
                <thead>
                <tr>
                	<th colspan = "2">账&nbsp;密&nbsp;登&nbsp;录<hr/></th>
                </tr>
                </thead>
                <tbody>
               		<tr>
                    	<td></td><label for = "usernam">账号</label>
                        </td>
                <td>
                	<input type = "text" id = "username" name = "username" placeholder = "请输入账号" required/>    
                </td>
                    </tr>
            
            <tr>
                   
                    	<td></td><label for = "usernam">密码</label>
                        </td>
                <td>
                	<input type = "text" id = "username" name = "username" placeholder = "请输入密码" required/>    
                </td>
                    </tr>
    <tr colspan = "2">
    	<button type = "submit">
            确&nbsp;定
        </button>
    </tr>
                </tbody>
            </table>
        </form>
    </div>
    //底部页脚
    <div>
        
    </div>
</body>
```

```css
body{
   background : url("../img/bg.png");
}
.center{
    background : white;
     width : 40%;
    margin : auto;
    margin-top : 100px;
    border-radius : 15p;
    text-aligin : center;	
}

```

### 中间表单样式的实现

1. 设置表头样式（字体大小，颜色）
2. 设置表体提示躺尸（问题大小）
3. 设置表体输入筐样式（表框，弧度，宽度，高度，背景色，字体颜色，字体大小）
4. 设置表行样式（行高）

```css
thead th {
    font-size : 30px;
    color : orangered;
}
tbody label{
    font-size : 20px;
    
}
tbody input {
    border : 1px solid grey;
    border-radius : 5px;
    width : 90%;
    height : 40px;
    outline : none;
}
tr{
    line-height : 60px;
}
tfoot button{
    border : 1px solid srimson;
    border-radius : 5px;
    width : 95%;
    height : 40%;
    background : crimson;
    color : white;// 文字颜色
    font-size: 20px;
}
```

### 底部页脚的实现

1. 在底部页脚div标签中通过文字和a标签实现超链接

2. 设置底部页脚样式（宽度，外边距，字体大小，字体颜色）

3. 设置超链接样式（去除下划线，超链接文字颜色）

4. 在案例以头条页面登录超链接中引入跳转登录页面

   ```html
   <div class= "footer">
       <br/><br/>
       登录/注册既表示您统一&nbsp;&nbsp;
       <a href = "#" target = "_blank">隐私条款</a>&nbsp;&nbsp;&nbsp;&nbsp;
       <a href = "#" target = "_blank">忘记密码？</a>
       
    </div>
   ```

   ```css
   //底部页脚
   .footer {
       width : 35%;
       margin : auto ; //自动水平居中
       font-size : 15px;
       color : grey;
   }
   a{
      text-decoration : none;
       color : blue;
   }
   ```

   css的核心作用就是美化页面

### Nginx的介绍和安装

什么事Nginx：

- Nginx是一款服务器软件
- 其核心功能时可以和服务器硬件相结合，从而可以将程序发布到Nginx服务器上，让很多用户浏览

帮助我们发布网站。在同一个局域网内可以相互访问，如果想要通过外网访问，需要购买域名

安装Nginx步骤：

1. 进入CRT（并连接Linux）
2. 点击Alt+t  进入sftp路径
3. put  d:/.....   安装包的路径（在资源包里）
4. 然后进入Linux控制台（刚切换和控制台）进入管理员模式
5. 进入主界面：cd ~
6. ls 展示主界面内容
7. 然后 mv nginx-1.17.5.tar.gz  /home/
8. cd  /home/
9. ls 
10. tar -zxvf nginx-1.17.5.tar.gz  
11.  cd ngnix-1.17.5
12. ls
13. yum  -y install pcre pcre-devel
14. yum -y install zlib-devel 
15. yum -y install openssl openssl-devel
16. ls
17.    ./configure
18. make
19. make install
20. cd /usr/local/nginx/
21. ls
22. pwd
23. ls
24. cd sbin
25. ls

#### 启动Nginx

- cd /usr/local/nginx/sbin
- ./nginx    启动
- ./nginx -s stop   停止
- ./nginx -s reload   重启

启动后查看Nginx服务状态

- ps -ef | grep nginx

​	连接测试

通过浏览器：

http://ip地址（：80	）   //Linux的ip地址

### 案例发布

步骤：

1. 在/home下创建一个toutiao目录： mkdir toutioa

2. 将项目上川岛该目录下： put d:/web.zip

3. 解压项目压缩包 ： unzip web.zip

4. 编辑Nginx配置文件 vi /home/nginx-1-17.5/conf/nginx.conf

   - 找到server的大括号范围，修改location的路径

   - 既： 

   - > root  /home/toutiao

5. 关闭Nginx服务 ./nginx -s stop 

6. 关闭后启动Nginx服务并加载配置文件：

   > /usr/local/nginx/sbin/nginx -c /home/nginx-1.17.5/conf/nginx.conf 

7. 通过浏览器测试网站：

   http://192.222.222.222
