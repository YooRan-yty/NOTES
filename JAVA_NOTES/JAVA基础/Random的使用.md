## 1.Random模块的使用

### 1.1 使用步骤

1. 导包
2. 创建对象
3. 获取随机数

```java
import java.util.Random;  //导包
Random r = new Random();  //创建对象
int num = r.nextInt(10);  //获取随机数，范围为[0,10)
```

```java
//猜大小
Random r = new Random();
int random = r.nextInt();
Scanner in = new Scanner(System.in);

while(true){
  System.out.println("输入：");
  int num = in.nextInt();
  if (num > random){
    System.out.println("大了");     //while为死循环，在结束if判断后，会开始新的循环
  }else if (num < random){
    System.out.println("小了");
  }else{
    System.out.println("猜对了");
    break;
  }
}
```

