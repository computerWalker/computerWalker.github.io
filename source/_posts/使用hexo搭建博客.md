---
title: 使用hexo搭建博客
date: 2019-06-08 15:42:07
tags:
---
## 准备
### 安装node.js
直接去node.js官方网站下载对应操作系统的安装包。

```bash
node -v
```
查看node版本
```bash
npm -v
```
查看npm版本
```bash
npm install hexo -g
```
安装hexo
```bash
hexo -v
```
测试hexo是否成功安装
```bash
hexo init
```
新建一个文件夹，初始化博客
```bash
npm install
```
安装所需软件（没有安装貌似也没事）
### 配置git
windows上可以安装git bash管理git
```bash
git config --global --list
```
查看本机的git全局配置
```bash
git config --global user.name "your naame"
git config --global user.email "your email"
```
配置本机git信息
```bash
ssh key-gen -t rsa -C "your email"
```
生成本机key，windows电脑默认目录：C:\Users\Administrator\\.ssh
在github设置当中，添加ssh key（自己理解：一对钥匙和锁头的关系，计算机本机有一把钥匙，在github中设置这把钥匙可以使用，有多台电脑就在每个电脑上新建一个钥匙，然后在github上设置这些钥匙可以使用）
```bash
ssh -T git@github.com
```
测试本机是否可以连上git

### 配置博客项目
#### 首先需要安装一个插件“hexo-deployer-git”
```bash
npm install hexo-deployer-git --save
```
安装插件
#### 配置_config.yml
```html
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: git@github.com:computerWalker/computerWalker.github.io.git
  branch: master
```
设置git信息
这个配置文件比较重要，一般的设置都在这个文件中，包括博客首页的信息、使用的主题等等
#### 推送代码到git库当中
```bash
hexo d -g
```
这样就配置好了基本的博客环境，在写博客时候，使用 hexo s 来预览网页效果，编辑完成后使用 hexo d -g 推送到git上，hexo会自动将文件转成网页格式，这是在外网就可以访问自己的博客了，网址就是[https:// + git 库](https://computerwalker.github.io)

## 在多台电脑上管理博客
#### 主要思路：在博客的git库当中新建一个分支：hexo
##### 将博客的源代码放在这个分支当中，并且设置hexo为默认的分支
##### 这样在其他的电脑上，只要将git库clone下来就可以编辑网页了
##### 使用hexo d -g 推送网页到git的master分支上，使用git push将源代码推送到hexo分支。
在mac电脑上实验了一下，可行的。