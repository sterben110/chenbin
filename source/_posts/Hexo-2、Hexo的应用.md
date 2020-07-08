---
title: Hexo-2、Hexo的应用
date: 2020-07-08 17:33:48
tags:
---
<a name="3a3636e1"></a>
# 1、创建博客
```
hexo new 博客名
```
利用这条命令我们可以创建一个新的md文件，比如我们输入`hexo new hello`，<br />那么框架就会自动替我们创建一个叫做hello.md的文。<br />创建的md文件存放在我们博客文件夹下source/_posts文件夹内，然后重新发布博客就可以了。
<a name="beb9b908"></a>
# 2、Hexo更换主题
<a name="3cbb5269"></a>
## 下载主题文件至themes目录下
```
//在博客根目录中使用该命令
git clone https://github.com/iissnan/hexo-theme-next themes/next
```


> 这里`[https://github.com/iissnan/hexo-theme-next](https://github.com/iissnan/hexo-theme-next)`是该主题的仓库地址



> `themes/next`表示下载到根目录中的themes文件夹下，下载为next文
> 件夹，注意前面有个空格和仓库地址分隔哦

<a name="95cb21c7"></a>
## 更改文件配置
我们打开`_config.yml`这个文件，将配置中的`theme: landscape`改为`theme: next`
<a name="f6cb763b"></a>
## 发布更改
`hexo generate` -> `hexo deploy` -> `hexo clean` 
