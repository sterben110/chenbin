---
title: Math类
toc: true
date: 2020-07-15 13:51:37
categories: 
 - Java
 - Java类
 - java.lang
---
<meta name="referrer" content="no-referrer"/>

## 一、Math.random()
Math.random() 方法返回一个<font color=red>**double类型**</font>的随机数，随机数范围为<font color=red>**[0,1)**</font>。
```java
// 得到一个随机数
double value = Math.random();
System.out.println(value);
```

### 生成6位随机数的例子
```java
//得到一个随机数[10的5次方，10的6次方)
double value = (Math.random()*9+1)*10⁵;
```