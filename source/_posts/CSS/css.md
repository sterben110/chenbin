---
title: css
toc: true
date: 2020-07-31 15:23:38
categories:
 - CSS
---
<meta name="referrer" content="no-referrer"/>

# CSS 选择器
| 选择器 | 示例 |
| :--- | :--- |
| <font color=red>元素选择器</font> | **html {color: black;}** |
| <font color=red>类选择器</font> | **.important {font-weight: bold;}** |
| <font color=red>id选择器</font> | **#red {color: red;}** |
| <font color=red>后代选择器</font> | **#password .box p{}** |
| <font color=red>子选择器</font> | **p>span {color: orangered;}** |
| <font color=red>相邻兄弟选择器</font> | **h1 + p {margin-top:50px;}** |
| <font color=red>伪类</font> | **span::before {}**<br />**span::after {}**<br />**li:hover {}       /* 鼠标悬浮时 */**<br />**li:active {}       /* 鼠标点击时 */**<br />**input:focus {}     /* 获取焦点后 */**<br />**ul>li:first-child {}     /* 匹配父元素的第一个子元素 */**<br />**ul>li:last-child {}      /* 匹配父元素的最后一个子元素 */**<br />**ul>li:nth-child(3) {}      /* 匹配父元素的第3个子元素 */**<br />**ul>li:not(:last-child) {}    /* 匹配父元素除最后一个元素之外的子元素 */** |

# CSS 样式
## 1、背景属性
| 属性 | 描述 |
| :--- | :--- |
| <font color=red >background</font> | 简写属性，作用是将背景属性设置在一个声明中。 |
| <font color=red >background-color</font> | 设置元素的背景颜色。 |
| <font color=red >background-image</font> | 把图像设置为背景。 |
| <font color=red >background-repeat</font> | 设置背景图像是否及如何重复。 |
| <font color=red >background-attachment</font> | 背景图像是否固定或者随着页面的其余部分滚动。 |
| <font color=red >background-position</font> | 设置背景图像的起始位置。 |
| <font color=red >background-size</font> | 规定背景图片的尺寸。 |
| <font color=red >background-clip</font> | 规定背景的绘制区域。 |

