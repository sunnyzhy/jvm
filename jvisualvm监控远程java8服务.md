# 添加远程主机
打开 jvisualvm，选择 "远程" -> 右键 "添加远程主机" -> 输入主机 IP 地址（比如 192.168.0.1） -> "确定"

# linux服务器
## 新建策略文件
在任意目录下新建 jstatd.policy 策略文件

```
# vim /usr/jstatd.policy
grant codebase "file:${java.home}/../lib/tools.jar" {
   permission java.security.AllPermission;
};
```

**只有开放权限，才能使用 Visual GC。**

## 启动jstatd
- 默认启动

```
jstatd -J-Djava.security.policy=/usr/jstatd.policy
```

- 指定启动端口

```
jstatd -J-Djava.security.policy=/usr/jstatd.policy -p 1099
```

- 指定端口和IP

```
jstatd -J-Djava.security.policy=/usr/jstatd.policy -J-Djava.rmi.server.hostname=192.168.0.1 -p 1099
```

**此时，即可在远程主机名下显示出远程服务器上运行的所有 java 进程。**

# windows服务器
## 新建策略文件
在任意目录下新建 jstatd.policy 策略文件（比如 D 盘），输入以下内容

```
grant codebase "file:${java.home}/../lib/tools.jar" {
   permission java.security.AllPermission;
};
```

## 启动jstatd

```
jstatd -J-Djava.security.policy=D:\jstatd.policy
```

## 添加 jstatd 连接
在新建的远程主机上，右键 "添加 jstatd 连接"，默认端口 1099

**此时，即可在远程主机名下显示出远程服务器上运行的所有 java 进程。**

# 添加 JMX 连接
## 在服务器上启动 java 服务

```
java -Xmx256m -Xms256m -Djava.rmi.server.hostname=192.168.0.1 -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=1199 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -jar D:\java\remote_jvm-0.0.1-SNAPSHOT.jar
```

```
192.168.0.1是服务器地址

1199是监控端口

D:\java\remote_jvm-0.0.1-SNAPSHOT.jar是 java 服务的路径
```

## 添加 JMX 连接
在新建的远程主机上，右键 "添加 JMX 连接"，输入IP和端口，如 192.168.0.1:1199
