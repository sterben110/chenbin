---
title: Arrays类
toc: true
date: 2020-07-19 15:16:20
categories:
 - Java
 - Java类
 - java.util
---
<meta name="referrer" content="no-referrer"/>

## 1、方法列表
sort()方法

## 2、Arrays类的相关应用
### 数组转为List
利用`java.util.Arrays`类的`asList()`方法,该方法无法对<font color=red>**基本类型数组**</font>进行转换。<font color=red>**只能转换对象数组**</font>。
```java
  public static void main(String[] args) {
    // 数字数组
    Integer[] intArr = { 10, 20, 15, 22, 35 };
    // 转化数组为 list
    List<Integer> lists = Arrays.asList(intArr);
    System.out.println("集合的长度是: " + lists.size());
  }
```
```java
 public static void main(String[] args) {
   // 转化数组为 list
   List<String> lists = Arrays.asList("小王","小明");
   System.out.println("集合的长度是: " + lists.size());

   // 转化数组为 list2
   List<String> lists2 = Arrays.asList("小王","小明","小李");
   System.out.println("集合2的长度是: " + lists2.size());
 }
 ```

### 数组的排序
利用`java.util.Arrays`类的`sort()`方法就可以实现数组的自定义排序，默认是升序排序。
> static <T> void sort(T[] a, Comparator< super T> c):
```java
    public static void main(String[] args) {

        Integer[] intArr = { 10, 20, 15, 22, 35 };

        // 自定义排序
        Arrays.sort(intArr, new Comparator<Integer>(){
            public int compare(Integer o1, Integer o2){
                // 判断 o2>o1，执行降序排序
                return o2-o1;
            }
        });

        System.out.println("Integer Array: "
                           + Arrays.toString(intArr));
    }
```

### 数组转为字符串
利用`java.util.Arrays`类的`toString()`方法用于转换数组（包含基本类型数组）为字符串
```java
    public static void main(String[] args) {

        boolean[] boolArr = new boolean[] { true, true, false, true };
        byte[] byteArr = new byte[] { 10, 20, 30 };
        char[] charArr = new char[] { 'g', 'e', 'e', 'k', 's' };
        double[] dblArr = new double[] { 1, 2, 3, 4 };
        float[] floatArr = new float[] { 1, 2, 3, 4 };
        int[] intArr = new int[] { 1, 2, 3, 4 };
        long[] lomgArr = new long[] { 1, 2, 3, 4 };
        Object[] objArr = new Object[] { 1, 2, 3, 4 };
        short[] shortArr = new short[] { 1, 2, 3, 4 };

        System.out.println(Arrays.toString(boolArr));
        System.out.println(Arrays.toString(byteArr));
        System.out.println(Arrays.toString(charArr));
        System.out.println(Arrays.toString(dblArr));
        System.out.println(Arrays.toString(floatArr));
        System.out.println(Arrays.toString(intArr));
        System.out.println(Arrays.toString(lomgArr));
        System.out.println(Arrays.toString(objArr));
        System.out.println(Arrays.toString(shortArr));
    }
```


