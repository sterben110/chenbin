---
title: Hexo-3、本地电脑部署博客步骤
date: 2020-07-08 17:35:57
tags:
---
<a name="45ca8f20"></a>
# 1、本地安装Git
<br />在官网下载最新版本的git：[下载地址](https://git-scm.com/downloads)<br />

```
//查看git版本号
git --version
```

<a name="290f6479"></a>
# 2、本地配置SSH并绑定至GitHub
```
//生成本地SSH
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
//查询本地SSH
cat ~/.ssh/id_rsa.pub
```

<a name="2d096043"></a>
# 3、本地安装node.js
[下载地址](https://nodejs.org/zh-cn/)<br />

<a name="4d0c7542"></a>
# 4、本地安装hexo
[查阅文档](https://hexo.io/zh-cn/docs/)<br />安装完node.js之后,我们就可以安装Hexo啦，在命令行输入：
```
npm install -g hexo-cli
```

<br />局部安装 hexo 包，在命令行输入：
```
npm install hexo
```


<a name="5b58a060"></a>
# 5、git clone 到本地
clone 远程仓库dev分支的代码到本地
```
git clone -b dev 仓库地址
```

