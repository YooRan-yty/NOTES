# 跨平台原理



```mermaid
graph LR
JAVA程序 -.javac编译.-> A[class文件]
A --> Windows.JVM虚拟机
A --> Linux.JVM虚拟机
A --> MAC.JVM虚拟机
```

