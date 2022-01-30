JOptionPane  ----弹窗相关类

获取本机ip

```java
InetAddress addr = InetAddress.getLocalHost();
String ip = addr.getHostAddress();
Stirng name = addr.getHostName();
```

通过String的ip获得InetAddress对象：

> InetAdress adress = InetAdress.getByName(ip);



用idea打jar包只能将src文件中的东西打包，jar包相当于src目录。

要是用到图片

要么将图片放在src目录下，然后使用类加载器进行图片获取，

要么在jar包旁边依照原目录结构放置文件，把jar当做src。

