---
title: 1、初识Hexo
date: 2020-07-08 17:24:39
categories: Hexo
toc: true
---
# 一、Hexo定义
hexo是一个快速、简洁且高效的博客框架，它支持几条简短的命令发布博客，因此是对于初学者比较友好的博客框架。

# 二、安装Hexo
[hexo的安装](https://hexo.io/zh-cn/docs/#%E5%AE%89%E8%A3%85-Hexo)

1. 安装**Node.js**和**Git**
1. 然后使用npm安装Hexo
```
npm install -g hexo-cli
```
1. 局部安装 `hexo` 包
```
npm install hexo
```

安装以后，可以使用以下两种方式执行 Hexo命令：
1. `npx hexo <command>`
1. 将 Hexo 所在的目录下的 node_modules 添加到环境变量之中即可直接使用 hexo ：
```
echo 'PATH="$PATH:./node_modules/.bin"' >> ~/.profile
```

# 三、创建博客文件夹
进入某目录，执行如下命令创建博客文件夹：
```
//在当前目录下创建一个叫blog的博客文件夹
hexo init blog
```

# 四、安装发布工具
进入博客目录（`cd blog`），打开控制台，输入以下命令：
```
npm install hexo-deployer-git --save
```


# 五、修改配置文件
找到blog文件夹中的`_config.yml`文件，输入如下配置：
```
theme: landscape
deploy:
  type: git  
  repository: git@github.com:sterben110/sterben110.github.io.git  
  branch: master
```

# 六、Hexo提交
## hexo generate
```
hexo generate
```
作用是生成新的静态文件,可以简写为`hexo g`
## hexo deploy
```
hexo deploy
```
作用是把生成的文件部署到我们的博客上，可以简写为`hexo d`，发布后，我们就可以看到我们的博客变成了这样：
![](https://cdn.nlark.com/yuque/0/2020/png/437282/1594185106908-7ab390a4-e0fc-45bc-a0c0-4b04b20d7392.png#align=left&display=inline&height=1302&margin=%5Bobject%20Object%5D&originHeight=1302&originWidth=2524&size=0&status=done&style=none&width=2524)
## hexo clean
```
hexo clean
```
用途是清除缓存，能让新发布的博客能快速生效
