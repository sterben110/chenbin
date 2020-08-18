---
title: Hexo问题与解决方案
toc: true
date: 2020-07-17 18:24:16
categories: Hexo
---
<meta name="referrer" content="no-referrer"/>

## 1、hexo引用外网的图片不显示
方法其实很简单，只需要文章的头部如下图所示位置添加`<meta name="referrer" content="no-referrer"/>`这一句话就可以完美解决问题。
```markdown
---
title: Hexo问题与解决方案
toc: true
date: 2020-07-17 18:24:16
categories:
---
<meta name="referrer" content="no-referrer"/>
```