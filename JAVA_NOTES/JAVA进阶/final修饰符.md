# 1.final

## 1.1 final的作用

- final意为最终，可修饰类、变量、方法
  - 修饰类：表明该类是最终类，不能被继承
  - 修饰方法：表明该方法是最终方法，不能被重写
  - 修饰变量：表明该变量第一次赋值后，不能被再次赋值，即有且仅能被赋值一次

## 1.2 final注意事项

- final修饰的变量为**基本数据类型**：变量存储的**数据值**不能发生改变
- final修饰的变量为**引用数据类型**：变量存储的**地址值**不不能发生改变，但地址值指向的**对象内容可以发生改变**

## 1.3 常量

### 1.3.1 常量的概述与基本作用

- 常量是使用了`public static final`修饰的**成员变量**，必须有初始化值，且执行的过程中值不能被改变
- 作用
  - 可用作系统的配置信息，方便维护
  - 提高可读性
- 常量名命名规范：英文单词全部大写，多个单词使用下划线进行连接
- 常量执行原理
  - 在编译阶段会进行“宏替换”，将使用常量的地方全部替换为真实的字面量

### 1.3.2 常量做信息标志与分类

- 提高代码可读性，实现了软编码形式

```java
public class Test{
  public static final int UP = 1; //定义常量
  public static final int DOWN = 2;
  public static final int LEFT = 3;
  public static final int RIGHT = 4;
  
  public static void move(int flag){
    switch(flag){  //将常量作为标志，进行操作
      case UP:
        sout("UP");
        break;
      case DOWN:
        sout("DOWN");
        break;
      case LEFT:
        sout("LEFT");
        break;
      case RIGHT:
        sout("RIGHT");
        break;
    }
  }
}
```

