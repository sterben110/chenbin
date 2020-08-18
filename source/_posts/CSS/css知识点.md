---
title: css知识点
toc: true
date: 2020-07-31 16:20:53
categories:
 - CSS
---
<meta name="referrer" content="no-referrer"/>


## 1、行内元素不能设置宽高
行内元素不能设置`width`和`height`,但可以设置`padding`。<br />行内元素可以设置左右 `margin` ,不可以设置上下 `margin` 

## 2、两个盒子之间margin的计算
**水平距离：margin等于两者margin之和**<br />![](https://cdn.nlark.com/yuque/0/2020/png/437282/1596187549738-48b83058-91b5-4252-97d2-5d79b44f8666.png#align=left&display=inline&height=204&margin=%5Bobject%20Object%5D&originHeight=204&originWidth=1000&size=0&status=done&style=none&width=1000)<br />**垂直距离：margin取较大值**<br />![](https://cdn.nlark.com/yuque/0/2020/png/437282/1596187573244-93df2bab-a63e-474e-8590-6c5d10f48541.png#align=left&display=inline&height=378&margin=%5Bobject%20Object%5D&originHeight=378&originWidth=1000&size=0&status=done&style=none&width=1000)

## 3、空白折叠现象
我们将 `div` 的 `display` 属性从 `block` 切换成 `inline-block` 之后，我们希望得到的效果是这样的:<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1596187907799-97bbd30c-6173-4df1-9942-8f94710e55cc.png#align=left&display=inline&height=59&margin=%5Bobject%20Object%5D&name=image.png&originHeight=78&originWidth=374&size=890&status=done&style=none&width=281)<br />但是得到的结果却是这样的：<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1596187942637-da61d1e4-4be5-40b1-bb72-068fb3c53111.png#align=left&display=inline&height=53&margin=%5Bobject%20Object%5D&name=image.png&originHeight=70&originWidth=493&size=972&status=done&style=none&width=370)<br />两个盒子中间多了一点空白，但是我们并没有设置margin，这就是传说中的<font color=red>**空白折叠**</font>现象。<br />其原因就是因为两个 div 之间多了一个回车，在html中，回车被当作是一个文字，所以这里的空白就是文字的空白，相当于在两个div之间加了一个字母。<br />**解决方案：给父元素设置font-size为0；**
```html
<div class="father">
  <div class="box1"></div>
  <div class="box2"></div>
</div>
```
```css
.father {
  font-size: 0px;
}

.box1 {
  width: 200px;
  height: 50px;
  display: inline-block;
  background-color: #fff2cc;
}

.box2 {
  width: 200px;
  height: 50px;
  display: inline-block;
  background-color: #b0e3e6;
}
```
## 4、margin问题
**兄弟之间的margin**
> 我们之间最常用的应该是这种兄弟之间的margin

**![微信图片_20200804154725.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1596527293425-9e1ab01c-dcb7-42da-9148-2f8aa7211546.png#align=left&display=inline&height=364&margin=%5Bobject%20Object%5D&name=%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20200804154725.png&originHeight=364&originWidth=1430&size=45445&status=done&style=none&width=1430)**<br />**父子之间的margin**<br />分为两种情况：父元素有border和没有border时<br />![微信图片_20200804155102.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1596527477051-15bfa7b0-832f-45c6-88d4-1afca5ea7818.png#align=left&display=inline&height=134&margin=%5Bobject%20Object%5D&name=%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20200804155102.png&originHeight=534&originWidth=1050&size=25451&status=done&style=none&width=263)
> 如上图所示，纸箱靠墙，人在纸箱里，
> 给人设置margin-top就相当于人在往上踹，这时有两种结果，
> 1. 一种就是纸箱的上边没有纸箱壁（也就是没有border-top），此时人往上踹，踹到的是墙，所以**纸箱会跟着人一起往下跑**。
> 1. 纸箱有上纸箱壁（有border-top），此时人往上踹，人会因为反作用力，远离纸箱壁，而**纸箱并没有动**。
> 
同样的道理理解margin-bottom失效原因即可。

## 5、选择器优先级问题
### （1）单个选择器
> **单个选择器的优先级顺序：id 选择器>类选择器>标签选择器**
### （2）高级选择器的优先级
高级选择器的优先级由权重决定。权重的作用就是决定当用**两个不同的选择器**给**同一个标签**设置了相同的属性，该听谁的。
> 假设 id 选择器的权重为 100，类选择器的权重为 10，标签选择器的权重为 1。
> `.param #item span{}` 该选择器的权重为：10+100+1=111
> `#item1 #item2 .param1 .param2 p span {}` 该选择器的权重为：200+20+2=222

## 6、文字属性的继承性
例如`font-size`(文字大小)、`font-weight`(文字粗细)、`font-family`(字体)、`color`(文字颜色)等属性属于文字属性，子类标签会继承的是离它最近的一个父类标签的文字属性。
```html
<ul class="ul-item">
  <li>
    <p>文字的颜色到底是什么颜色？</p>
  </li>
</ul>
```
```css
.ul-item {
  color: #ff6973;
}
```
像这样，p标签父类的父类定义了字体颜色为`#ff6973`,p标签自己又没有定义颜色,此时p标签的颜色就是`#ff6873`。
