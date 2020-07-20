---
title: Map接口
toc: true
date: 2020-07-17 17:08:00
categories:
 - Java
 - Java类
 - java.util
---
<meta name="referrer" content="no-referrer"/>

## 1、分析
Map接口中键和值一一映射. 可以通过键来获取值。

- 给定一个键和一个值，你可以将该值存储在一个Map对象. 之后，你可以通过键来访问对应的值。 
- 当访问的值不存在的时候，方法就会抛出一个NoSuchElementException异常. 
- 当对象的类型和Map里元素类型不兼容的时候，就会抛出一个 ClassCastException异常。 
- 当在不允许使用Null对象的Map中使用Null对象，会抛出一个NullPointerException 异常。 
- 当尝试修改一个只读的Map时，会抛出一个UnsupportedOperationException异常。

![](https://cdn.nlark.com/yuque/0/2020/png/437282/1594976617431-376ad1cc-79fb-4b3f-ad89-1d32572c7580.png#align=left&display=inline&height=259&margin=%5Bobject%20Object%5D&originHeight=259&originWidth=441&size=0&status=done&style=none&width=441)

## 2、方法列表
| 方法 | 描述 |
| :--- | :--- |
| <font color=red>**void clear( )**</font> | _从此映射中移除所有映射关系（可选操作）。_ 
| <font color=red>**boolean containsKey(Object k)**</font> | _如果此映射包含指定键的映射关系，则返回 true。_ 
| <font color=red>**boolean containsValue(Object v)**</font> | _如果此映射将一个或多个键映射到指定值，则返回 true。_ 
| <font color=red>**Set entrySet( )**</font> | 返回此映射中包含的映射关系的 Set 视图。 
| **boolean equals(Object obj)** | 比较指定的对象与此映射是否相等。 
| <font color=red>**Object get(Object k)**</font> | 返回指定键所映射的值；如果此映射不包含该键的映射关系，则返回 null。 
| **boolean isEmpty( )** | 如果此映射未包含键-值映射关系，则返回 true。 
| **Set keySet( )** | 返回此映射中包含的键的 Set 视图。 
| <font color=red>**Object put(Object k, Object v)**</font> | 将指定的值与此映射中的指定键关联（可选操作）。 
| **void putAll(Map m)** | 从指定映射中将所有映射关系复制到此映射中（可选操作）。 
| **Object remove(Object k)** | 如果存在一个键的映射关系，则将其从此映射中移除（可选操作）。 
| <font color=red>**int size( )**</font> | 返回此映射中的键-值映射关系数。 
| <font color=red>**Collection values( )**</font> | 返回此映射中包含的值的 Collection 视图。 

## 3、Map接口的相关应用
### Map的遍历
```java
 for (Map.Entry<Integer,String> entry : map.entrySet()){ 

   System.out.println("Key = " + entry.getKey() + 
                  ", Value = " + entry.getValue());
 }
```