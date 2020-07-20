---
title: Duration类
toc: true
date: 2020-07-20 11:55:22
categories:
 - Java
 - Java类
 - java.time
---
<meta name="referrer" content="no-referrer"/>

## 1、方法列表
| **方法** | **描述** |
| :---: | :---: |
| **static Duration between(Temporal startInclusive, Temporal endExclusive)** | 获取表示两个临时对象之间的持续时间的Duration |

## 2、Duration类的应用
### 获取两个日期的间隔天数
```java
LocalDateTime startDay = LocalDateTime.of(2019, 9, 1, 8, 0, 0);
LocalDateTime endDay = LocalDateTime.of(2020, 1, 15, 18, 0, 0);

//得到两个日期的间隔天数
long days = Duration.between(startDay,endDay).toDays();
```