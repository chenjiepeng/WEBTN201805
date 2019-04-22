# JavaScript 概述

---

## 什么是 JavaScript

  * JavaScipt是一种运行于**JavaScript解释器/引擎**中的解释型脚本语言
  
  * JavaScript解释器作为JS脚本的运行环境，有如下两种呈现方式

    * 独立安装的 JS 解释器——如**Node.js平台**
      服务端JS
    * 嵌入在浏览器中的 JS 解释器——如**Chrome浏览器**
      客户端JS
  * JavaScript 当前的应用领域十分广泛，例如：
    * 编写在网页中，操作网页内容，实现各种用户交互效果
    * 编写移动 App 应用
    * 编写桌面 GUI 应用
    * 编写命令行应用
    * 编写企业服务器端应用
    * 2D 绘图和 3D 游戏建模
    * Web VR
    * Web AR
    * ...
  
## JavaScript 的发展史

  * 1992年，Nombase公司为自己的CEnvi软件开发了一款脚本语言ScriptEase
  * 1995年，Netscape公司为自己的Navigator2.0浏览器开发了另一款客户端脚本语言LiveScipt，重命名为Javascript
  * 1996年，Microsoft公司在IE3.0浏览器发布了一个Javascipt的克隆版，成为JScript
  
  * 1997年，Javascript作为草案提交给ECMA，各个厂家合力推出了ECMA-262标准，定义了全新的ECMAScript标准脚本语言。各大浏览器厂家开始将ECMAScript作为实现的标准和目标
  * 2009年，CommonJS规范提出，确立了JS向服务端和桌面端应用发展的方向
  
  * CommonJS规范在传统的基于浏览器的JS API基础上，指定了更加丰富的API规范，提供了类似Java，Python，Ruby等语言的一样强大的编程能力；并实现**跨硬件平台、跨操作系统、跨解释器**的应用体验
    目前实现了CommonJS规范的技术有：Node.js、RequireJS、SeaJS等等
  
## JavaScript 的特点

  * 代码可以使用任何文本编辑工具编写，语法类似于Java和C
  * 脚本文件无需编译，由JavaScript 引擎解释执行
  * 弱类型语言
  * 基于对象
  * 跨平台性
  JS语言本身提供的数据类型和对象比较有限，其运行环境一般都扩展提供了更加丰富的编程接口
  如浏览器为JS提供了BOM对象和DOM对象
  Node.js为JS提供了网络访问，文件操作，数据库查询等功能对象
  学习不同环境下的JS注意区分