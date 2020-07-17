---
title: Map接口
toc: true
date: 2020-07-17 17:08:00
categories:
 - Java
 - Java面向对象
---

## 1、分析
Map接口中键和值一一映射. 可以通过键来获取值。

- 给定一个键和一个值，你可以将该值存储在一个Map对象. 之后，你可以通过键来访问对应的值。<br />
- 当访问的值不存在的时候，方法就会抛出一个NoSuchElementException异常.<br />
- 当对象的类型和Map里元素类型不兼容的时候，就会抛出一个 ClassCastException异常。<br />
- 当在不允许使用Null对象的Map中使用Null对象，会抛出一个NullPointerException 异常。<br />
- 当尝试修改一个只读的Map时，会抛出一个UnsupportedOperationException异常。

![](https://cdn.nlark.com/yuque/0/2020/png/437282/1594976617431-376ad1cc-79fb-4b3f-ad89-1d32572c7580.png#align=left&display=inline&height=259&margin=%5Bobject%20Object%5D&originHeight=259&originWidth=441&size=0&status=done&style=none&width=441)

## 2、Map遍历
```java
 for (Map.Entry<Integer,String> entry : map.entrySet()){ 

   System.out.println("Key = " + entry.getKey() + 
                  ", Value = " + entry.getValue());
 }
```

## 3、方法列表

- <font color=red>**void clear( )**</font><br />_从此映射中移除所有映射关系（可选操作）。_<br />
- <font color=red>**boolean containsKey(Object k)**</font><br />_如果此映射包含指定键的映射关系，则返回 true。_<br />
- <font color=red>**boolean containsValue(Object v)**</font><br />_如果此映射将一个或多个键映射到指定值，则返回 true。_<br />
- <font color=red>**Set entrySet( )**</font><br />返回此映射中包含的映射关系的 Set 视图。<br />
- boolean equals(Object obj)<br />比较指定的对象与此映射是否相等。<br />
- <font color=red>**Object get(Object k)**</font><br />返回指定键所映射的值；如果此映射不包含该键的映射关系，则返回 null。<br />
- boolean isEmpty( )<br />如果此映射未包含键-值映射关系，则返回 true。<br />
- Set keySet( )<br />返回此映射中包含的键的 Set 视图。<br />
- <font color=red>**Object put(Object k, Object v)**</font><br />将指定的值与此映射中的指定键关联（可选操作）。<br />
- void putAll(Map m)<br />从指定映射中将所有映射关系复制到此映射中（可选操作）。<br />
- Object remove(Object k)<br />如果存在一个键的映射关系，则将其从此映射中移除（可选操作）。<br />
- <font color=red>**int size( )**</font><br />返回此映射中的键-值映射关系数。<br />
- <font color=red>**Collection values( )**</font><br />返回此映射中包含的值的 Collection 视图。<br />
