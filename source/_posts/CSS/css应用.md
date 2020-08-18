---
title: css应用
toc: true
date: 2020-08-10 12:18:01
categories:
 - CSS
---
<meta name="referrer" content="no-referrer"/>

## 1、单行文本超出省略
```
/* 强制不换行 */
white-space: nowrap;
/* 隐藏超出部分 */
overflow: hidden;
/* 用省略号代替剩余内容 */
text-overflow: ellipsis;
```

## 2、元素水平居中
> 1. 若内部为行内元素，我们可以在父容器上使用 `text-align: center`  。
> 1. 若内部是块状元素，我们可以在子容器上使用 `margin: 0 auto` （若内部不是块状元素，需要设置 `display: block` ）。