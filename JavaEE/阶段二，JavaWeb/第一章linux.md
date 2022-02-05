# linux

## 1.初识Linux

### 操作系统简介

Linux操作系统更多的是应用于服务器

操作系统：

管理计算机硬件于软件资源的计算机程序

作用：

- 管理与配置内存
- 决定系统资源供需的优先次序
- 控制输入设备和输出设备
- 操作网络与管理文件系统等基本事物
- 操作系统也提供一个让用户与系统交互的操作界面

在操作系统中安装各种应用程序

主流的操作系统：

1. 桌面操作系统：
   - window系列
   - macOS
   - Linux
2. 服务器操作系统
   - Linux(免费)
   - Windows Server  (收费)
3. 嵌入式系统：（手表，家电）
   - Linux
4. 移动设备操作系统
   - Linux
     - Android
     - 华为鸿蒙
     - (由Linux演变过来的)
   - ios

### 初识Linux，发展历程

1994 Linux1.0正式发布

- 用我的Linux就收钱
- 把源代码都给别人

最开始的1.0才一万行代码

前身为Minix操作系统

### 初识Linux特点

Linux是一套免费试用和自由传播的Unix操作系统

Linux的特点：

- 两个基本思想
  - 一切都是文件
  - 每个软件都有明确的用途
- 完全免费
- 完全兼容POSIX1.0标准
- 多用户，多任务
- 良好的界面
- 支持多平台
- 其他三个优点：
  - 云代码完全开源
  - 具有非常强大的网络功能
  - 工具链完整，（简单操作就可以配置出合适的开发环境，可以简化开发过程，减少开发中仿真工具的障碍，使得系统具有较强的移植性

###  Linux 与其他操作系统的区别

Linux是基于Unix的

Linux和Unix的区别

- 开源情况
- 硬件使用
- 本质不同

Linux和windows区别

- 系统界面，Linux更好
- 驱动程序，Windows更好
- 系统使用
- 学习，Linux更好
- 软件使用LInux中大部分软件是免费的，Windows软件更多
- 开放性
- 文件格式不同
- 免费和收费
- 技术支持
- 安全性:Linux开放源代码，不会有黑箱操作
- 开源
- 使用习惯：Linux更侧重命令行，windows更侧重图形化界面
- 软件与支持：Linux几乎无法运行游戏。

Linux更适用于企业服务器使用

### 发型版本

![](D:\截图\JavaEE\1.png)

CentOS Linux的一种发型版本，乌邦图也是一种发型版本，我们学习CentOS

## 2.Linux安装与使用

### 虚拟机简介

先安装虚拟机，在安装Centos

VMware虚拟机：

- 不需要分区或重新开机就能在同一台PC上使用两种以上的操作系统
- 完全隔离并且保护不同的操作系统的环境以及所用的软件和资料
- 不同的操作系统还能互动操作
- 有复原功能
- 能够设置并且随时修改操作系统的操作环境

虚拟机有两种：

VMware workstation 

VirtualBox 

我们用第一种

### VMware下载：

网址:https://www/vmware.com/cn.html 

### 安装

所有的勾选都要勾选（除了要选择位置的页面）

检查是否安装成功：

打开网络和共享中心——>更改适配器设置--》发现有两个VMware

### 下载和安装CentOS

官网: https://www.centos.org/download/

点击：centOS Linux DVD ISO 

选择CentOS-7 63位 的版本

#### 安装

打开虚拟机：

1. 点击创建洗呢虚拟机
2. 选择第一个：典型
3. 选择第三个：稍后安装操作系统
3. 选择第二个：安装Linux 系统 ，版本选择CentOS 7  64位
4. 给虚拟机取个名字：gxl_linux,设置位置：D盘APP目录中：Linux-VMware-File 
5. 最大磁盘，默认20G，选择第二个：将磁盘的拆分成多个文件
6. 点击自定义硬件
7. 点击"新CD/DVD",在右边选择“使用ISO映像文件”-》点击浏览，选择centOS7.exe文件--》点击打开-》点击关闭
8. 点击完成
9. 发现VMware界面左端“我的计算机”下多了一个虚拟机

**注意：**虚拟机放置的目录Linux-VMware-File文件必须放在D盘根目录下，不能放在子目录

### 启动虚拟机-CentOS设置

1. 点击开启此虚拟机（等5-10分钟）
2. 设置语言：中文，在最下面，点击继续
3. 耐心等一会儿，右下角黄色感叹号会消失大半，仅剩下安装位置这一项是感叹号，点击进入去设置他
4.  其实啥也不用动，再点击左上角的完成就可以了
5. 点击软件选择，这里需要严肃修改一下。在基本环境中选中“GNOME桌面”，在点击左上角的完成就好了（再等一会让感叹号自动消失）
6. 然后点击右下角的安装就好了
7. 此时等待安装的过程，设置一下我们的管理员密码：
   - root密码：root账号是拥有管理系统。root密码为Gxl2236035.
   - 点击左上角的完成呢
8. 数分钟后，安装完成，显示“完成"字样。点击右下角的重启按钮
9. 重启后，点击“未接受许可证”，进入后，点击接受，点击完成
10. 点击右下角的“完成配置”
11. 选择语言： 汉语
12. 选择键盘：英语（美国）
13. 隐私，位置服务：尽量不打开
14. 右上角，点击前进（点击“自由拉伸"可一屏幕显示所有，不用拖动屏幕）
15. 设置时区：上海，上海，中国
16. 连接在线账号，跳过
17. 创建一个用户：用户名称：gengxuelong
18. 密码：Gxl2236035.
19. 点击右上角的前进
20. 点击开始使用

### 启动虚拟机你，静态IP配置

1. 在window系统里，进入适配器设置，确保VMware的VMnet8已启用
2. 打开虚拟机
3. 编辑- 》虚拟网络编辑器
4. 选择VMnet8，设置子网ip
5. 点击更改设置，点一下就好了，再点击VMnet8
6. 点击子网ip：设置为192.168.47.0
7. 子网掩码：设置为255.255.255.0
8. 点击NET 设置
9. 设置网关：192.168.47.2
10. 点击确定
11. 点击确定
12. 此时虚拟机就设置过了，接下来到centOS在操作系统层面对网卡进行配置项信息的修改
13. 点击应用程序（在Linux操作系统中）
14. 点击终端

