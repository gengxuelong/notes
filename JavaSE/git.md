# git

## 1.git的基本操作

### git本地仓库基本工作流程

git基本流程：

- 本地仓库
- 远程仓库

工作目录（working tree)：代码存放的位置，代码经常发生变动，需要对其进行版本控制

本地历史仓库(repository)：存放了不同版本的代码

​    按说应该时不时地把工作目录中的东西存放在本地历史仓库，可是不能直接转移，有一个过渡区：暂存区

暂存区（index):代码提交到仓库之前的临时存储空间

工作目录---》 暂存区---》本地历史仓库

### git常用命令

git init :初始化，创建git仓库

git  status 查看git状态（问价是够进行了添加、提交操作）

git add  添加，将指定违建添加到暂存区

git commit 提交，将暂存区文件提交到历史仓库

git log  查看日志，（git提交的历史日志）

操作步骤：

1. 创建一个新的文件夹：my_project。这是一个很普通的文件夹。进入这个文件夹，打开git bash命令行。输入命令：git init     完成初始化。多出了隐藏的.git文件
2. 新建一个test.txt文件，暂不执行添加操作）
3. 使用git status命令查看状态；发现红色内容，红色内容就是你没有进行添加操作的文件，被称为：untracked files
4. 使用add命令 并查看状态：发现一个绿色的文件，绿色的文件表示暂存区中放置的文件，称为：Changes to be committed(变化正正准备被提交)。和stage files(已放置的文件)
5. 使用commit命令，将文件提交到本地历史仓库。commit命令不需要指出要提交哪个文件了，它只会把暂存区中的所有暂存文件提交到本地历史仓库。但必须加上-m的参数和一个字符串信息，用作注释。（这个必须）
6. 使用log命令，查看日志
7. 修改text.txt文件
8. 添加并提交，查看日志。查看日志发现，存在两个不同的索引信息，分别指向不同的版本。这两个唯一的索引表示用作以后的版本切换

###  git版本管理

#### 历史版本切换

最初项目有一个bug，可是经过一个星期的修复，变成了五个bug。。。我们需要切换到最初的版本

- 准备动作：

  1. 查看my_project的log日志
     - git reflog命令，比git log命令更加好：版本标识号取缩写；可显示所有分支的版本
  2. 新增一次新的修改记录，仅有两个版本看的不太清楚

-  切换版本：

  - git reset --hard 版本的唯一索引值（有缩写即可）

  - > $ git reset --hard 03dd774 
    >
    > HEAD is now at 03dd774 ..(这个版本的注释)
    >
    > //检查后咋切换一个版本
    >
    > git reset --hard  33f227a
    >
    > HEAD is now at 33f227a ...

### git版本管理-分支管理

分支不好理解，但是分身好理解

两个分身有自己时间线，并行工作，各不打扰，而且最后多条时间线可以合并。

分支：有每次提交的代码，传承的一条时间线

分支的使用场景:

- 周期较长的模块开发
- 尝试性的模块开发

使用分支，意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线

### 分支的工作流程

分支: 有每次提交的代码，串成的一条时间线

Master分支，当没有开新分支的时候，默认只有一条分支：Master主分支。

Master其实还是一个指针；提交了第一个版本，Master就指向第一个版本，体交第二个版本master就指向第二个版本...Master所指向的就是提交的代码版本

分支当中其实还是存在一个指针的：HEAD：

指向当前所使用的分支。既，HEAD 默认指向Master指针

 从第三个版本开始，我们想要开发一个高难度功能，不知道能不能实现。那就新开一个分支，Dev,此时Dev指向版本三，将HEAD 指向Dev，进行迭代，开发出来后，如何将新分支合并到主分支中呢：先将Master指向Dev中的最新版本，再将HEA指向Master，在把Dev分支（指针）删除掉就好了。

总的流程就是：

- 创建新分支，
- 切换分支
- 合并分支
- 删除分支

### 分支管理操作

创建于切换：

- 创建分支:git branch 分支名
- 切换分支：git checkout 分支名

>$ git branch xiaoming	
>
>$git status //可以清楚看到当前在哪个分支，其实每一个命令上面的系统文字都用（）告诉可当前分支
>
>on branch Master
>
>nothing to commit working tree clean
>
>$git branch// 直接回车，查看所有分支名
>
>master
>
>xiaoming
>
>$git checkout xiaoming
>
>Switched to branch 'xiaoming'
>
>$git add test2.txt 
>
>$git commit -m 'commit test2.txt'
>
>...
>
>$git checkout master
>
>Switched to branch 'master'
>
>$ls   //查看当前分支内都有什么文件.此时本地工作目录中也是只有text.txt(既类同版本切换)
>
>text.txt
>
>$git checkout xiaoming 
>
>Switched to branch 'xiaoming'
>
>$ls 
>
>text.txt   text2.txt

管理：

创建和切换：

- 创建分支：git branch 分支名
- 切换分支：git checkout 分支名

查看文件命令：ls

查看分支列表：git branch

> 不同分支之间的关系是平行的关系，不会互相影响

### 合并分支和删除分支

