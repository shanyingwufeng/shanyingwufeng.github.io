---
title: 搭建 Hexo 个人博客（多设备同步）
date: 2018-10-20 09:52:12
categories: 
- Hexo
tags:
- hexo
- study
---

安装使用 <a href="https://hexo.io/zh-cn/" target="_blank">Hexo</a> 步骤如下：

## 安装 Node.js

下载 <a href="https://nodejs.org/en/" target="_blank">Node.js</a> 直接安装。

## 安装 Git

下载 <a href="https://git-scm.com/downloads/" target="_blank">Git</a> 直接安装，安装完成后使用 Git 生成本机的 SSH Key 并添加到 Github 中（因为本地仓库和 Github 之间通过 SSH 加密传输），步骤如下：

<!-- more -->

1、打开终端输入：

```
ssh-keygen -t rsa -C "xyfaqq@163.com"
```

连续 3 次回车操作后将创建 key 存到用户目录下，目录地址一般为：当前用户目录/.ssh/id_rsa.pub中。

2、复制 id_rsa.pub 文件中的内容并添加到 <a href="https://github.com/settings/keys" target="_blank">Github</a> 的 SSH Keys 中。

3、测试密钥添加是否成功，在终端中输入：

```
ssh git@github.com
```

选择 yes 将主机持久添加到已知的 hosts 中。

再输入一次确认密钥添加成功。

```
ssh git@github.com
```

4、配置全局 name 和 email，在终端中输入以下两个命令：

```
git config --global user.name "xuyifan"
git config --global user.email "xyfaqq@163.com"
```

## 从 <a href="https://github.com/shanyingwufeng/shanyingwufeng.github.io">Github</a> 克隆 Hexo 分支

选择合适的位置克隆 Hexo 分支

```
git clone -b hexo https://github.com/shanyingwufeng/shanyingwufeng.github.io.git
```

## 安装 Hexo

```
npm install
npm install -g hexo-cli
npm install hexo-deployer-git
```

## 同步源文件到 Github 仓库

```
git add . // 添加源文件
git commit -m ‘’ // 提交
// 先拉原来分支的文件到本地进行合并
git pull origin hexo --allow-unrelated-histories
git push origin hexo
```

## 更新博客

```
hexo clean // 清除缓存，如果网页显示正常则不需要操作此命令
hexo g // 生成静态网页
hexo s // 本地部署（通过 http://localhost:4000 访问）
hexo d // 部署到 Github 仓库
```

