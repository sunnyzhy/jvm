# 官网
[MAT官网](https://www.eclipse.org/mat/ "MAT官网")

# java was started but returned exit code=13
本地安装32的jdk，与eclipse要求的64位jdk不符合

# MAT Java heap space OutOfMemory
编辑文件MemoryAnalyzer.ini
```
-startup
plugins/org.eclipse.equinox.launcher_1.3.100.v20150511-1540.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.win32.win32.x86_64_1.1.300.v20150602-1417
-vmargs

-Xmx2048m
```

**Xmx 默认是1024m ，可以把 Xmx 设置大一些 2048m**
