---
title: LocalDate类
toc: true
date: 2020-07-16 16:23:58
categories: 
 - Java
 - Java语言入门
---

## 一、日期时间与字符串的转化
```java
	LocalDate time = LocalDate.now();
    // 打印默认的时间数据
    System.out.println(time.toString());
    // 创建一个格式化方式
    DateTimeFormatter df = DateTimeFormatter.ofPattern("yyyy年MM月dd");
    // 执行时间的格式化处理，得到期望格式的时间字符串
    String timeStr = df.format(time);


    // 定义一个时间字符串，日期是2019年1月1日
    String date = "2019/01/01";
    DateTimeFormatter df = DateTimeFormatter.ofPattern("yyyy/MM/dd");
    // 把字符串转化位 LocalDate 对象，并得到字符串匹配的日期
    LocalDate date2 = LocalDate.parse(date,df);
    // 打印出日期
    System.out.println(date2.toString());
```

## 二、LocalDate获取日期时间具体的值

### 获取年、月、日、星期
> 获取月、星期      重点关注

```java
	LocalDate time = LocalDate.now();

    // 得到当前时间所在年
    int year = time.getYear();
    System.out.println("当前年份 " + year);

    // 得到当前时间所在月
    int month = time.getMonth().getValue();
    System.out.println("当前月份 " + month);

    // 得到当前时间在这个月中的天数
    int day = time.getDayOfMonth();
    System.out.println("当前日 " + day);

    // 得到当前时间所在星期数
    int dayOfWeek = time.getDayOfWeek().getValue();
    System.out.println("当前星期 " + dayOfWeek);
```

## 三、LocalDate时间日期的加减运算
```java
    LocalDate now = LocalDate.now();
    System.out.println("当前：" + now.toString());

    System.out.println("加法运算");
    System.out.println("加1天：" + now.plusDays(1));
    System.out.println("加1周：" + now.plusWeeks(1));
    System.out.println("加1月：" + now.plusMonths(1));
    System.out.println("加1年：" + now.plusYears(1));

    System.out.println("减法运算");
    System.out.println("减1天：" + now.minusDays(1));
    System.out.println("减1周：" + now.minusWeeks(1));
    System.out.println("减1月：" + now.minusMonths(1));
    System.out.println("减1年：" + now.minusYears(1));
```

## 四、两个LocalDate日期时间的比较

### 之前、之后、同一天
```java
	LocalDate now = LocalDate.now();

    // 可以对两个 LocalDate 进行比较，
    // 可以判断一个日期是否在另一个日期之前、之后或同一天，
    // 或者判断两个日期是否是同年同月同日。
    boolean isBefore = now.minusDays(1).isBefore(LocalDate.now());
    System.out.println("是否在当天之前：" + isBefore);

    boolean isAfter = now.plusDays(1).isAfter(LocalDate.now());
    System.out.println("是否在当天之后：" + isAfter);

    // 判断是否是当天
    boolean sameDate = now.isEqual(LocalDate.now());
    System.out.println("是否在当天：" + sameDate);
```
