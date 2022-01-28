JOptionPane  ----弹窗相关类

获取本机ip

```java
InetAddress addr = InetAddress.getLocalHost();
String ip = addr.getHostAddress();
Stirng name = addr.getHostName();
```

通过String的ip获得InetAddress对象：

> InetAdress adress = InetAdress.getByName(ip);