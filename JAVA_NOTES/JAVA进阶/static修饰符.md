状态修饰符

| 修饰符 | 范围                   | 特点                                                         |
| ------ | ---------------------- | ------------------------------------------------------------ |
| final  | 成员变量、成员方法、类 | 对方法：不能被重写；对变量：不能再被赋值；对类：不能被继承； |
| static | 成员变量、成员方法     | 对类的所有对象共享；可通过类名进行调用；                     |

# 1.static 

- 可修饰成员变量、成员方法
- static修饰的成员变量，表示该成员变量只在内存中存储一份，可以被共享、访问

## 1.1特点

- 可以被类的所有对象共享
- 使用类名进行调用（推荐）
- 访问特点
  - 非静态的成员方法
    - 1.可直接访问静态的成员变量
    - 2.可直接访问非静态的成员变量
    - 3.可直接访问静态的成员方法
    - 4.可直接访问非静态的成员方法
  - 静态的成员方法
    - 1.可访问静态的成员变量
    - 2.可访问静态的成员方法
    - 3.可**间接**访问实例成员变量
    - 4.可**间接**访问实例成员变量

## 1.2 静态成员变量与静态成员方法

### 1.2.1 静态成员变量

- 成员变量的分类
  - 1.静态成员变量：用static修饰，属于**类**、加载一次、可以被共享访问
  - 2.实例成员变量：无static修饰，属于**对象**

![](https://tva1.sinaimg.cn/large/e6c9d24egy1h4512uxno5j215t0u0djg.jpg)

步骤：

1. class文件进入方法区
2. 堆内存中，同步生成类的静态变量区，存放static修饰的成员变量
3. main方法进入栈内存中执行
4. 可通过类名直接访问静态变量
5. 可通过对象，访问静态变量，因为静态变量被同一个类的所有对象所共享

### 1.2.2 静态成员方法

- 成员方法分类
  - 1.静态成员方法：有static修饰，属于类，可用类名进行访问，也可以用对象名进行访问
  - 2.实例成员方法：无static修饰，属于对象，只能用对象进行访问
- 使用场景
  - 功能表示对象自身的行为，需要访问实例成员变量的情况下，需要声明为实例方法
  - 若方法以执行一个公用功能为目的，则可以声明为静态方法

![](https://tva1.sinaimg.cn/large/e6c9d24egy1h452e72e5kj212t0u0777.jpg)

## 1.3 工具类

- 类中都是一些静态方法，每个方法都是以完成一个公用的功能为目的，这个类用于给系统开发人员共同使用的。

- 优点：方便调用、一次编写，多次复用
- 要求：私有化构造方法
  - 原因：可直接从工具类中调用方法，无需先创建对象，再进行调用，节省了堆内存。

```java
//ArrayUtil.java
public class ArrayUtil{ //创建工具类
  private ArrayUtil(){} //私有化构造方法
  public static String tostring(int[] arr){  //创建静态方法,返回数组转化后的字符串
    StringBuilder sb = new StringBuilder("["); //通过StringBuilder进行字符串拼接
    for(int i=0;i<arr.length;i++){
      if(i != arr.length-1){
        sb.append(arr[i] + ", ");
      }else{
        sb.append(arr[i] + "]");
      }
    }
    return sb.toString();
  }
}

//Test.java
public class Test{
  public static void main(String[] args){
    int[] arr = {1,2,3};
    sout(ArrayUtil.tostring(arr));//直接通过类名，调用静态方法
  }
}
```

## 1.4 代码块

### 1.4.1 概述

- 概述：代码块，是类的5大成分之一（成员变量、构造方法、成员方法、代码块、内部类），定义在类中方法外；
- 在java类下，使用{}括起来的代码，称为代码块；

### 1.4.2 代码块分类

- 静态代码块
  - 格式：static {}
  - 特点：需要static修饰，随着类的加载而加载（比main要先执行），且自动触发、只执行一次
  - 使用场景：在类加载时做一些静态数据的初始化
- 构造代码块
  - 格式：{}
  - 特点：每次创建对象，调用构造器执行时，都会执行代码块中的内容，并且在构造器执行之前执行
  - 使用场景：初始化实例资源

## 1.5 单例设计模式

开发时，会遇到问题，问题通常有多种解法，但一定有一个解法是最优的，这个最优解被称之为，设计模式

### 1.5.1 概述

- 单例模式：可以保证系统中，应用该模式的类，永远只有一个实例，即一个类永远只能创建一个对象
- 优点：节省内存空间

### 1.5.2 恶汉单例

- 在类中获取对象时，对象已经**提前**创建好了
- 设计步骤
  - 1.定义一个类，将构造器私有
  - 2.定义一个静态变量存储一个对象

```java
//ArrayUtil.java
public class ArrayUtil{
  public static ArrayUtil instance = new ArrayUtil();//提前创建对象，用静态变量存储
  private ArrayUtil(){} //私有化构造函数
}
//Test.java
public class Test{
  public static void main(String[] args){
    ArrayUtil s1 = ArrayUtil.instance;//直接通过类访问静态变量，不需要再new一次，应为对象已经提前创建好，此处可理解为只是将地址值传给了s1；
    ArrayUtil s2 = ArrayUtil.instance;
    sout(s1 == s2);//true,证实了单例，只能创建一个对象
  }
}
```

### 1.5.3 懒汉单例

- 在真正需要该对象时，才会去创建一个对象（延迟加载对象）
- 设计步骤
  - 1.定义一个类，将构造器私有
  - 2.定义一个静态变量存储一个对象,注意添加private修饰符，不再允许其他类直接访问，防止获取到null；
  - 3.提供一个返回单例对象的方法。（参考JavaBean，将成员变量私有化，通过方法去访问成员变量）

```java
//SingleInstance.java
public class SingleInstance{
  private static SingleInstannce instance;//私有化静态变量，定义一个对象，但暂时不进行创建；注意！此静态成员变量，必须私有化、且不能创建对象，否则就与恶汉单例相同了；
  private SingleInstance(){}//构造方法私有化
  public static SingleInstance getInstance(){
    if(instance == null){  //先判断单例是否是第一次调用方法来创建对象，若是第一次，由于对象创建后默认值为null，进行判断，相同则创建对象；若此处不进行判断，则每调用一次方法，都会创建一个对象
      instance = new SingleInstance();
    }
    return instance;
  }
}

//Test.java
public class Test{
  public static void main(String[] args){
    SingleInstance s1 = SingleInstance.getInstance();
    SingleInstance s2 = SingleInstance.getInstance();
  }
}
```

