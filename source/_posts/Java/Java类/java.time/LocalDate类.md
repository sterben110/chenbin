---
title: LocalDate类
toc: true
date: 2020-07-16 16:23:58
categories: 
 - Java
 - Java类
 - java.time
---
<meta name="referrer" content="no-referrer"/>

## 1、方法列表
### 创建LocalDate
| **方法** | **描述** |
| :---: | :---: |
| <font color=red>**static LocalDate now()**</font> | 获取默认时区的当前日期 |
| **static LocalDate now(Clock clock)** | 从指定时钟获取当前日期 |
| **static LocalDate now(ZoneId zone)** | 获取指定时区的当前日期 |
| <font color=red>**static LocalDate of(int year, int month, int dayOfMonth)**</font> | 根据指定的年、月、日获取LocalDate 实例 |
| **static LocalDate of(int year, Month month, int dayOfMonth)** | 根据指定的年、月、日获取LocalDate 实例 |

### 获取、修改年月日等
| **方法** | **描述** |
| :---: | :---: |
| <font color=red>**int getYear()**</font> | 获取年份 |
| <font color=red>**int getMonth().getValue()**</font> | 获取月份 |
| <font color=red>**int getDayOfMonth()**</font> | 获取日期在该月是第几天 |
| <font color=red>**int getDayOfWeek().getValue()**</font> | 获取日期是星期几 |
| <font color=red>**int getDayOfYear()**</font> | 获取日期在该年是第几天 |
| <font color=red>**LocalDate withYear(int year)**</font> | 修改该日期的年份 |
| <font color=red>**LocalDate withMonth(int month)**</font> | 修改该日期的月份 |
| <font color=red>**LocalDate withDayOfMonth(int dayOfMonth)**</font> | 修改该日期在当月的天数 |

### 加减天、周、月、年
| **方法** | **描述** |
| :---: | :---: |
| **LocalDate plusDays(long daysToAdd)** | 返回增加了*天的LocalDate副本 |
| **LocalDate plusWeeks(long weeksToAdd)** | 返回增加了*周的LocalDate副本 |
| **LocalDate plusMonths(long monthsToAdd)** | 返回增加了*月的LocalDate副本 |
| **LocalDate plusYears(long yearsToAdd)** | 返回增加了*年的LocalDate副本 |
| **LocalDate minusDays(long daysToSubtract)** | 返回减少了*天的LocalDate副本 |
| **LocalDate minusWeeks(long weeksToSubtract)** | 返回减少了*周的LocalDate副本 |
| **LocalDate minusMonths(long monthsToSubtract)** | 返回减少了*月的LocalDate副本 |
| **LocalDate minusYears(long yearsToSubtract)** | 返回减少了*年的LocalDate副本 |

### 日期判断、比较
| **方法** | **描述** |
| :---: | :---: |
| **boolean isLeapYear()** | 检查是否闰年 |
| **int lengthOfMonth()** | 返回日期所在月份共有几天 |
| **int lengthOfYear()** | 返回日期所在年份共有几天 |
| **boolean isEqual(ChronoLocalDate other)** | 日期与另一个日期比较 |
| **boolean isAfter(ChronoLocalDate other)** | 检查日期是否在指定日期之后 |
| **boolean isBefore(ChronoLocalDate other)** | 检查日期是否在指定日期之前 |
| <font color=red>**int compareTo(ChronoLocalDate other)**</font> | 比较该日期与other日期的大小，返回正数，那么当前对象时间较晚（数字较大） |

### 日期转换
| **方法** | **描述** |
| :---: | :---: |
| <font color=red>**String format(DateTimeFormatter formatter)**</font> | 使用特定格式化形式将LocalDate转为字符串 |
| <font color=red>**static LocalDate parse(CharSequence text)**</font> | 从文本字符串获取LocalDate实例 |
| <font color=red>**static LocalDate parse(CharSequence text, DateTimeFormatter formatter)**</font> | 使用特定格式化形式从文本字符串获取LocalDate实例 |

## 2、LocalDate的相关应用
### 日期与字符串的转化
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
### 日期的加减运算
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
### 日期之间的比较
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