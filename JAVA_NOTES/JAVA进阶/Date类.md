# 1.Date类

## 1.1 构造方法

| 方法                   | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| public Date()          | 无参构造，当前时间                                           |
| public Date(long data) | 有参构造，根据传入的毫秒值，设置时间对象。可理解为从时间原点开始，向后推移多少毫秒 |

## 1.2 成员方法

| 方法                           | 说明                                                         |
| ------------------------------ | ------------------------------------------------------------ |
| piblic void setTime(long data) | 根据传入的毫秒值，设置日期对象；即从时间原点开始，向后推移多少毫秒 |
| public long getTime( )         | 根据Date对象设置的值，获取毫秒值；随着对象的改变而改变       |

```java
Date d1 = new Date();
d1.setTime(1000);
d1.getTime();//1000，与System.currentTimeMillis的区别：system的方法每次都会获取从时间原点到现在的毫秒值；而getTime方法会根据setTime方法设定的时间，获取毫秒值

d1.setTime(System.currentTimeMillis); // 获取时间原点到现在的毫秒值，setTime方法会根据毫秒值将时间设置为当前的时间
d1.getTime()//此时d1.getTime的值与System.currentTimeMillis()相同
```

# 2. SimpleDateFormat类

- 格式化日期对象

## 2.1 构造方法

| 方法                                    | 说明                                 |
| --------------------------------------- | ------------------------------------ |
| public SimpleDateFormat( )              | 无参，使用默认格式，来格式化日期对象 |
| public SimpleDateFormat(String pattern) | 有参，使用给定格式，来格式化日期对象 |



## 2.2 成员方法

| 方法                                  | 说明                                                         |
| ------------------------------------- | ------------------------------------------------------------ |
| public final String format(Data data) | 将传入的日期对象，进行格式化操作，返回字符串                 |
| public Date parse(String source)      | 将传入的字符串解析为时间对象。字符串的格式要与构造方法的格式相同才行！ |

```java
//无参构造
SimpleDateFormat sdf = new SimpleDateFormat();
Date d = new Date();
String s = sdf.format(d); //根据默认格式，格式化日期对象，返回字符串

//有参构造
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
String s = "2022-10-20";
Date d = sdf.parse(s); //根据字符串解析出时间对象，返回时间对象；注：格式要与构造方法的格式相同！！！
```



```java
//按格式输入生日，输出过了多少天
Scanner in = new Scanner(System.in);
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd"); //创建日期格式化对象，有参构造，设定格式
sout("输入生日");
String s = in.nextLine();
Date date = new Date(); //创建Date对象，无参构造，默认为当前时间
date = sdf.parse(s);//调用parse方法，将字符串按照格式解析为日期对象
sout(date.getTime() / 1000 / 60 / 60 / 24);//通过getTime方法，获取日期对象中的日期到现在的毫秒值。运算得到天数
```