> $ su root//切换为用户root
>
> 密码：............
>
> '#'  vi /etc/sysconfig/network-scripts/ifcfg-ens33
>
> ....
>
> ....
>
> 再按一下回车键
>
> 打开一个文件，是centOS的网卡配置文件 
>
> 先按一下i,进入编辑模式（INSERT）
>
> 将文字换成一下文字：
>
> > TYPE=Ethernet
> > PROXY_METHOD=none
> > BROWSER_ONLY=no
> > BOOTPROTO=static
> > IPADDR=192.168.47.129
> > NETMASK=255.255.255.0
> > GATEWAY=192.168.47.2
> > DEFROUTE=yes
> > IPV4_FAILURE_FATAL=no
> > IPV6INIT=yes
> > IPV6_AUTOCONF=yes
> > IPV6_DEFROUTE=yes
> > IPV6_FAILURE_FATAL=no
> > IPV6_ADDR_GEN_MODE=stable-privacy
> > NAME=ens33
> > UUID=2c2371f1-ef29-4514-a568-c4904bd11c82
> > DEVICE=ens33
> > ONBOOT=true
>
> 先按下esc键，退出编辑模式
>
> 按下命令：
>
> > :wq!
>
> 退出文件
>
> '#' systemctl restart network
>
> '#'  ifconfig//查看Linux系统的ip，其值为我们在配置文件中的更改内容
>
> 。。。。
>
> 配置成功

15. 在windows系统的cmd中验证一下,zai cmd 中；

> ping 192.168.47 .129
>
> ...
>
> ...
>
> 可以ping得通

16. 距离Linux连上网还有最后一步操作
    - 点击“虚拟机”（在虚拟机软件中，左上角）
    - 点击设置
    - 点击网络适配器，
    - 点击添加
    - 点击网络适配器
    - 点击完成
    - 将第二个网络适配器选为NET 模式
    - 点击确定
17. 完成，可以上网了

### 安装注册和配置CRT

如果总是在虚拟机里面操作centOS，总是有些不方便

通过第三方工具SecureCRT，是一款终端仿真程序

在Windows下安装CRT，然后用CRT 连接Linux

一直选择下一步就好了

SecureCRT的激活和注册，参照手册进行

两个配置：

- 基本配置（登录）
- 其他配置：（字符集，字体大小，屏幕颜色）

