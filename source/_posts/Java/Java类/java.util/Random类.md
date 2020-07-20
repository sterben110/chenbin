---
title: Random类
toc: true
date: 2020-07-18 13:13:28
categories:
 - Java
 - Java类
 - java.util
---
<meta name="referrer" content="no-referrer"/>

## int nextInt(int n)方法
int nextInt(int n) 返回一个[0,n)区间内的随机整数，范围: <font color=red>**[0,n)**</font>
```java
// 实例化随机数
Random r = new Random();
// 得到0-7之间的随机数
int num = r.nextInt(8);

// 如果想得到 0-8 之间的随机数
int num = r.nextInt(9);

// 如果想得到50-100之间的随机数
int num = r.nextInt(51)+50;
// 这个 51 = 100 - 50 + 1
```