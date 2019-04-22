# 包

---

## CommonJS规范

  * JavaScript最初的设计目标是运行于客户端控制页面的交互与行为，对于实现服务端应用而言，有如下不足：
    * 没有模块系统
    * 没有标准库
    * 没有标准接口
    * 没有包管理系统
  * 由于缺少统一的标准和规范，上述问题限制了JS在服务器端更广泛深入的应用
  * CommonJS不是一门语言，而是为JS在更广范围的应用而定义的 API 标准和规范，最终提供类似于Python、Ruby、和Java语言一样丰富的功能
    * 只要遵守了这些规范，JS编写的应用就可以在任何兼容标准的解释器和主机上运行，从而使得JS可以应用于更加广泛的领域：服务器端、，命令行应用、桌面GUI应用、混合应用等等
  * Node.js实现了CommonJS规范，实现了其定义的常用API，以及模块和包的编写、使用和维护规范

## 什么是包

  * 包（package）：是在模块基础上更深一步的抽象
    * 类似于C/C++的函数库或者Java/.Net的类库
    * 将独立的功能封装起来，用于发布、更新、依赖管理和版本控制
  * Node.js 根据 CommonJS 规范实现了包机制
    * 包是一个目录
    * 包目录中包含任意的 js 文件
    * 包目录中包含一个名为 package.json 的包说明文件
      >目录式自定义模块，就是最简单的包

## 包的结构

  * 根据 CommonJS 包规范，一个包应该具有如下结构：
    * 一个package.json文件应该存在于包顶级目录下
    * 二进制文件应该包含在bin目录下
    * JavaScript代码应该包含在lib目录下
    * 文档应该在doc目录下
    * 单元测试应该在test目录下
  * Node.js 中，require()函数可以引入文件模块之外，还可以引入符合上述规范的包
  * 在调用包时，会首先检查包中 package.json 文件的main字段指定的入口文件； 如果不存在，则尝试寻找index.js 作为包的入口
    创建并使用包

### 创建并使用包

  * 创建包
  * 调用

# NPM

---

## 包管理器

  * Node.js官方提供了几十个核心模块，但是很多情况下功能仍然不够，很多个人和企业提供了大量的第三方模块供我们的应用程序使用，统一放在了 npmjs.com上

  * 包管理器（Node Package Manager，简称NPM）是Node.js提供的包管理工具，用于下载、安装、升级和删除包，或者发布并维护包

  * 使用 npm install 命令可以下载并安装一个包
    * 安装包将保存在./node_modules 下（运行 npm 命令时所在的目录）
    * 可以通过 require()来引入本地安装的包
      `npm install 包名`
  * 使用 require()引入包名时，参数是包的目录名； 要求包对应的目录处于 node_modules 目录下，其根目录下存在 package.json 文件，其内容格式满足CommonJS Pachages/1.1 规范

## 常用包

  * 常用的包

    包名|说明
    ---|---  
    colors| 命令行彩色输出
    evet-stream| Stream流操作工具
    mocha| 单元测试
    mysql| 连接MySQL
    request| HTTP客户端
    restify| REST API搭建
    socket.io| WebSocket实时通信
    xml2js| XML转换工具