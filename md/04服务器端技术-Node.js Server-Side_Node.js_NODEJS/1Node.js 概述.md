# Node.JS 概述

---

## 什么是 Node.js

  * 什么是JavaScript？
    * 1995年Netscape公司推出，后经ECMA统一标准的脚本语言。通常狭义上理解的JS是指在浏览器内置的JS解释器中运行的，主要用途是操作网页内容，实现用户交互。
  * 什么是 Node.js？
    * 2009年由Ryan Dahl开发，现由Node.js Foundation维护，基于Google V8引擎的JS运行时环境，其运行完全脱离浏览器，可以编写独立的服务器端程序。主要用途为文件读写、网络访问、加密压缩、数据库操作等等。
    * 官方网站：www.nodejs.org
    * 中文镜像网站：www.nodejs.cn

    >终于有一门语言既可以编写客户端应用，又可以编写服务端应用了！！一种语法统一前后端！！！

## Node.js 与 JavaScript

  JavaScript|Node.js
  ---|---
  客户端技术，运行于浏览器中| 服务端术，与PHP、JSP等是类似的技术
  有多种解释器可以使用，如IE的Chakra、FF的猴子系列、Chrome的V8等等| 只能运行于基于V引擎改进而来的运行时环境
  因为解释器有多种，所以存在代码兼容性题| 只有一种解释器，所以不存在代码兼性问题
  支持ES对象、自定义对象、BOM&DOM对象|支持ES对象、自定义对象、Node.js扩展象
  主要用于网页DOM元素的操作，实现用户互效果|主要用于实现服务端运行逻辑，文件系统操作、数据库访问、其他服务器用等
  
## 安装 Node.js

  * 官网：https://www.nodejs.org，下载对应版本
    * LTS:Long Term Supprt
    * Current
  * 手册网址：https://nodejs.org/api/
    安装后测试
  * 安装后测试
  
## 运行 Node.js

  * 交互模式（REFL 模式）
    * Read-Evaluate-Print-Loop
    * 读取用户输入，执行运算，输出执行结果，继续下一次循环
    * 交互模式下，Node.js自带的模块无需引入

  * 脚本模式
    * 将所有语句编写在独立的脚本文件中，一次性执行
    * 脚本模式下，除了全局对象及其相关成员外，所有其它模块中声明的对象和方法必须使用 require()引入

### 运行 Node.js

  * 安装 Node.js
  * 命令行方式下，两种方式运行 Node.js
    * 测试简单语句
    * 测试对象

# 使用 Node.js

---
  
## Node.js 体系结构
  
## Node.js 语法概述

  * Node.js 语法是完全基于JavaScript的，下列内容与 JS是完全一样的：
  * 数据类型
  * 声明变量和常量
  * 运算符
  * 逻辑结构
  * 函数作用域和闭包
  * 对象和原型
  * 对象分类

    >语法上，客户端 JS 和 Node.js 的最大不同点体现在有解释器所提供的扩展对象上

## 数据类型

  * 原始类型（Primitive Type）
    * string、number、boolean、null、undefined
  * 引用类型（Reference Type）
    * ES核心对象：Global、String、Number、Boolean、Date、Math、Array、Error、Function、Object、RegExp
    * Node.js对象：Buffer、ReadStream、ClientRequest...
    * 自定义对象
      >Node.js 中不支持任何 BOM 对象，如window、document... 也不支持任何 DOM 对象，如 Element、Image、TableRow...

### 第一个 Node.js 应用

  * 创建并测试 Node.js 应用
  
## Node.js 的特点

  * 简单，避免过度设计
  * 单线程逻辑处理
  * 非阻塞的异步I/O处理
  * 事件驱动编程
  * 无锁机制，不会产生死锁
  * 支持数万个并发连接
  * Node.js适合搭建以IO操作为主、响应速度快、易于扩展的网络应用，例如：
    * 命令行工具  带有GUI界面的本地应用程序
    * 交互式终端工具
    * 单元测试工具
    * 基于社交网络的大规模Web应用
    * Web Socket服务器
    * TCP/UDP套接字程序
    * 客户端JavaScript编译器
  * Node.js不适合CPU密集型应用，例如：
  * 深层次的嵌套和递归
  * 复杂加密和解密算法
  * 高可靠性运算
  * 严格内存管理
  * 数据挖掘和数据分析

    >总结：
    >(1)Node.js与Java/PHP/.NET等技术属于同类，都是运行于服务器端的技术： 而与客户端JS仅仅是语法相同，功能完全不同
    >(2)Node.js适合于IO密集型的应用，而不适合于CPU密集型的应用。