- 合并分支
  - ​	合并分支：git merge 分支名
  - 一般是将其他分支合并到主分支上，理论上也允许将主分支合并到一般分支

- 删除分支
  - git branch -d 分支名

> $git checkout master
>
> Switched to branch 'master'
>
> git merge xiaoming 
>
> ...
>
> $git branch -d xiaoming //删除分支
>
> Deleted branch xiaoming 
>
> $git branch 
>
> master
>
> $

本地历史仓库和工作目录之间也有作用:

checkout 切换分支，在本地历史仓库切换一下分支，工作目录的内容也随之改变

还有就是版本切换



> Git鼓励大量使用分支：
> 查看分支：git branch
> 创建分支：git branch <name>
> 切换分支：git checkout <name>
> 创建+切换分支：git checkout -b <name>
> 合并某分支到当前分支：git merge <name>
> 删除分支：git branch -d <name>

### 远程仓库的工作流程

远程仓库，就是一个代码托管平台

本地历史仓库A ----push推送---》远程仓库----clone克隆----》本地历史仓库B

本地历史仓库B----push推送--》远程仓库----pull拉取（更新内容）---》本地历史仓库A

### 远程仓库凭条介绍

GitHub，码云gitee

### 远程仓库创建-SSH公钥配置

操作情况：

- 情况一：现有本地仓库，远程仓库是空的
  - 步骤：
    1. 创建远程仓库，
    2. 将项目从本地仓库推送到远程仓库
- 情况二： 现有远程仓库，本地仓库为空的

注意：

推送代码之前，需要配置SSH公钥（SSH是一种协议）

生成SSH公钥的步骤：

1. 设置git账户
2. 生成SSH公钥
3. 设置账户公钥
4. 公钥测试

 一。设置git账户

命令：

- git config user.name     查看git账户名字
- git config user.email    查看git邮箱
- git config  --global user.name "账户名"    //设置全局账户名和邮箱；表示这台机器上所有的git仓库都会使用这个配置
- git config  --global user.email  '邮箱‘
- cd ~ /.ssh    //查看是否生成过SSH公钥

结果如果是：No such  file or directory ,表示没有生成过SSH

生成SSH 公钥的命令：

> $ ssh-keygen -t rsa -C "3349495429@qq.com"  // ssh-keygen 是连着的
>
> ....
>
> Enter file in witch to sava the key (/c/Users/apple/.ssh/id_rsa)：  //会卡在这，同意默认装在C盘，就敲回车，接着每卡一下，敲一次回车 
>
> $cat ~/.ssh/id_rsa.pub  // 查看生成好的公钥
>
> ..........................
>
> ..........................(这就是我们的SSH 公钥)
>
> //接着我们将生成好的公钥配置当我们的远程仓库中

远程配置公钥步骤:

1. 进入码云，点击右上角，找到设置
2. 点击设置，看到SSH公钥 
3. 点击SSH公钥
4. 将我们在git生成的公钥复制到这，正再点击确定就可以了

公钥测试：

> $ ssh -T git@gitee.com
>
> 询问你是否真的要连接：输入yes
>
> 。。。successfully（绿色）。。。
>
> $//表示配置成功

### 本地代码推送到远程仓库

推送到远程仓库

- 步骤：

1. 为远程仓库的URL（网址）自定义仓库名称
2. 推送

- 命令：
  - git remote add 远程名称 远程仓库URL      //自定义仓库名称
  - git push -u 仓库名称 分支名   //推送，同时明确要提交哪一个分支的代码

>$git remote add origin（任意起名） URL(去gitee网上赋值，HTTPS 和 SSH都行)               // 本命令是为远程仓库起一个名称
>
>$git push -u origin master
>
>...
>
>...
>
>$ 

于是我就用`git push -f origin master`强制push就成功了。（注意：大家千万不要随便用-f的操作，因为f意味着强制push，会覆盖掉远程的所有代码！）



#### 问题1：

fatal: refusing to merge unrelated histories

解决：

```
$git pull origin master --allow-unrelated-histories
```

#### 问题2：

Updates were rejected because the tip of your current branch is behind

描述：出现这个错误的原因是git本地仓库的当前版本低于远程仓库的版本(大白话就是：你在[github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020)上进行的修改没有同步到本地git仓库中)。

解决：

git pull origin master

#### 问题3

 Your local changes to the following files would be overwritten by merge

解释：

这句代码的意思是以本地进行的修改会被覆盖，也就是说你本地进行的修改不会生效。一般是使用了git pull相关的命令同步远程仓库到本地引起的，而本地的修改无法上传到远程仓库，导致两者都不能兼备

解决：

git stash  # 备份当前的工作区的内容，让工作区保证和上次提交的内容一致。同时，将当前的工作区内容保存到Git栈中
git commit
git stash pop  # 从Git栈中读取最近一次保存的内容，恢复工作区的相关内容
在终端下依次输入上述代码就可以让服务器上的代码更新到了本地，而且你本地修改的代码也没有被覆盖
之后使用add，commit，push命令即可更新本地代码到服务器

#### 问题4：

