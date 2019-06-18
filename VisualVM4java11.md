# 官网
[https://docs.oracle.com/en/java/javase/11/](https://docs.oracle.com/en/java/javase/11/ "jdk11官网")

## Migration Guide(迁移指南)

### Removed Java VisualVM

Java VisualVM is a tool that provides information about code running on a Java Virtual Machine. The jvisualvm tool was provided with JDK 6, JDK 7, and JDK 8.

Java VisualVM is no longer bundled with the JDK, but you can get it from the [VisualVM open source project site](https://visualvm.github.io/ "VisualVM open source project site") .

# 安装 VisualVM
## 下载
[https://visualvm.github.io/](https://visualvm.github.io/ "VisualVM")

## 修改配置文件
1. 打开 etc\visualvm.conf
2. 修改 visualvm_jdkhome="jdk的绝对路径"

## 安装 VisualGC
参照[VisualVM安装VisualGC插件](https://github.com/sunnyzhy/jvm/blob/master/VisualVM%E5%AE%89%E8%A3%85VisualGC%E6%8F%92%E4%BB%B6.md "VisualVM安装VisualGC插件")

## VisualVM监控远程java11服务
[VisualVM监控远程java11服务](https://github.com/sunnyzhy/jvm/blob/master/VisualVM%E7%9B%91%E6%8E%A7%E8%BF%9C%E7%A8%8Bjava11%E6%9C%8D%E5%8A%A1.md "VisualVM监控远程java11服务")