1. 双击打开CRT ，进去后会有连接小页面，如果每:file--》quick Connection
2. 输入:
   - HostName:192.168.47.129(Linux的ip）
   - UserName:gengxuelong
3. 点击右下角的connect，开始连接
4. 会弹出密码输入页面：Gxl2236035.
5. 勾选保存密码
6. 设置字符集等
   - 点击Options
   - 点击session options
   - terminal ->Appearance
     - 字体:仿宋  16pt
     - 编码集：utf-8
     - 背景颜色：current color scheme;;下拉框，选择最后一个
   -  

### CentOS目录与文件

Linux 没用盘符的概念。	在总根目录下，是各种文件。只有一个根目录/

etc 文件：系统中的配置文件

bin

sbin

usr:系统预设执行文件的放置目录

var/log：程序运行日志的存放目录

在CRT里演示一下：

>$ cd /
>
>$ ls -l    展示当前目录中的所有文件（夹）

### CentOS-时间同步

> $ date         显示系统的时间

进入虚拟机，

右键点击gxl-linux ,点击设置，点击选项，点击VMware tools，勾选 将客户机时间与主机同步

### contOS 的克隆系统和还原系统

系统备份：克隆

克隆方式的特点：

- 占用空间大
- 源系统不在时，克隆系统还能用

方法：

1. 右键点击虚拟机gxl-linux
2. 点击管理
3. 点击克隆，发现：无法为开启或挂起的虚拟机进行克隆。注意一定要关闭虚拟机
4. 点击下一步
5. 选择第一个：克隆虚拟机当前的状态
6. 点击下一步
7. 点击第二个：克隆完整的系统
8. 为克隆体起个名字，并选择储存位置
9. 点击关闭

如何启动克隆的系统：

- 文件
- 打开
- 找到.vmx文件.这样就把恐龙的虚拟机加载到“我的计算机”目录中了，点击开启此虚拟机即可

### 系统备份--快照

相当于给源系统拍了一张照片，并没有保存完整的系统

特点：

- 占用空间小
- 原系统不存在，就无法使用

方法：

1. 右键点击虚拟机
2. 点击 快照
3. 点击 拍摄快照
4. 为快照起个名字，最好包括时间，描述可写可不写
5. 点击  拍摄快照
6. 如果系统没哟报错，照片就成功生成了
7. 快照的还原
   - 右键点击虚拟机，
   - 点击  快照
   - 点击  快照管理器
   - 点击之前拍过的照片
   - 点击  转到
   - 发现提示：回复此快照后，当前状态将消失
   - 点击  是
   - 如果系统没有报错，那就转成功了

## 3.系统与设置命令

### 用户相关命令 -- 账号管理

在公司中，用CRT连接服务器，通过CRT远程管理服务器

Linux命令总共有两百多个，和快捷键一样，不用刻意记忆。需要用什么就查一下，用多了自然就记住了。关键是Linux的语法和结构

账号管理：

- 创建用户：useradd （选项） 用户名

  - > $ useradd aaa    ---提示权限不够，需要切换到管理员的账号上
    >
    > $ su root 
    >
    > 密码：
    >
    > '#' useradd aaa
    >
    > '#' su aaa         //此时aaa无密码，刻意直接切换
    >
    > $ 
    >
    > 

- 用户口令：passwd（选项） 用户名

  - > $su root 
    >
    > #passwd aaa
    >
    > 更改用户aaa的密码。
    >
    > 新的密码：
    >
    > 重新输入密码：
    >
    > passwd : 所有的身份令牌已经成功更新
    >
    > '#' su gengxuelong
    >
    > $ su aaa
    >
    > 密码：

> 有关密码的要点：
>
> 1. 输入密码时无* ，而是完全不显示
> 2. 密码不能是回文
> 3. 密码可由字母、数字、字符组成，且至少8位以上
> 4. 进入root用户必须输入密码，在root用户中进入其他用户不用输入密码，在一般用户中，进入其他用户需要输入密码

> 有关用户的要点：
>
> **跟用户（root）的开头符号为# ，一般用户的开头符号为$**

- 修改用户 ： usermod 选项  用户名

  - 选项表示要修改用户的什么东西

  - > $su root     //进入root才有权限修改用户
    >
    > 密码：
    >
    > #usermod   //直接点击回车，可查看选项都有什么（其他用户相关命令相似）
    >
    > 其中：
    >
    > -l  --login LOGIN  新的登录名称（--后是对l这个字母的全称注释）
    >
    > #usermod -l czbk aaa
    >
    > //aaa 这个用户的用户名改为czdk
    >
    > 发现提示：用户aaa 正在使用，无法修改
    >
    > 处理方式:1.直接断开连接，重新连接，这样aaa就不在使用中了。
    >
    > 处理方式2：Ctrl + d ,或者输入exit命令，退出当前用户，然后回到上一个用户，知道退到上面没再有aaa为止。退到头的话会直接断开连接，再重新连接一下就好
    >
    > 此时：
    >
    > #usermod -l cadk aaa
    >
    > #

- 删除用户： userdel (选项) 用户名

  - ​	同上，如果csdk在运行，则给出提示并无法执行。

  - 处理方式同上

  - 看一下选项：

    - -f  强制删除
    - -r  删除主目录和邮件池，既删掉一切信息

  - 两个选型结合可以使删除更加彻底干净

  - > #' userdel -r -f czdk
    >
    > '#' su csdk

### 用户组相关的命令

用户组其实就是为了方便管理用户的

给这个组添加权限，那这个组的成员都拥有这个权限

用户组相关的四个命令：

- 创建用户组：groupadd (选项) 用户组的名字

  - > $ groupadd  kaifa
    >
    > 权限不够
    >
    > $ su root
    >
    > 密码：
    >
    > '#'goupadd kaifa

- 修改用户组

  - groupmod (选项) 用户组名

  - > '#' groupmod  //查看选项
    >
    > -n 修改名字
    >
    > '#' groupmod -n kaifazu kaifa
    >
    > '#' //只要系统没有报错，就算操作成功了

- 查询用户所属组： groups 用户名

  - >#groups itcast
    >
    >itcast : itcast wheel
    >
    >   // 既，如果一个用户没有被分组，那么查询它所属组的名字结果为它自己的名字

- 删除用户组： groupdel 用户组名

  - > '#' groupdel kaifazu
    >
    > 

### 管理用户组内成员

语法： gpasswd (可选项） 组名

gpasswd 是Linux下的管理工具，用于将一个用户添加到组或者从组中删除

选项：

1. -a : 添加用户到组
2. -d：从组中删除用户
3. -A： 指定组成员为管理员
4. -M： 同-A
5. -r: 删除密码
6. -R： 限制用户登入组，只有组中成员才可以用newgrp加入该组

> '#' groupadd kaifazu 
>
> '#' useradd user1
>
> '#'useradd user2
>
> '#' useradd user3
>
> '#'gpasswd -a user1 kaifazu
>
> '#'gpasswd -a user2 kaifazu
>
> '#'gpasswd -a user3 kaifazu
>
>  // 验证：
>
> '#' grep 'kaifazu' /etc/group
>
> kaifazu : x: 1002 : user1,suer2.user3
>
> '#'

> 小技巧： **按上键可以调出上一个命令行**

### 日期管理

语法: date [参数选项]

参数选项：

1. -d <字符串> ：显示字符串所指的日期和时间,<>符号无意义
2. -s<字符串> 根据字符串设置日期和是时间
3. -u 显示GWT。英国格林威治时间
4. --help :在线帮助
5. --version:显示版本信息

> $ date
>
> 2022 ....//显示当前时间
>
> $ date -d "2020-12-12 11:11:11"
>
> 2020年 12月12日 星期六 11:11:11 CST   //CST是指北京时间
>
> $date -s "2020-12-12-12 11:11:11"
>
> date: 无法设置日期，不允许的操作  //其实是权限不够
>
> su root 
>
> 密码：
>
> '#' date -s "2020-12-12 11:11:11"
>
> 2020年。。。。//修改成功
>
> ’#'date --help
>
> ...

#### 显示用户：

logname  [--help] [--version]

显示登录账号的信息

> $ logname
>
> gengxuelong //仅仅就是显示当前登录的账号信息

#### 切换用户

 su  [USER]   //还可以跟一些选项

> $ su root
>
> 密码：
>
> "#" su //回车
>
> -c  IQ切换用户去执行命名，执行完毕之后在变回原来的使用者
>
> '#' su itcast 
>
> $ su -c ls root
>
> 密码：
>
> ....//  这句命令的含义是：先切换到root用户，再执行ls 这个指令，然后在切换回ITcast用户

### id命令

id [-g]  [--help] [--version]

查看当前用户的详细信息(用户id，群组id，所属组)

-g或--group：显示用户所属群组的ID



最常用的是单独使用id

> id    // 回车
>
> uid 自己的id     gid  组的id

#### sudo命令

sudo [参数选项]     提高普通玉蝴蝶额操作权限

参数选项：

1. -V   显示版本号
2. -h 会显示版本编号和指令的使用方式
3. -l  会显示自己的权限
4. -v 超出N分钟没有使用，要求再次输入密码（默认5分钟）
5. -k  下次执行sudo时 问密码
6. -s 执行环境变数中的SHELL 对指定的shell，或是etc/passwd 里所指定的shell。
7. -H 将环境变数中的HOME 指定为要变更身份的使用者HOME 目录
8. sudo command 要以系统管理员身份（或以-u更改为其他人）执行的指令

>$sudo ls
>
>$sudo -u root ls   // -u  指定root用户做ls这条指令

> 只用在sudoers文件中登记的用户才可以使用sudo临时提升权限。
>
> 已知我们第一个用户gengxuelong在该文件夹中。其他新建的用户都不在

### 进程相关命令。top,ps,kill

同windows的任务管理器

top命令。实时显示process的动态

> top  //直接换行
>
> 就会显示所有的进程信息：
>
> PID :线程的id编号
>
>  USER：线程所属的用户
>
> PR:优先级，整数优先级低
>
>  NI 优先级，有负数优先级高（和NI恰相反
>
> VIRT：使用虚拟内存的总量
>
>  RES ：没讲
>
> SHR ： 没讲
>
> S ：线程状态： S 睡眠状态。R运行状态 
>
> %CPU 
>
> %MEM 
>
> TIME+COMMAND ：命令的名字

因为top命令是实时监控状态，如果top命令不停，根本就没办法输入其他命令。

停止的方法： 按下：q

带参数选项的top命令

> top -c  
>
> //command 数据项把命令行显示完整

> top -p 12095
>
> //加的是进程的id

结束监控的快捷键：q

#### ps 命令

ps [option] [--help] 查看进程信息，静态的当前时刻的进程信息

只显示当前这个时刻的进程信息，运行的进程才显示。

> $ ps  // 显示正在运行的进程的信息

带参数的ps

> ps  -A//显示所有的进程信息.

上面显示的进程信息只要：PID  TIME CMD

> ps -ef//显示所有数据项

> ps -u 用户名
>
> //显示归属用户的所有进程信息

#### kill命令

杀死进程，中断执行中的程序

kill 1111//杀死id为1111的进程

kill -编号 1111   // 通过编号选择如何杀死1111进程

> $ kill 12249

在CRT中可以在点击一下Linux的ip，可以再开一个连接端口

先在一个端口： top，，，top这是一个持续运行的进程。

再在另一个窗口中写： kill 12249（号不确定），发现第一个窗口中top的实时监控已经停止了

带编号的：

> kill -9 12323    //-9 表示强制杀死

 kill -l   //L的小写    // 查看所有编号的作用，最常用的为-9

想要杀死一个用户的所有进程：

两种方式：

1. $ kill -9 $(ps -ef|grep itcast)

   //杀死所有itcast用户的进程，因为itcast是主用户，所以连接也会断掉

2. $ killall -u itcast

## 4.Linux的目录管理

### 关机和重启命令--shutdown  reboot

关机命令：shutdown参数：

1. -t second ： 设定在几秒后关机
2. -k：并不会真正关机，只是将警告讯息传送给所有使用者
3. -r:关机后重新开机
4. -h:关机后停机
5. -n : 不采用正常程序来关机，用强迫的方式杀掉所有执行中的程序后自行关机
6. -c ： 取消目前已经进行中的关机动作
7. -f: 关机时，不做fcsk动作（检查Linux档系统）
8. -F： 关机时。强迫进行fsck动作
9. time： 设定关机时间
10. -message :传递给所有使用者的警告信息

>$ shutdown 
>
>Must be root
>
>$ su root
>
>密码：
>
>'#' shutdown 
>
>一分钟后关机、  //sentOS 6 及之前是立马关机

带参数的命令：

> '#' shutdown +1 "分钟后关机"
>
> // +1 指一分钟，后面的字符串是解释信息

> shutdown -c   //取消正在执行的关机动作

> shutdown -r +1 "一分钟后重启"

#### 重启命令

reboot  

有参数，但最常用的是裸用

> '#' reboot //立马重启

### 系统管理的其他命令：who  timedatectl   clear

#### who命令。

who -[husfV] [user]

显示当前登录系统的用户

多人操作同一个服务器

> '#' who     //列出所有已经登录的用户

带参数：

> '#' who -H    //显示明细信息（标题）

#### timedatectl命令

矫正服务器时间。时区

ntp时间服务器。一个国际标准服务器

timedatectl set-ntp true  //服务器将和ntp服务器进行时间同步

> '#'timedatectl   //直接使用，可以查看目前的信息
>
> 同： timedatectl status

查看时区：

> '#' timedatectl list-timezones

 时区特别多，一页展示不下，按回车到下一页，按q跳出查看

给自己的系统设置时区

> '#' set-timezone 'Asia/Shanghai'

禁用ntp

> '#' timedatectl set-ntp false
>
> timedatectl set-time "2040-01-01 11:11:11"   // 只有禁用ntp之后才可以设置时间

开启ntp：

> '#' timedatectl set-ntp true

了解缩写：

> CST 当地时间，中部标准时间
>
> UTC 国际通用时间
>
> RTC 主板刻录时间，只有电池不拿出来，就一直在计时

几个小概念：

> 时区：  date命令可查看
>
> 系统时间：操作系统CentOS的时间，date命令可查看
>
> 硬件时钟RTC：real time clock : 主板上有电池供电的BIOS时间，hwclock -r 可查看
>
> NTP ：network time protocol  ，校准时间

#### clear命令

清屏作用。仅裸用。

仅仅是吧内容顶到上面，并没有删除记录

### 目录管理命令： ls  pwd   cd

#### ls命令，列侧护目录里的内容

语法： ls [参数选项] 目录名称；不带目录名称的话就展示当前目录

带参数的：

ls -l     : 显示文件或文件夹的详细信息

ls -a : 显示隐藏的目录，名字以点开头的文件或文件夹是隐藏型的

ls -al :既显示隐藏，由以详细信息的形式

ls -al 后所得的结果：

第i个数据项：

1. 权限，第一个字母为：
   - d 表示目录，-便是文件
2. 属主
3. 属组
4. 大小
5. 最后一次访问时间
6. 名称
   - 以点开头表示隐藏

#### pwd 命令

$pwd     //输出当前所在目录

带参数：pwd -P  和不带-P一模一样

#### cd命令

语法:cd  [相对路径或绝对路径]

- 相对路径 ： 相对当前目录而言；cd   home
- 绝对路径： 有根目录/开始的；cd /home

回退：cd ..

在/home目录中，存放这我们创建的所有一般用户

在任一用户目录里，存放着所有我们从虚拟机桌面“主文件夹”里看到的所有东西



### 目录管理命令mkdir  rmdir  rm

#### 创建目录，mkdir  目录名字

语法：mkdir 目录名字

> $cd /home/itcat/桌面
>
> $mkdir aaa          //裸用只能创造单级文件夹

带参数的：

> $mkdir -p bbb/ccc       // 可以创造多级文件夹

#### rmdir 文件夹名字

> $rmdir aaa      // 裸用只能删除空的文件夹

带参数的：

> rmdir -p bbb/ccc  //删除ccc,如果删完之后bbb是空的，bbb也一起删除

#### rm  [ ] 文件/目录

> $touch a.txt   // 创建一个文件
>
> $rm a.txt

裸用只能删文件

带参数的：   -r   删除目录，删除目录和目录里的所有内容

> $mkdir aaa
>
> $mkdir bbb/ccc
>
> $rm -r aaa
>
> $ rm -r bbb

### 目录管理命令cp   mv

#### cp命令

语法： cp [] 数据源  目的地    //文件复制

裸用只能拷贝文件，-r参数可以拷贝文件夹

动作一:

将aaa文件夹里的a.txt文件拷贝到ccc文件夹中

> 先进入桌面里面，就可以用相对路径操作了
>
> $cd /home/itcast/桌面
>
> $cp aaa/a.text ccc

动作二： 将aaa 中的所用内容拷贝到ccc文件夹中

> $cp aaa/* ccc
>
> //只是把aaa中所有文件给拷贝了，略过了aaa/bbb这个目录（略过的当然包括目录中的内容）
>
> $cp -t aaa/* ccc	

#### mv命令

mv [] 数据源 目的地        //改名（数据源和目的地都是文件名）；移动文件或文件夹

动作：将aaa文件夹中的所有内容全部剪切到ccc文件夹里面。

直接裸用就可以处理文件和文件夹

> $mv aaa/* ccc
>
> $mv ccc/a.txt aaa

具体来看：

mv 文件名  文件名：

将源文件改名为目标文件

mv 文件名 目录名

将文件移动到目标目录

mv 目录名 目录名

目标目录已经存在，将源目录移动到目标目录，布标目录不存在测改名

mv 目录名 文件名 出错

### 文件的基本属性--权限

权限：

drwxr-xr-x:一共有十位

- 第一位:
  - d :目录
  - ‘-’  ： 文件
  - l : 连接文档（快捷方式）
- 后九位：
  - r : 可读
  - w: 可写
  - x： 可执行
  - '-' : 没有当前权限
- 2-4位： 属主的权限，一般为可读可写可执行
- 5-7 位： 属组的权限
- 8-10位： 其他用户权限

### 更改文件的属主和属组chgrp chown---root 的动作

####  chgrp  ：更改文件的属组

change group

chgrp 新组 文件/文件夹

> su root
>
> 密码：
>
> ls -al
>
> ...
>
> chgrp root aaa
>
> ls -al
>
> ...

带参数的：

> charp -v itcast aaa    //-v 的作用仅仅是多了一条提示语句而已

#### chown :更改属主，或更改属组和属主

语法: chown 属主名  文件名        //更改属主

chown 【】 属主名 ：属组名  文件名  //更改属组和属主

选项参数

-R  : 处理指定目录以及其子目录下的所有文件及目录

> ls -al
>
> ...
>
> chown root aaa  //将aaa 目录属主改为root
>
> chown root : root bbb//将目录bbb的所有者和属组都更该	

带有参数：

> cd aaa
>
> ls -al
>
> chown -R root : root aaa

### 更改权限，chmod

chmod ：修改属主，属组和其他用户的权限

修改方式：

- 数字方式，
- 符号方式

数字方式：

- 读： r    4
- 写：w    2
- 执行   x   1
- 无权限  0

语法:

chmod [] 数字权限  文件或目录

比如可读可写可执行，权限数字就是：4+2+1 = 7；

不用担心同一个数字的二义性，设计者设计的数字已经巧妙应对了

常用权限：

-R ： 对目前目录下的所有档案与子目录进行相同的权限变更

 数字全权限就是rwx的数字总和。一个数字只针对一种类型用户的权限设置。

> '#' chmod -R 770 aaa

所有者可读可写可执行，同组的也是，但一般用户不可读不可写不可执行

符号权限：

语法：chmod 符号权限  文件或文件夹

-R 同效果

只是把符号权限代替数字权限

user :u 

group  :g

others  : a

all全部身份 ： o

设定符： 

'+'  加入权限

'-'   除去权限

=   设定权限

举例:

> chmod u = rwx, g = rx.o=r a.txt

> '#' chmod -R u=rwx,g=rx,o=r bbb
>
> '#' chmod a = rwx bbb //所有用户都rwx

需求：去掉其他用户的全部权限

> chmod -R o-rwx bbb

### 练习

需求：

一个公司的开发团队有三个用户，java，erlang，golang

有一个文集爱你目录tmp/work供他们开发，如何实现然让这三个用户都具备写的权限

>'#' useradd java 
>
>useradd erlang
>
>useradd golang
>
>groupadd dev-group
>
>gpasswd -a java dev-goup
>
>gpasswd -a erlang dev-group
>
>gpasswd -a golang dev-group
>
>//如何验证添加成功了呢
>
>grep 'dev-group' /etc/group
>
>...
>
>mkdir -p /tmp/work
>
>chgrp -R dev-group /tmp/work
>
>chmod -R 770 /tmp/work
>
>su java
>
>cd work
>
>mkdir aaa
>
>cd aaa
>
>cd ..
>
>ls -al

## 5.文件管理

### touch命令

作用：新建文件，如果文件不存在，就创建文件，如果存在，就修改时间属性

> touch a.txt

//批量创造多个文件

>  touch a{1..10} .txt
>
> //会创建a1.txt a2.txt 。。等等

查看时间属性：

> stat a.txt //查看文件的属性，其中包含时间属性

### vi 和 vim的介绍

vi文本编辑器：

- 只是编辑文件内容，不能对字体段落进行排版
- 不支持鼠标操作
- 没有菜单
- 只用命令

（功能非常强大）

vim:

是从vi发展出来的一个文本编辑器

diamante补全、编译以及错误跳转等方便编程的功能特别丰富，在程序员中广泛使用

vim是一个程序开发者的一项很好用的工具

vi/vim的三种模式	

在windows中双击打开一个文本文件后：

阅读---》编译-----》保存

对应的Linux系统：

用命令行打开后：

命令模式（只能看不能改）

编辑模式

末行模式（既输入保存指令）

命令模式：按i进入编辑模式；编辑模式按Esc退出编辑模式，进入命令模式

命令模式按：进入末行模式；末行模式按两下Esc进入命令模式

### vim的三种模式的切换

#### 打开和新建文件：

语法：vim 文件名

- 如果文件已经存在，会直接打开这个文件
- 如果文件不存在，则打开一个临时文件，在保存退出后，就会新建一个文件

打开后，就是命令模式，不能编辑，只能阅读

命令模式中安i进入编辑模式

编辑完成后安Esc重返命令模式，安： 进入末行模式，然后：

- q 没走任何操作，按q可退出
- q!  编辑过了，但想放弃编辑内容并退出
- wq 正常保存并退出
- wq! 强行保存并退出，只针对与root用户或文件所有人

> $vim a.t
>
> ~nihao
>
> ~
>
> ~
>
> ~
>
> :wq
>
> $

### 文件查看，cat ; less 

文件查看： 

- cat 文件名            查看小文件内容
- less -N 文件名       分屏显示大文件内容
- head -n  文件名      查看文件的前一部分
- tail -n 文件名        查看文件的前一部分内容
- grep 关键字  文件名     根据关键字搜索文本文件内容

#### cat命令：

> $ cat small.txt
>
> ...
>
> ...
>
> ...
>
> $cat -n small.txt
>
> 1.,,,
>
> 2.,,,
>
> 3,.,,,
>
> //-n 就是表示显示内容有行号
>
> //cat只能查看小型文件。对于大型文件只能显示部分内容

less命令可以查看大型的文件，参数-N用来显示行号

文件在一个屏幕中当然只能显示部分，用上下左右键可以查看其他

对于长文件，阅读到一般不想阅读，想跳出直接进入命令输入行，按q即可

### 文件查看tail  和head命令

tail命令：

> tail big.txt   //默认显示最后十行
>
> tail -3 big.txt  //  显示最后三行数据
>
> tail -f big.txt //动态显示最后十行的文件，直到按Ctrl+ c退出动态查看模式，进入命令行输入
>
> tail -4f big.txt //动态显示后4行
>
> tail -n +2 big.txt //从文件第二行开始，往下显示全部
>
> tail -c 44 big.txt   // 显示最后44个字符

head命令，和tail命令是类似的，功能反过来

### 文件查看，grep

grep命令

查找： 在Windows中，打开一个文本文件，点击Ctrl+f，可以进行查找动作。

查看任务进程：在windows中，在任务管理器中可以查看任务管理进程

语法：

> grep [] 关键字 文件    //根据关键词，搜索文本文件的内容

演示：

> grep 日 small.txt
>
> .....//把含有这个关键字的一行数据显示出来
>
> grep -n 日 small.txt
>
> 1,.... //把行号也显示出来
>
> grep -i a small.txt
>
> ...
>
> ...//忽略大小写查找
>
> grep -v 日 small.txt 
>
> ...
>
> ...
>
> ...//忽略含有关键字的那一行数据，其他的全展示

grep在显示进程命令ps中也能加入去发挥筛选进程的功能：

> ps -ef |grep sshd
>
> //显示带有关键词sshd的进程
>
> ps -ef |grep sshd | grep -v "grep" 
>
> //显示带有关键词sshd的进程并忽略带有grep的进程（grep命令本进程）
>
> ps -ef |grep -c sshd 
>
> 4   //求带有sshd关键字进程的个数

###  vim定位行

语法：

> vim 文件名 +行数  
>
> //查看文件并定位到具体行数

演示：

> ls -al    // 展示当前文件夹中的文件（夹）
>
> vim small.txt +5
>
> //打开文件并光标初始在第五行

### vim的异常处理

如果vim异常退出，在磁盘上可能会保存有交换文件

对于修改文件a.txt,修改过程本文件没有改动，而是生成一个新的文件：a.txt.swp ，保存的时候将a.txt.swp内容写回到原文件中。

a.txt.swp 就是交换文件

当发现有交换文件后，应该第一时间将他删除，之后才可以在编辑文件

### echo命令

语法

>  echo 字符串     //展示文本，就跟java中 输入语句一样
>
> echo 字符串 > 文件名     //将字符串写进文件中（覆盖文件中的内容）
>
> echo 字符串 >>文件名    //将字符串写到文件中(不覆盖文件中的内容)
>
> cat  不存在的目录 &>> 文件名   //将命令的失败结果追击到文件的后面

字符串用双引号包裹，仅仅是利于代码更利于阅读

>cat a.txt &>>small.txt
>
>cat a.txt 是一个完整语句，因为a.txt不存在，故应该有报错信息，&>>small.txt 表示将报错信息输入到small.txt 文件中

### awk命令

AWK是一种处理文本文件的语言，是一个强大的文本分析工具

语法：

> awk [参数] 'awk语法' 文件

例子：

需求一：搜索含有zhang和li的数据行

> cat a.txt | awk '/**zhang|li**/'    粗写的或两边不能有空格，会有理解错误。表示：展示a.txt文件，展示的内容是：带有'zhang'或者'li'的数据行

需求二：每一行按照空格切割，在输出切割后的每一小串

> 参数：-F ','      //使用指定字符进行分割
>
> $ + 数字           //获取第几段内容，从1开始
>
> $0                //获取当前行的内容

> cat a.txt |awk -F  ' '    '{print $1,$2,$3,$4}'

### awk语法： 切割后按照指定方式展示

需求三：

每一行按照空格切割，在输出切割后的每一个小串，多个小串中间以"===" 间隔

> OFS = "字符"    含义:  向外输出时的按照指定字符串进行分割

> cat a.txt |awk -F " "    "{OFS = "                         ==="}{print $1,$2,$3,$4}"

需求四：

每一行按照空格切割，在输出切割后的每一个小串，多个小串中间以"\t"间隔。

>  cat a.txt |awk -F ' '  '{OFS="\t"}{print $1,$2,$3,$4}'

###  awk语法，toupper ,tolower ,length 

需求五：

每一行按照空格切割，将第一段内容转成大写并显示

函数名：

toupper（） 字符转成大写

tolower（）字符转成小写

length（） 返回字符长度

> cat a.txt |awk -F ' '  '{print toupper($1)}'
>
> cat a.txt |awk -F ' '  '{print length($1)}'
>
> cat a.txt | awk -F ' '  '{print tolower($1)}'

### awk 语法：计算

需求：

每一行按照空格切割，计算第四列的总分并显示

格式：

BEGIN{}     执行前执行的语句

{}                对每一行的操作语句

END{}        执行结束后执行的语句

> cat a.txt |awk -F '  '    'BEGIN{}{totel = totel +$4}END{print totel}'

需求：

每一行按照空格切割，计算第四列的总分，显示总分，总人数

> cat a.txt |awk -F '  '    'BEGIN{}{totel = totel +$4}END{print totel,NR}'    NR表示当前处理的是第几行

需求三：

每一行按照空格切割，计算第四列的总分，显示总分，总人数，平均分

> cat a.txt |awk -F '  '    'BEGIN{}{totel = totel +$4}END{print totel,NR,totel/NR}'    NR表示当前处理的是第几行.totel /NR,就是平均分

### 软连接

相当于微软的快捷方式

在Linux中，文件名和文件内容存放在两个位置

语法：

> ln -s 目标文件路径  快捷方式路径

> ln -s aaa/bbb/ccc/ddd/eee/a.txt  a.txt
>
> //创建一个快捷方式，指向目标文件，放在当前文件目录中a.txt 文件中

## 6.压缩命令

### find命令

语法：

find [参数选项] <自定目录> <指定条件> <指定内容>

在指定目录下查找文件

参数选项：

- -name   filename      //查找名为filename的文件
- -ctime  -n或+n          //按时间来查找文件，-n指n填以内，+n是指n天以前操作过的文件

> find . -name "*.txt"
>
> find . -ctime -1   
>
> find / -name "*.txt"    //全局查找

### 备份压缩

.rar格式在Linux下是无法识别的

.zip格式两个系统都可以识别

gzip命令

语法：gzip [参数选项] [文件]        压缩文件

> cd aaa
>
> gzip a.txt
>
> //源文件a.txt消失，a.txt.gz文件多出
>
> gzip *           
>
> //压缩当前目录下的所有文件，已经是压缩包文件的不会参与再次压缩
>
> gzip -dv  *          //解压文件，解压当前目录所有已压缩文件，并显示过程解压信息
>
> gzip -d *           //解压当前目录所有文件，不显示信息

#### gunzip 命令

语法： 

gunzip [参数] [文件]        解压文件

### tar命令

语法：

tar [必要参数] [选择参数] [文件或文件夹]       打包、压缩和解压文件 或文件夹

注意：

tar本身不具备压缩功能，他是调用压缩功能实现的

> 参数选项：
>
> -c ： 建立新的压缩文件
>
> -v : 显示指令执行过程
>
> -f ：<备份文件> 指定压缩文件
>
> -z：通过gzip指令处理压缩文件
>
> -t: 列出压缩文件中的内容
>
> -x : 表示解压

> cd aaa
>
> tar -cvf a.tar a.txt
>
> //仅仅是打包文件，.tar 文件并没用压缩。c指建立新的文件a.tar ,v指显示执行执行过程，f指定压缩哪个文件
>
> tar -zcvf b.gz b.txt
>
> // 调用gzip的功能进行压缩。

压缩整个文件夹：

> tar -zcvf aaa.gz aaa

查看压缩文件夹里的内容：

> tar -ztvf aaa.gz
>
> ...

解压：

> rm -r -f aaa    // 先删除掉之前的aaa文件夹
>
> tar -zxvf aaa.gz
>
> ...
>
> 屏幕上就又出现了aaa文件夹
>
>  cd aaa
>
> ls -al

tar命令：

tar -cvf 打包文件名 文件名       //打包文件并指定打包之后的文件名，仅打包不压缩

tar -zcvf 压缩文件名 文件名/文件夹名        //压缩文件或者文件夹并指定压缩文件名

tar -ztvf 压缩文件名    //查看压缩文件中有哪些文件

tar  -zxvf  压缩文件名      //解压

### 压缩命令 zip  unzip 

zip命令

语法：

> zip [必要参数] [原则参数] [文件]      //压缩

参数选项：

-q :不显示指令执行过程

-r : 递归处理，将指定目录下的所有文件和子目录一并处理

> cd aaa
>
> ls -al
>
> cd ..
>
> zip -q -r aaa.zip aaa
>
> ls -al

zip 命令：

zip -q -r 压缩文件名 文件/文件夹    //压缩

#### unzip

语法:

> unzip [必要参数] [选择参数] [文件]   //解压

注意：尽可以解压.zip扩展文件

参数选项：

-l 显示压缩文件内所有包含的文件

-d <目录>    指定文件解压后要存储的目录

> unzip -l aaa.zip     //查看aaa.zip 中都有什么
>
> unzip -d bbb aaa.zip 
>
> //将aaa.zip解压，并把解压的结果放入bbb目录中

unzip 命令：

unzip -l 压缩文件名   //查看这个压缩文件中有什么内容

unzip -d 指定文件夹  压缩文件       //解压

### 压缩命令  bzip2      bunzip2

语法： bzip2 [参数选项] 文件       //压缩

注意：使用新的压缩算法，压缩后的文件比原来的药效，但是花费的时间变长

如果没有加上任何参数，bzip2压缩完文件后会产生.bz2的压缩文件，并删除源文件

> cd aaa
>
> bzip2 a.txt

#### bunzip2   

语法：bunzip2 [参数选项] 文件       //解压

参数选项：

-v   解压缩文件时，显示详细的信息。

> bunzip2  -v a.txt.bz2

## 7.网络与磁盘管理

### 网络管理，ifconfig 命令

ifconfig命令

语法： ifconfig [参数选项]      //显示或配置网络设备的命令，和Windows中的ipconfig类似

> ifconfig  
>
> //直接回车，显示各个网卡的ip等信息。

关闭和打开网卡：

> su root 
>
> 密码:
>
> #' ifconfig ens37 down 
>
> #' ifconfig
>
> ...
>
> #' ifconfig  ens37 up
>
> #' ifconfig
>
> ...

修改网卡的ip

> #' ifconfig ens37 192.168.23.199
>
> #‘ ifconfig

修改ip和子网掩码

> #’ ifconfig ens37 192.168.23.199 netmask 255.255.255.0

ifconfig 命令：

ifconfig    //显示激活的网卡信息

ifconfig  ens37 down    // 关闭网卡

ifconfig  ens37 up   //启动网卡

ifconfig ens37 192.168.23.199 配置ip地址

ifconfig ens37 192.168.23.133 netmask 255.255.255.0   // 配置ip地址和子网掩码

### 网络管理，ping，，netstat

ping  命令

语法：

ping [参数选项]         //检测是够与主机联通，和Windows中的ping相似

参数选项：

-c  <完成的次数>      // 设置完成要求回应的次数

> ping www.baidu.com 
>
> //这是一个动态试探的过程，如果不想测试了，就按Ctrl+c退出ping模式
>
> ping -c 2 www.baidu.com 
>
> //静态的，值试探两次就结束

#### netstat命令

语法：netstat [参数选项]    //显示网络状态

参数选项：

-a   :显示所有连线中的Socket

-i ： 显示网卡列表

> netstat -a 
>
> 弹出Linux系统中所有的连接情况
>
> netstat -i    //显示网卡列表

### 磁盘管理  lsblk  和 df 

lsblk 命令：

语法：

lsblk [参数选项]    //累出硬盘的使用情况

理解为 ： list block 的英文缩写

参数选项

-f    显示系统信息

> lsblk 
>
> //展示硬盘的使用情况
>
> RM  ： 是否为可移动设备
>
> lsblk -f    
>
> //显示UUID编号。

#### df 命令

语法：

df [参数选项]    //显示母亲在Linux系统上，硬盘的使用情况。和lsblk有点类似

参数选项：

--total  显示所有信息

-h   换算成KB ,MB ,GB 等形式进行展示(方便阅读)

> df   
>
> //显示各个储存块的已用 可用等情况，单位为KB
>
> df -h
>
> //自动将KB 单位转换为MB 、GB等用以便于观察

df命令：

df    显示整个硬盘的使用情况

df 文件夹  显示文件夹使用情况

df --total   显示所有的信息

df -h   将结果自动变成KB MB GB形式，利于阅读

### 磁盘管理： mount

mount命令： 

语法： mount [参数选项] 目录 用于挂载Linux系统以外的设备

挂载：U盘，出入Linux系统的电脑，不想Windows那么方便，需要手动建立一个空文件夹，将这个空文件夹和U盘进行关联。这样这个文件夹称作"挂载点",这个过程称作"挂载"

卸载：接触挂载点和U盘的关系的过程

mount命令：

注意：挂载点目录需要一下几点要求：

- 目录实现存在，可以使用mkdir命令新建目录
- 挂载点目录不可被其他进程使用到
- 挂载点下原有文件将被隐藏

移动设备：U盘，CD，DVD .虚拟机中就提供了一个，

：

- 点击“虚拟机”,在左上角
- 点击“设置”
- 点击CD/DVD。这个就是虚拟光驱

> ru root 
>
> 密码：
>
> mkdir aaa
>
> mount -t auto /dev/cdrom  aaa
>
> 写保护，将以只读方式挂载
>
> cd aaa 
>
> ls -al
>
> cd ..
>
> umount aaa    // 卸载aaa 文件夹
>
> cd aaa
>
> ls -al               //显示为空

mkdir 文件夹         //创建文件夹，也就是创建一个挂载点

mount -t auto  /dev/cdrom 文件夹   //开始挂载

umount 文件夹        //卸载

### yum的基本使用

在Linux中，如果我们想要查找。安装，下载或者卸载另外的软件，就需要通过yum来进行操作

全称：Yellow dog Updater ,Modified

小黄狗

yum概念：

yum的好处： 从yum源下载的软件包都是自动完成：解决软件的依赖问题和安装

实例：安装tree软件，用来将文件目录以树状的形式形象展示

> yum -y install tree  
>
> //-y指遇到任何询问都选择yes
>
> 提示权限不够，只能在管理员权限下才可以下载软件
>
> ru root 
>
> 密码：
>
> yum -y install tree
>
> 显示安装完成。
>
> 直接使用tree命令：
>
> tree
>
> ...

卸载tree

> yum remove tree 

查找软件，查找以tom开头的软件

> yum list tom*

yum 命令：

yum -y install tree    安装tree

tree             执行tree，展示当前目录结构

yum remove tree        卸载tree

yum list tom*             找出以tom为开头的软件名称

### yum，更改yum源

默认的yum源是国外的，速度超级慢

应该将yum源更改为国内的，比如阿里的，搜狐的

> yum -y install wget   
>
> //首先下载一个下载工具
>
> 、、应该将原本yum的配置进行备份
>
> cd /etc/yum.repos.d/
>
> mv CentOS-Base.repo   CentOS-Base.repo.back
>
> //..通过下载工具下载阿里的yum源
>
> wget -O CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
>
> cat CentOS-Base.repo
>
> //查看配置文件
>
> yum clean all       //清理之前的缓存文件
>
> yum makecache  //给现在的yum源配置新的缓存文件。等在三到五分钟

查找Tomcat软件

> yum search tomcat
>
> ...

###  yum 和rpm工具的区别

rpm：

在最初，专门用来管理Linux各项套件程序

区别：

rpm只能安装已经下载到本地机器上的rpm包

yum能在线下载并安装rpm包，能更新系统，且还能自动处理包与包之间的依赖问题。这个是rpm工具不具备的

## 8.shell

### 初始shell

在计算机科学中，shell就是一个命令解释器

shell是位于操作系统和应用程序之间，是他们两者的只要接口

shell负责把应用程序的输入命令信息解释给操作系统，将操作系统指令处理后的结果解释给应用程序

应用程序-》shell-》操作系统-》硬件

在Windows中也有shell，cmd.exe 就是windows中的shell

Linux中有很多的shell，

现在默认使用的shell是：

bash

> $ echo $SHELL    // 展示shell，$SHELL是一个变量
>
> /bin/bash

#### shell的使用方式

- 手工方式:
  - 手工敲击键盘，直接输入命令，按enter后执行命令，显示命令执行的结果
  - 重点：逐行执行输入命令，逐行进行确认执行
- 脚本方式：
  - 我们把手工执行的命令写到一个文件中，然后运行这个问阿金，达到执行命令的效果
  - 这个文件我们就叫做脚本文件

### shell 第一个脚本文件

编写第一个shell，

- 新建一个文件，后缀名是sh

- 书写内容

  - > #! /bin/bash     //指定使用的shell
    >
    > #’ 这是临时shell脚本    // 注释
    >
    > echo 'nihao'
    >
    > echo 'itcast'

- 执行

> touch a.sh    //新建文件
>
> vim a.sh 
>
> //再按i进入插入模式（编写状态）
>
> //编写内容就是脚本内容
>
> //再按esc退出
>
> //     ：wq!         保存 

执行：

> //因为这个.sh文件默认root和一般用户都是可读可写但不可执行。所以没办法直接运行a.sh文件
>
> //先修改文件的权限
>
> chmod 777 a.sh
>
> ./a.sh          //会执行里面的脚本代码
>
> itcast
>
> nihao

### shell注释

- 单行注释：

  - #

- 多行注释

  - >  :<<字符 
    >
    > ​    注释内容
    >
    >    同样字符（一般用！）

### shell变量

- 定义变量
  - 普通变量的定义
  - 命令变量的定义
- 使用变量
- 只读变量
- 删除变量



-  普通变量
  - 变量名 = 变量值
    - 变量值必须是一个整体，中间没有特殊字符
  - 变量名 = '变量值'
    - 单引号中的内容，原样赋值
  - 变量名 = "变量值"
    - 如果双引号里面有其他变量，会把变量的结果进行拼接，然后复制

> ls -al 
>
> vim a.sh
>
> 按i 
>
> > mumber = 10
> >
> > echo $number       //$代表使用变量
>
> //运行：
>
> 两种方式：./a.sh       bash a.sh
>
> bash a.sh
>
> 10
>
> vim a.sh
>
> > mumber = 10 10
> >
> > //报错
> >
> > a = '10'
> >
> > a = '$number'    // 打印出￥number
> >
> > b = "$number" //打印10

习惯：数字不加引号，其他默认双引号

- 命令变量的定义:
  - 方式一： 变量名 = \`命令`
  - 方式二 ： 变量名 = $(命令)

`将命令执行的结果赋值给变量`

第二种格式可读性更高

> vim a.sh
>
> > c = \`date`
> >
> > echo $c 
>
> bash a.sh
>
> vim a.sh 
>
> > d = $(date)
> >
> > echo $d

#### 使用变量

- 方式一：  
  - $变量名    非标准写法，图省事
- 方式二 ：
  - "$变量名"   非标准写法，图省事
- 方式三：
  - ${变量名}  
- 方式四：
  - "${变量名}"     标准使用方式

> vim a.sh 
>
> > result  = "现在的时间是${d}"
> >
> > echo "${result}"
>
> bash a.sh

#### 只读变量

- 在前面加上readonly 关键字。任何时候都可以加

#### 删除变量

- unset 变量名

> vim a.sh 
>
> > //按i 进入插入编辑模式
> >
> > result = "现在时间是${d}"
> >
> > echo "${result}"
> >
> > readonly result
> >
> > unset result

### shell 语法：数组

- 定义数组   数组名 = (值1 值2 值3 。。)
- 给数组元素赋值   数组名[索引] = 值 
- 获取元素    ${数组名[下标]}
- 获取长度      ${#数据名[*]}    或   ${#数据名[@]}

>  vim array.sh 
>
> > arr = (a b c d e f)
> >
> > arr[0] = A
> >
> > echo ${arr[0]}
> >
> > echo ${arr[1]}
> >
> > echo "数据的长度￥{#arr[@]}"
> >
> > echo "数据的长度￥{#arr[*]}"
>
> 

### shell语法：运算符

shell算术运算符

- +
- -
- \*           * 在shell中有特殊的用法，运算中用 \\*  代表乘号
- /
- %
- =
- ++
- --

注意点：

1. 原生的bash不支持简单的数学运算，可以通过其他命令实现： expr
2. 表达式和运算符之间要有空格
3. 完整的表达式要被反引号包含

举例：\`expr 2 + 2`

>operator.sh
>
>vim operator.sh
>
>> num1 = \`expr 2 + 2`
>>
>> echo "整数2+2的结果是$num1"
>>
>> num2  = \`expr 2 - 2`
>>
>> echo "相减的结果是￥num2"
>>
>> num3 = \`expr 2 \\* 2`
>>
>> cheo "jieguo  $num3"
>>
>> 变量相加
>>
>> a = 10
>>
>> b = 20 
>>
>> num4 = \`expr $a + $b` 
>>
>> echo  "变量相加的结果hi $num4"
>>
>> 赋值
>>
>> c  =30 
>>
>> num5 = "${c}"
>>
>> #‘ 自增
>>
>> e = 1
>>
>> ((e++))
>>
>> echo "变量e为1，自增后，结果为$e"
>
>

### shell语法：字符串运算符

字符串运算符：

- =  检测两个字符串是否相等,相等返回true    [$a = $b]
- !=   检测两个字符串是否不相等，不相等返回true，   [$a != $b]
- -z   检测字符串长度是够为0 ，为零返回true        [-z $a]
- -n   检测字符串长度是否为0，不为零返回true          [-n  "$a"]
- $    检测字符串是否为空，不为空返回true。        [$a]

注意:

1. 条件表达式必须写在中括号之中。
2. 方括号和里面的内容不能挨着
