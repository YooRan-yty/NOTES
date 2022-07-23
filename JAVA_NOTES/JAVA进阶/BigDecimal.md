# 1.BigDecimal

- 使用BigDecimal，就不允许计算不准确
- 为解决精度问题，只能使用字符串为参数的构造方法 或 BigDecimal.Valueof(double) 进行创建

```java
BigDecimal b1 = new BigDecimal("123");
BigDecimal b2 = BigDecimal.valueOf(123);

b1.add(b2);
b1.subtract(b2);
b1.multiply(b2);
b1.divide(b2);

b1.divide(b2,3);//此方法以及过时
b1.divide(b2,RoundingMode.UP);//四舍五入向上取
```