昨天还可以git push代码到远程仓库，今天git  push时报了这个错：fatal: unable to access 'https://github.com/.......': OpenSSL SSL_read: Connection was reset, errno 10054

分析与解决：

一般是这是因为服务器的SSL证书没有经过第三方机构的签署，所以才报错

参考网上解决办法：解除ssl验证后，再次git即可

git config --global http.sslVerify "false"

#### 问题5

克隆时： error: RPC failed; curl 28 OpenSSL SSL_read: Connection was reset, errno 10054
fatal: expected flush after ref listing

解决方法:

```shell
git config http.sslVerify "false"
```

### 远程仓库操作-克隆，拉取

- 操作情况：现有远程仓库，本地仓库为空

- 步骤;
  1. 将远程草哭的代码，克隆到本地仓库
     - 克隆命令：git clone 仓库地址
  2. 创建新文件，添加并提交到本地仓库
  3. 推送到远程仓库（只有将修改的文件提交到历史仓库之后太刻意推送至远程仓库
     - 推送的命令：git push -u 远程仓库名 分支名
  4. 项目拉取更新
     - 拉取命令：git pull 远程仓库名  分支名

 >$git clone URL 
 >
 >....// 此时我们所在的目录会有一个新的文件，这个文件包括了仓库的所有内容。所以不必事先为远程仓库建立本地文件作为工作目录
 >
 >$git add tet3.txt 
 >
 >$git commit -m ''
 >
 >$git push -u origin master
 >
 >//在回到原来的my_project 文件。
 >
 >这里的文件只有text.txt and text2.txt两个文件。还没有新文件夹提交的text3.txt
 >
 >$git pull origin master
 >
 >...
 >
 >此时test3.txt 被拉取到工作目录中
 >
 >

​	

### 代码冲突

两个程序员拉取了（pull）同一个文件，并分别对文件进行了修改。然后分别进行了push推送。造成了两个文件的内容冲突。

实际流程：

两个程序员同用一个远程仓库，来开发同一个项目

A程序员将test文件修改一下，并且push到远程仓库。而B程序员，并没有在A上传后最新版本后去拉取最新版本的代码。而是在自己原有的版本上也去修改text文件（与A修改的不同） ，他在push自己的代码，就造成了代码冲突

出现代码冲突后push的时候就会报错，拒接push

如何解决代码冲突：

进行最新版代码拉取：

> $git pull origin master
>
> 之后会发现冲突的文件会有感叹号
>
> $cat test.txt   // 查看冲突文件中那些部分不一样	
>
> ...左尖括号和右尖括号之间的内容就是代码冲突的任荣。下面显示的是本机代码，上面显示的远程的代码。将本机代码修改成远程代码冲突就消除了
>
> //修改之后再提交，就没事了
>
> $git add text.txt
>
> $git commit -m ''
>
> $git push -u origin master

所以为了应对代码冲突，执行提交之前一定要进行一个拉取动作，之后所有有冲突的文件都会显示出感叹号，并且内部会保留您的和远程的两方面的信息。你自己决定留那些，删哪些，不论怎么修改，只要拉取过，就会提交成功

## 2.IDEA 集成 git

### 创建本地仓库-提交代码

1. file  --> version control  --> git 

   进入git设置后，在git目录栏中找到git的安装目录中的git.exe；

   再点击test用来验证git是否配置好了

2. 配置好后的使用步骤

   - 点击VCS ,,点击import into version control，，点击create git repository
   - 控制目录选择：选择下面带有.idea的那一层目录。
   - 此时多出了两个按钮，一个蓝的的下降符号，一个绿色的对钩符号。下降是pull操作，对钩是commit操作
   - 点击对钩   提交：
     - 勾选要提交的文件，勾选的动作就是add，然后输入注释信息，然后点击commit提交

   - 观看提交记录:点击下方的version control。

### 版本切换

  有两种方式：

- 方式一：reset
  - 进入version control的log中，右击任意版本，点击reset ..，--》点击reset;;
  - 进入该版本后，此版本之后的新版本都直接销毁（无奈，但没办法）

- revert commit

  - 同样的进入log后，点击之前的版本，右键，点击revert commit，此时当前版本和欲进入版本之间不一样的文件都会爆红色。

  - 出现的状况可以理解为代码冲突，只要最后取舍中选择与进入版本的代码就好了

  - 点击merge

  -  初始化状态就是与进入版本为结果端，当前版本为参看端，只要什么也不该，把叉号就点一下，再点击APply就好了

  - 进入提交界面，既revert这个行为会作为一个版本进入历史仓库

  - 内容都自动弄好了，点击commit即可

    

### idea中对远程仓库的操作

- 本地推送到远程
  - 点击VCS ，点击git，点击push，
  - 点击define remote
  - 起名字并输入URL
  - 点击push即可推送成功

- 把远程仓库中的diamante克隆到本地
  - 点击file---》点击Close project
  - 此时退出当前项目并进入最开始的新建项目的页面
  - 点击check out from version control
  - 点击git
  - 输入URL
  - 选择clone的代码放在哪里
  - 点击clone
  - 然后一路next
  - clone下来的代码也能看到以前版本控制的信息

