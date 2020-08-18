---
title: SASS/SCSS
toc: true
date: 2020-08-10 14:57:01
categories:
 - CSS
---
<meta name="referrer" content="no-referrer"/>

**SASS 是一款 CSS 预编译器**，它定义了一种新的编程语言，为CSS添加了一些编程的特性。SASS有变量、函数、控制语句、混用、嵌套等高级功能。<br />SASS有两种语法，一种是**SCSS**，另一种是类似yaml一样的**缩进语法**。
# SCSS语法
## 1、变量
```css
/* 声明变量 */
$width: 10px;
	/* 变量类型为字符串，一般不需要加引号，但是有些特殊情况*，比如字符串中有双斜杠“//”，
		就需要用英文输入法状态下的单引号或者双引号包裹字符串，用引号的写法 */
$url: 'https://www.yuque.com/';
	/* 定义类似数组的遍量 */
$animals: puppy kitty chick;

/* 使用变量 */
#main {
  width: $width;
}
#main {
  width: $width / 2;
  height: $width * 2;
}
```

## 2、嵌套
### 嵌套规则
![image.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1597042054160-4fa4476d-cdbb-4124-b24d-d98514a5f578.png#align=left&display=inline&height=266&margin=%5Bobject%20Object%5D&name=image.png&originHeight=354&originWidth=652&size=91047&status=done&style=none&width=489)
### 父选择器 &
![image.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1597042183281-45493093-692e-48b0-84f6-02eb25399b7a.png#align=left&display=inline&height=217&margin=%5Bobject%20Object%5D&name=image.png&originHeight=289&originWidth=653&size=65836&status=done&style=none&width=490)

## 3、复用
无参数时
```css
@mixin square {
  width: 100px;
  height: 100px;
}

// 应用：
.user-avatar {
  @include square;
}
.admin-avatar {
  @include square;
}
```
参数无默认值时
```css
@mixin square($size) {
  width: $size;
  height: $size;
}

// 应用
.avatar {
  @include square(100px);
}
```
参数有默认值时
```css
@mixin square($size: 100px,$lineHeight: 50px) {
  width: $size;
  height: $size;
  line-height: $lineHeight;
}

// 不传参数就会使用默认的值 100px
.avatar {
  @include square;
}

// 传入参数就会使用传入的值 200px
.avatar-200 {
  @include square(200px,100px);
}
```

## 4、其他
### 插值法
`#{}` 插值几乎可以在Sass样式表的任何地方使用：
```css
$name: "mail";
$top-or-bottom: "top";
$left-or-right: "left";

.icon-#{$name} {
  background-image: url("/icons/#{$name}.svg");
  position: absolute;
  #{$top-or-bottom}: 0;
  #{$left-or-right}: 0;
}
```