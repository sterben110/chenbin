---
title: List接口
toc: true
date: 2020-07-19 15:18:31
categories:
 - Java
 - Java类
 - java.util
---
<meta name="referrer" content="no-referrer"/>

## 1、方法列表
| 方法 | 描述 |
| :--- | :--- |
| <font color=red>**boolean add(E o)**</font> | 向列表的尾部追加指定的元素
| **void add(int index,E element)** | 在列表的指定位置插入指定元素。
| <font color=red>**boolean addAll(Collection<? extends E> c)**</font> | 追加指定 collection中的所有元素到此列表的结尾，顺序是指定collection的迭代器返回这些元素的顺序。
| **boolean addAll(int index,Collection<? extends E> c)** | 将指定collection中的所有元素都插入到列表中的指定位置。
| **void clear()** | 从列表中移除所有元素。
| **boolean contains(Object o)** | 如果列表包含指定的元素，则返回true。
| **boolean containsAll(Collection<?> c)** | 如果列表包含指定collection的所有元素，则返回true。
| **boolean equals(Object c)** | 比较指定的对象与列表是否相等。
| <font color=red>**E get(int index)**</font> | 返回列表中指定位置的元素。
| **int hashCode()** | 返回列表的哈希码值。
| **int indexOf(Object o)** | 返回列表中首次出现指定元素的索引，如果列表不包含此元素，则返回-1。
| **boolean isEmpty()** | 判断集合是否为空 如果为空 则返回true,否则返回false
| <font color=red>**Iterator<E> iterator()**</font> | 返回以正确顺序在列表的元素上进行迭代的迭代器。
| **int lastIndexOf(Object o)** | 返回列表中最后出现指定元素的索引，如果列表不包含此元素，则返回-1。
| **ListIterator<E> listIterator()** | 返回列表中元素的列表迭代器（以正确的顺序）。
| **ListIterator<E> listIterator(int index)** |返回列表中元素的列表迭代器（以正确的顺序），从列表的指定位置开始。
| <font color=red>**E remove(int index)**</font> | 移除列表中指定位置的元素。
| **boolean remove(Object o)** | 移除列表中出现的首个指定元素。
| **boolean removeAll(Collection<?> c)** | 从列表中移除指定collection中包含的所有元素。
| **boolean retainAll(Collection<?> c)** |仅在列表中保留指定collection中所包含的元素。
| <font color=red>**E set(int index,E element)**</font> | 用指定元素替换列表中指定位置的元素。
| <font color=red>**int size()**</font> | 返回列表中的元素数。
| **List<E> subList(int forIndex,int toIndex)** | 返回列表中指定的formIndex(包括) 和toIndex(不包括)之间的部分视图。
| **Object toArray()** | 返回以正确顺序包含列表中的所有元素的数组。

## 2、List类相关的应用
### List转为数组
```java
    public static void main(String[] args) {
        List<Integer> al = new ArrayList<Integer>();
        al.add(10);
        al.add(20);
        al.add(30);
        al.add(40);

        // 转化为数组
        Integer[] arr = al.toArray(new Integer[] {});

        for (Integer x : arr) {
            System.out.println(x + " ");
        }
    }
```
### List转为字符串
利用`String`类的`String.join(",",list)`方法
```java
    public static void main(String args[]) {
        // 创建字符串集合
        List<String> list = Arrays.asList("Geeks", "ForGeeks", "GeeksForGeeks");

        // 转化集合为字符串， 使用 `,` 分割
        String string = String.join(",", list);
        // 打印结果
        System.out.println("字符串是: " + string);
    }
```
### List的排序
利用`java.util.Collection`类中的`sort()`方法
> static <T> void sort(List<T> list, Comparator<? super T> c)
```java
 public static void main (String[] args) {
    List<Student> ar = new ArrayList<Student>();
    ar.add(new Student(111, "bbbb", "london"));
    ar.add(new Student(131, "aaaa", "nyc"));
    ar.add(new Student(121, "cccc", "jaipur"));

    System.out.println("原始集合");
    for (int i=0; i<ar.size(); i++) {
      System.out.println(ar.get(i));
    }

    // 实现升序排序
    Collections.sort(ar, new Comparator<Student>(){
      public int compare(Student a, Student b) {
        // 第一个参数的学号 > 第二个参数的学号
        return a.getRollNo() - b.getRollNo();
      }
    });

    System.out.println("\n排序后的集合");
    for (int i=0; i<ar.size(); i++) {
      System.out.println(ar.get(i));
    }

  }
```
### List的过滤
```java
public class AccountingRecord {
  //创建时间
  private String createTime;
  //记录时间
  private Date time;
  //金额
  private int amount;
  //收入或支出
  private String type;
  //分类
  private String category;
}

  //List<AccountingRecord> records=new ArrayList();
  List<AccountingRecord> filterd=records.stream().filter(str->str.getAmount()>amount).collect(Collectors.toList());
```