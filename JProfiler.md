# JProfiler

[JProfiler 官网](https://www.ej-technologies.com/products/jprofiler/overview.html 'JProfiler')

## JProfiler 远程监控 JVM

### 下载 liunx 版的 jprofiler-11.1.4

```bash
# cd /usr/local

# tar -zxvf jprofiler_linux_11_1_4.tar.gz

# vim /etc/profile
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/jprofiler11.1.4/bin/linux-x64

# source /etc/profile
```

### 下载 windows 版的 jprofiler-11.1.4

1. 安装完成之后，启动 JProfiler
2. 点击 ```Start Center -> New Session -> New Remote Integration```
3. 选择 ```On a remote computer: Linux X86/AMD64```，下一步
4. 选择 ```JVM Vendor: Oracle; Version: 1.8.0; Mode: hotspot```，下一步
5. 选择 ```Startup immediately, connect later with the JProfiler GUI```，下一步
6. 输入 ```Direct connection to: 远程服务器IP```，下一步
7. 输入 ```Remote installation directory: 远程服务器上安装的JProfiler目录```，如 ```/usr/local/jprofiler11.1.4```，下一步
8. 选择 ```Apply configuration when conneting with the JProfiler GUI```，下一步
9. 端口号默认 ```8849```，下一步
10. ***非常重要***，配置完成之后，下一步
      1. 把 ```C:\Users\user\.jprofiler11\jprofiler_config.xml``` 复制到远程服务器 ```/usr/local/jprofiler11.1.4/config``` 的目录里
      2. 把 ```-agentpath:/usr/local/jprofiler11.1.4/bin/linux-x64/libjprofilerti.so=port=8849,nowait``` 添加到业务 java 程序的启动参数里，如 ```nohup java -jar -XX:+HeapDumpOnOutOfMemoryError -Xmx256m -Xms256m ./gateway.jar -agentpath:/usr/local/jprofiler11.1.4/bin/linux-x64/libjprofilerti.so=port=8849,nowait  > /dev/null 2>&1 &```
11. 选择 ```Yes, start the session and wait for the remote application.```，完成。

### 启动远程服务器的 jpenable

```bash
# cd /usr/local/jprofiler11.1.4/bin

# ./jpenable
Select a JVM:
kkFileView-2.2.1.jar [1321] [1]
org.elasticsearch.server/org.elas...rch.bootstrap.Elasticsearch [2787] [2]
./gateway.jar -age...lerti.so=port=8849,nowait [43628] [3]
3
Please select the profiling mode:
GUI mode (attach with JProfiler GUI) [1, Enter]
Offline mode (use config file to set profiling settings) [2]
1
Please enter a profiling port
[37642]
8849  
You can now use the JProfiler GUI to connect on port 8849
```

1. 选择需要监测的服务，序号 ```3```
2. 选择 ```GUI mode```，序号 ```1```
3. 输入默认的端口号：```8849```

### 启动 windows 的 JProfiler

选择 ```Start Center -> Remote application on 远程服务器IP```
