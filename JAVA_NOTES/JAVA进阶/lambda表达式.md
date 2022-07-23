# 1.lambda表达式

## 1.1 概述

- JKD8之后出现的新语法形式
- 作用：简化匿名内部类的代码
- 格式：（）->{}
  - ( ):存放内部类中被重写的方法的形参列表
  - ->:语法格式，无特殊含义
  - {}:方法体

```java
//lambda.java
public class lambda{
  public static void Operate(Swimming s){ //此方法加上static，因为main方法被static修饰，静态只能访问静态
    s.swim();
  }
  
  public static void main(String[] args){
    Operate(()->{sout("游泳")};); //
  }
}

interface Swimming{
  public abstract void swim();
}
```

## 1.2 lambda的省略规则

- lambda只能简化，函数式编程接口

  - 函数式编程接口：有且只有一个抽象方法的接口

  

- 形参的数据类型可以省略

- 只有一个参数时，可以省略（）

- 方法体只有一条语句时，{}以及；可以省略（同时省略）

- 方法体只有一条语句时，若是return语句，则return和；可以省略（同时省略）

```java
//lambda.java
@FunctionInterface  //表示为函数式编程接口
interface Swimming{
  public abstract void swim();
}

public class lambda{
  public static void operate(Swimming s){
    s.swim();
  }
  
  public static void main(String[] args){
    operate(()->{sout("游泳")});
  }
}
```

