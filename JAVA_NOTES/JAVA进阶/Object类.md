# 1.Object类

## 1.1 常用方法

| public String toString(Object o) | 返回该对象的字符串表示形式；建议每一个子类都重写此方法；不重写则打印地址值 |
| -------------------------------- | ------------------------------------------------------------ |
| public boolean equals(Object o)  | 判断对象是否相等，默认比较地址值；重写后可比较内容           |

```java
//重写equals
//Student.java
@Override
public boolean equals(Object o){
  if (this == o){  //首先判断两个对象的地址值，若相等，则直接返回true
    return true;
  }
  if (o == null || getClass() != o.getClass()){ //判断传入的对象是否为空、或两个对象不属于同一类，不满足任意一个条件，直接返回false
    return false;
  }
  Student stu = (Student) o; //向下转型，将父类引用转为子类对象(Object为父类，o为父类的引用)
  if (age != stu.age){ //通过对象访问成员变量，比较成员对象的值
    return false;
  }
  return name != null ? name.equals(stu.name) ; stu.name == null; //判断成员是否为空，不为空则比较值是否相同，同则返回true。
}
```

