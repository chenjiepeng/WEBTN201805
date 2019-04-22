# Ionic 概述

---

## 概述

  * Ionic：一个完全开源的 HTML5 应用程序开发框架，
  可以使用 Web 技术，比如 HTML、 CSS 和 Javasript 构
  建接近原生体验的移动应用程序。
  * Ionic是构建在Angular和Apache Cordova之上的。
  * 为什么选择Ionic
    * 开源且免费
    * 构建在angular、cordova之上
    * 接近于原生体验
    * 社区活跃
  * 注意事项
    * Ionic是一个轻量的手机UI库，具有速度快、界面现代化、
    美观等特点。为了解决其他一些UI库在手机上运行缓慢的
    问题，它直接放弃了IOS6和Android4.1以下的版本支持，
    来获取更好的使用体验。
  
  Ionic应用开发整体示意图：

## Ionic 特点

  * 完美融合AngularJS
  * 专注原生，结合cordova可以调用底层硬件
  * 设计风格漂亮
  * 提供强大的命令行操作
  * 性能优越，运行速度快

# 环境搭建

---

## 搭建Ionic开发环境

  * 步骤1 安装Node
    * nodejs.org官网下载并安装最新版本安装包
  * 步骤2 通过命令行安装cordova
    * npm install -g cordova
  * 步骤3 全局安装ionic
    * npm install -g ionic
  * 步骤4 创建Ionic工程
    * ionic start appName
  * 查看安装结果
    * Ionic-info
  * 启动项目
    * ionic serve

## Ionic 常用指令

  * Ionic常用指令

## Ionic 工程目录结构

  * 工程主要目录结构介绍
    * config.xml 当前app配置信息
    * src 把精力放到这，编写主要业务逻辑的地方
    * node_modules 根据package.json安装的包
    * platforms 支持的平台
    * plugins 存储cordova的插件
    * resources 存储资源，比如icon和图片

### 使用 Ionic

  * 1、搭建 Ionic 的开发环境
  * 2、熟悉工程目录结构
  * 3、创建 Hello World