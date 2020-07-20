---
title: Java注意点
toc: true
date: 2020-07-16 10:35:49
categories: 
 - Java
 - Java语言入门
---
<meta name="referrer" content="no-referrer"/>

## 1、数组初始化注意事项
```java
 int[] numbers = new int[8];
```
上面的代码的目的就是做了一个数组的初始化，这个初始化的作用就是开辟了该长度的存储空间。**数组初始化完后**，并没有存储实际的值，**int 类型的数据默认值是 0**,**String 类型的数据默认值是 null**。

## 2、循环
### 增强for循环
增强`for`循环是`JDK1.5`以后出来的一个高级`for`循环，专门用来遍历数组和集合的。它的内部原理其实是个`Iterator`迭代器，所以在遍历的过程中，**不能对集合中的元素进行增删操作**。<br />格式：
```java
for(元素的数据类型 变量 : Collection集合or数组){
    System.out.println();
}
```
遍历数组的例子
```java
int[] arr = new int[]{11,22,33};
for (int n : arr) {
    //变量n代表被遍历到的数组元素
    System.out.println(n);
}
```
遍历Collection集合的例子
```java
Collection<String> coll = new ArrayList<String>();
coll.add("a1");
coll.add("a2");
coll.add("a3");
coll.add("a4");
for(String str : coll){
    //变量Str代表被遍历到的集合元素
    System.out.println(str);
}
```

## 3、字符串分割注意点
### 字符串分割split()
这里要强调一下特殊字符的分割
> `.` `|` `*`  这三个字符如果作为分割符，那么就需要加上 `\\`,比如 `str.split("\\|")` 

## 4、静态变量使用场景
有些时间我们还是需要在多个对象里共享一些数据，这个时候就需要引入**常量**了，常量也可以叫做**静态变量**。常量的特点是不需要实例化，在 **Java 当中实际上是创建了一个全局唯一的内存空间并且分配给了这个变量**。所以常量的值只会随 Java 的销毁才会被销毁，这样也就方便我们存储一些数据到内存中，否则会随着对象的销毁被销毁掉的。
### 使用场景
> 1、常用的字符串值
> 2、需要在内存做缓存的值

## 5、子类继承了父类的私有属性及方法吗？
**子类对象确实拥有父类对象中所有的属性和方法**，但是父类对象中的私有属性和方法，**子类是无法访问到的**，只是拥有，但不能使用。<br />

## 6、Exception和RuntimeException的区别
- `Exception` ：受检查的异常，<font color=red>**这种异常是强制我们catch或throw的异常。**</font>你遇到这种异常必须进行catch或throw，如果不处理，编译器会报错。比如：IOException。手工抛出其余的 `Exception` 异常时，<font color=red>**必须在方法上约定可能抛出的异常。**</font>
- `RuntimeException`：运行时异常，<font color=red>**这种异常我们不需要处理，完全由虚拟机接管。**</font>比如我们常见的NullPointerException，我们在写程序时不会进行catch或throw。手工抛出 `RuntimeException` 异常时，<font color=red>**不需要在方法上约定可能抛出的异常。**</font>

## 7、实例内部类注意事项
<font color=red size=5>**特性：**</font>
- 实例内部类不能有静态成员(包括属性、方法) 
- 实例内部类对象外部创建语法:Outer.new Inner(); 
- 实例方法访问外部类实例成员:Outer.this.成员（包含私有成员）
```java
class Outer1{
    private String name="张三";
    private int num1=10;
    public void outerShow(){
        System.out.println(name);
        System.out.println(num1);
    }
    public class Inner1{
        private String name="李四";
        private int num2=20;
        private static final int num3=10;//静态常量在内部类中是可以的
        //private static int num3=30;//在成员内部类中不能声明静态的成员,包括属性和方法
        public void innerShow(){
            System.out.println(name);
            //System.out.println(Outer1.this.name);
            System.out.println(num2);
            outerShow();//成员内部类可以直接访问外部类的属性和方法，包括私有的
        }
    }
}  

```

