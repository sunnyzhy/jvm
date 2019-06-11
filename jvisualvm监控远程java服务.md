1. 打开 jvisualvm，选择 "远程" -> 右键 "添加远程主机" -> 输入主机 IP 地址（比如 192.168.0.1） -> "确定"

2. windows服务器
-  在任意目录下新建 java.policy 策略文件（比如 D 盘），输入以下内容

```
grant codebase "file:${java.home}/../lib/tools.jar" {
   permission java.security.AllPermission;
};
```

```
只有开放权限，才能使用 Visual GC
```

- 启动jstatd

```
jstatd -J-Djava.security.policy=D:\java.policy
```

3. 在新建的远程主机上，右键 "添加 jstatd 连接"，默认端口 1099

4. 在windows服务器上启动 java 服务

```
java -Djava.rmi.server.hostname=192.168.0.1 -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=1199 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -jar D:\java\remote_jvm-0.0.1-SNAPSHOT.jar &
```

192.168.0.1是服务器地址

1199是监控端口

D:\java\remote_jvm-0.0.1-SNAPSHOT.jar是 java 服务的路径
