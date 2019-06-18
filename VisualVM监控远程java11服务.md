# 注意
在 java11 中策略文件 jstatd.policy 需要修改为以下内容

```
grant codebase "jrt:/jdk.jstatd" {
   permission java.security.AllPermission;
};

grant codebase "jrt:/jdk.internal.jvmstat" {
   permission java.security.AllPermission;
};
```

# 其他配置流程
参照[jvisualvm监控远程java8服务](https://github.com/sunnyzhy/jvm/edit/master/jvisualvm%E7%9B%91%E6%8E%A7%E8%BF%9C%E7%A8%8Bjava8%E6%9C%8D%E5%8A%A1.md "jvisualvm监控远程java8服务")
