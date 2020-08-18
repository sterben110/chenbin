---
title: css渐变
toc: true
date: 2020-08-09 21:08:58
categories:
 - CSS
---
<meta name="referrer" content="no-referrer"/>

[学习链接地址](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Using_CSS_gradients)

## 线性渐变
从某一个边界到另一个边界的颜色渐变
> 1. background：linear-gradient(red, blue); 从上到下
> 1. background：linear-gradient(to right, red, blue); 从左到右
> 1. background：linear-gradient(to bottom right, red, blue); 从左上到右下
> **0deg代表从上往下，90deg代表从左往右，-90deg代表从右往左**
> 1. **background：linear-gradient(180deg, red, blue); 角度渐变**
> 1. background：linear-gradient(red 10%, green 85%, blue 90%); 多色渐变
> 1. background：linear-gradient(to right, rgba(255,0,0,0), rgba(255,0,0,1)); 透明度渐变
> 1. background：repeating-linear-gradient(red, yellow 10%, green 20%); 重复渐变

## 径向渐变
从某一个点开始的向四周扩散的颜色渐变
> 1. background：radial-gradient(red, green, blue); 同比例
> 1. background：radial-gradient(red 5%, green 15%, blue 60%); 自定义比例
> 1. background：radial-gradient(circle, red, yellow, green); 环形径向渐变

实例：`background: radial-gradient(red 10px, yellow 30%, #1e90ff 50%);` <br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1596978141735-15f341e0-2bee-495c-bb38-13f623e7e749.png#align=left&display=inline&height=80&margin=%5Bobject%20Object%5D&name=image.png&originHeight=159&originWidth=160&size=12072&status=done&style=none&width=80)