![文字属性.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1596976556478-65ef8cc4-ee30-4f22-9fd8-f0c5d0eeec45.png#align=left&display=inline&height=587&margin=%5Bobject%20Object%5D&name=%E6%96%87%E5%AD%97%E5%B1%9E%E6%80%A7.png&originHeight=1108&originWidth=1408&size=161757&status=done&style=none&width=746)
## 2、文本属性
| 属性 | 描述 |
| :--- | :--- |
| <font color=red>color</font> | 设置文本颜色 |
| <font color=red>direction</font> | 设置文本方向。 |
| <font color=red>line-height</font> | 设置行高。 |
| <font color=red>letter-spacing</font> | 设置字符间距。 |
| <font color=red>text-align</font> | 对齐元素中的文本。 |
| <font color=red>text-decoration</font> | 向文本添加修饰。 |
| <font color=red>text-indent</font> | 缩进元素中文本的首行。 |
| <font color=red>text-shadow</font> | 设置文本阴影。CSS2 包含该属性，但是 CSS2.1 没有保留该属性。 |
| <font color=red>text-transform</font> | 控制元素中的字母。 |
| <font color=red>white-space</font> | 设置元素中空白的处理方式。 |
| <font color=red>word-spacing</font> | 设置字间距。 |

![文本属性.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1596974416669-a276023a-3cac-4bf9-943a-d1e8dac0fae2.png#align=left&display=inline&height=534&margin=%5Bobject%20Object%5D&name=%E6%96%87%E6%9C%AC%E5%B1%9E%E6%80%A7.png&originHeight=534&originWidth=821&size=52265&status=done&style=none&width=821)
## 3、字体属性
| 属性 | 描述 |
| :--- | :--- |
| <font color=red>font-family</font> | 设置字体系列。 |
| <font color=red>font</font> | 简写属性。作用是把所有针对字体的属性设置在一个声明中。 |
| <font color=red>font-size</font> | 设置字体的尺寸。 |
| <font color=red>font-size-adjust</font> | 当首选字体不可用时，对替换字体进行智能缩放。（CSS2.1 已删除该属性。） |
| <font color=red>font-stretch</font> | 对字体进行水平拉伸。（CSS2.1 已删除该属性。） |
| <font color=red>font-style</font> | 设置字体风格。 |
| <font color=red>font-variant</font> | 以小型大写字体或者正常字体显示文本。 |
| <font color=red>font-weight</font> | 设置字体的粗细。 |

![文字属性(1).png](https://cdn.nlark.com/yuque/0/2020/png/437282/1596973316953-bacf2300-9d23-4658-ba4c-ff1804035db4.png#align=left&display=inline&height=643&margin=%5Bobject%20Object%5D&name=%E6%96%87%E5%AD%97%E5%B1%9E%E6%80%A7%281%29.png&originHeight=643&originWidth=1013&size=80565&status=done&style=none&width=1013)

# CSS 布局
## 1、定位布局方式
![image.png](https://cdn.nlark.com/yuque/0/2019/png/437282/1566041226844-05a5e1b5-b639-4311-9393-09ac04737f3c.png#align=left&display=inline&height=398&margin=%5Bobject%20Object%5D&name=image.png&originHeight=478&originWidth=985&size=62977&status=done&style=none&width=820.8333007163485)<br />**Position-static（默认定位）**
> 浏览器会自动给所有的 DOM 元素，添加 `position: static` 属性。 `static`  遵循默认的文档流布局, `top、right、bottom、left` 等属性此时无用。

**Position-relative（相对定位）**
> `relative`  是相对于当前元素 `static`  布局位置进行的调整。它先遵循默认的文档流布局，然后再用 `top、right、bottom、left` 等属性进行位置调整。
> `z-index` 默认为 `0` 。

![](https://cdn.nlark.com/yuque/0/2020/jpeg/437282/1597034377359-e865e326-dfb0-4dfb-827c-ebb244c4ef35.jpeg#align=left&display=inline&height=398&margin=%5Bobject%20Object%5D&originHeight=1593&originWidth=993&size=0&status=done&style=none&width=248)<br />**Position-absolute（绝对定位）**
> `absolute`  是相对于<font color=red>**最近非static定位祖先元素**</font>布局位置进行的调整。它脱离了默认的文档流布局，变为了第二图层，然后用 `top、right、bottom、left` 等属性来确定元素位置。
> `z-index` 默认为 `0` 。


<br />**`absolute` 定位的元素会变为类似块状元素的元素， `width、height、padding、margin` 等都可以设置。**<br />**<br />![](https://cdn.nlark.com/yuque/0/2020/jpeg/437282/1597034880385-92219cbf-3af6-48e5-9a16-d5e38172742e.jpeg#align=left&display=inline&height=399&margin=%5Bobject%20Object%5D&originHeight=1593&originWidth=995&size=0&status=done&style=none&width=249)<br />**Position-fixed（固定布局）**
> `fixed` 定位类似 `absolute` ，是相对于屏幕视口（viewport）进行的位置调整。它脱离了默认的文档流布局，用 `top、right、bottom、left` 等属性来确定元素位置。元素的位置在屏幕滚动时不会改变。

## 2、浮动布局方式
> `float` 会脱离文档流，浮动到父元素的左侧或右侧位置。它常常会出现布局错乱现象，这种时候就需要通过清除浮动的方式来解决浮动元素的影响。

## 3、Flex布局方式
**采用 Flex 布局的元素，称为 Flex 容器（flex container），简称”容器”。**<br />**它的所有子元素称为 Flex 项目（flex item），简称”项目”。**<br />![](https://cdn.nlark.com/yuque/0/2020/jpg/437282/1597036845542-08306877-ee8e-4055-9b42-d3012e292885.jpg#align=left&display=inline&height=301&margin=%5Bobject%20Object%5D&originHeight=1204&originWidth=1644&size=0&status=done&style=none&width=411)<br />**Flex布局中有两条轴——主轴和交叉轴**<br />![](https://cdn.nlark.com/yuque/0/2020/jpeg/437282/1597036951214-b04b678a-dd37-4c6f-8a06-13a843cc88d0.jpeg#align=left&display=inline&height=301&margin=%5Bobject%20Object%5D&originHeight=602&originWidth=822&size=0&status=done&style=none&width=411)

| 属性 | 描述 |
| :--- | :--- |
| <font color=red>justify-content</font> | 定义项目在主轴方向上的对齐方式。 |
| <font color=red>align-items</font> | 定义项目在交叉轴方向上的对齐方式。 |
| <font color=red>flex-wrap</font> | 定义项目溢出时换行方式。 |
| <font color=red>flex</font> | 设置项目如何分配空间。 |
| <font color=red>flex-direction</font> | 设置flex主轴方向。 |

> **注意：**设为 Flex 布局以后，子元素的 float、clear 和 vertical-align 属性将失效

### justify-content 和 align-items
> `justify-content` 和 `align-items` 是容器的属性，设置在容器上。

![9.jpg](https://cdn.nlark.com/yuque/0/2020/jpeg/437282/1597038348901-b7ea7eff-3d0a-4cd2-a3d5-290f8f5cec0b.jpeg#align=left&display=inline&height=472&margin=%5Bobject%20Object%5D&name=9.jpg&originHeight=1252&originWidth=1326&size=196131&status=done&style=none&width=500)<br />![10.jpg](https://cdn.nlark.com/yuque/0/2020/jpeg/437282/1597038447784-6e4b2797-fb7d-447d-90c5-5c6cd127e815.jpeg#align=left&display=inline&height=472&margin=%5Bobject%20Object%5D&name=10.jpg&originHeight=1252&originWidth=1326&size=168483&status=done&style=none&width=500)
### flex-wrap
![](https://cdn.nlark.com/yuque/0/2020/jpg/437282/1597038530622-1adb967c-6eb9-42a9-8113-1cc74a61beb5.jpg#align=left&display=inline&height=642&margin=%5Bobject%20Object%5D&originHeight=1284&originWidth=884&size=0&status=done&style=none&width=442)
### flex
`flex: [flex-grow flex-shrink flex-basis] | auto | initial | inherit ;` ![image.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1597038772525-ac62ec5e-170f-4a63-be03-560a0720b136.png#align=left&display=inline&height=185&margin=%5Bobject%20Object%5D&name=image.png&originHeight=185&originWidth=1073&size=25338&status=done&style=none&width=1073)<br />![1597038945188-0f43d343-c952-4e1d-82cc-646d9200c0a5.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1597039079782-be9200f5-10f0-491e-a726-c4c69afc8d29.png#align=left&display=inline&height=175&margin=%5Bobject%20Object%5D&name=1597038945188-0f43d343-c952-4e1d-82cc-646d9200c0a5.png&originHeight=175&originWidth=619&size=434264&status=done&style=none&width=619)<br />![1597039107369-f84f2266-e51e-42fa-92c5-d8fd7bbdc485.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1597039213686-5079cc80-03f2-4451-8a44-435ffc481a9a.png#align=left&display=inline&height=177&margin=%5Bobject%20Object%5D&name=1597039107369-f84f2266-e51e-42fa-92c5-d8fd7bbdc485.png&originHeight=177&originWidth=613&size=434982&status=done&style=none&width=613)<br />![image.png](https://cdn.nlark.com/yuque/0/2020/png/437282/1597039251451-abe19f9d-db58-4ad2-a4fb-931cb30fa4a6.png#align=left&display=inline&height=341&margin=%5Bobject%20Object%5D&name=image.png&originHeight=454&originWidth=658&size=32159&status=done&style=none&width=494)
### flex-direction
![](https://cdn.nlark.com/yuque/0/2020/jpg/437282/1597039314580-aa913e22-95d7-4480-b879-a51b9904f229.jpg#align=left&display=inline&height=564&margin=%5Bobject%20Object%5D&originHeight=564&originWidth=1804&size=0&status=done&style=none&width=1804)


# CSS 高级
## 1、媒介查询
![](https://cdn.nlark.com/yuque/0/2020/jpeg/437282/1597042797718-a0a87287-adbf-40aa-9449-bcdf8fcbbc98.jpeg#align=left&display=inline&height=456&margin=%5Bobject%20Object%5D&originHeight=911&originWidth=1197&size=0&status=done&style=none&width=599)