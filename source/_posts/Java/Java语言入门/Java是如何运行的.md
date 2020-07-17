---
title: Java是如何运行的
toc: true
date: 2020-07-15 13:44:28
categories: 
 - Java
 - Java语言入门
---

## 一、什么是编程语言
Java 是一种高级语言，有“高级语言”自然也有“低级语言”，一般计算机世界里把“低级语言”叫做机器语言或者汇编语言。计算机<font color=red>**只能运行低级语言**</font>，所以<font color=red>**高级语言编写的程序必须先被翻译成低级语言才能运行**</font>。<br /><font color=red>**高级语言的优点**</font>有很多：更容易编程、更容易阅读和修改、<font color=red>**可移植性高**</font>；低级语言只能在一种计算机上运行。

## 二、Java语言的执行
![](https://cdn.nlark.com/yuque/0/2020/svg/437282/1594785283558-6833f28a-67d6-40f9-b2ab-54ab51ae1885.svg#align=left&display=inline&height=98&margin=%5Bobject%20Object%5D&originHeight=98&originWidth=765&size=0&status=done&style=none&width=765)<br />Java 既可以被编译也可以被解释，不同的是<font color=red>**Java 编译**</font>过程并不生成机器语言，而是<font color=red>**生成字节码**</font>。<font color=red>**字节码**</font>和机器语言一样，但是它<font color=red>**具备高级语言的可移植性**</font>。JVM （Java virtual machine ，Java 虚拟机）支持了对<font color=red>**字节码的解释运行**</font>。

## 三、Java代码的注释

### 1、块注释
```java
/**
* 	我是块注释
*/
```

### 2、行注释
```java
// 我是行注释
```

