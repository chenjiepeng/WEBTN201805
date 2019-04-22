# 全局对象

---

## 全局对象概述

  * 全局对象（Global Object），它及所有属性都可以在程序的任何地方访问，及全局变量

  * 嵌入在浏览器中的V8引擎，支持ES原生对象、BOM和DOM对象，全局对象称为 **window**
    * 声明全局全局作用域的变量和函数默认为window对象的成员——全局对象污染
  * Node.js 中的全局对象是 **global** ，所有全局变量都是global 对象的属性
    * 独立的Node.js环境中，不支持BOM和DOM对象

## global

  * global 作为全局变量的宿主
    * 在交互模式下声明的“全局变量和函数”都是global对象的成员——全局对象污染
    * 在脚本模式下声明的“全局变量和函数”不是global对象的成员——避免了全局对象污染
      >脚本模式下，每个.js文件都是一个独立的模块对象，其中创建的“全局变量和函数”都是该对象构造方法内的局部成员

## console

  * Node.js 中的 console 模块提供了一种控制台调试输出机制，类似于 Chrome 浏览器中 console 对象的功能
    * 用于向标准输出流（stdout）或标准错误流（stderr）输出字符
  * 常用方法
    * log
    * info
    * error
    * warn
    * time
    * timeEnd

## process

  * 当操作系统启动一个程序时，会将必需的可执行文件和数据文件从文件系统调入内存，分配必需的内存空间，执行其中的代码——称为创建了一个**执行进程**
    * 全局对象 global.process 就是这个进程的代码表示
    * 可以使用process对象获取当前操作系统及运行时信息，并操作脚本所在执行进程，如杀死进程等

    >Windows系统中的“任务管理器”记录的就是当前系统中所有正在运行的进程；每个Node.js进程也同样记录在其中。

  process对象具有如下一些常用的成员：

    ```js
    arch
    platform
    env
    
    cwd
    exePath
    versions
    uptime
    memoryUsage
    
    pid
    process.kill(pid)
    ```

## Buffer

  * Buffer：缓冲区，指一块专用于存储数据的内存区域，可用于存储读写的文件数据、网络上要传输的数据等等
  * Buffer对象的实例，可以直接构造，也可以通过数据读写获得
  * Buffer实例中，不仅能存储字符数据，也可以存储二进制的字节数据

    >Buffer中存储的数据可能很大，所以不是分配在解释器进程的堆内存中，而是直接分配在操作系统内存中
    >注意：不同版本的Node.js中，Buffer对象的API变化比较大，请参考当前版本的Node.js手册

# 全局函数

---

## 定时器

  * Node.js 提供了四种形式的定时器
    * global.stTimeout()：一次性定时器
    * global.setInterval()：周期性定时器
    * process.nextTick()：本次事件循环结束时立即执行的定时器
    * global.setImmediate()：下次事件循环立即执行的定时器
      >客户端 JS 中只支持 setTimeout() 和 setInterval() 两组函数

## 一次性定时器

  * 一次性定时器：在一个设定的时间间隔之后执行指定任务，而不是在函数被调用后立即执行

  * setTimeout()(func,delay)：创建一次性定时器
    * func：：要执行的任务
    * delay：间隔时间，单位为毫秒
    * 返回已经启动的定时器对象
  * clearTimeout(timerObj)：停止启动的定时器
    * timerObj：启动的定时器对象
  
## 周期性定时器

  * 周期性定时器：每间隔指定的时间间隔之后就执行一次指定的任务
  
  * setInterval(func,delay)：创建周期性定时器
    * func：：要执行的任务
    * delay：间隔时间，单位为毫秒
    * 返回已经启动的定时器对象
  * clearInterval(timerObj)：停止启动的定时器
    * timerObj：启动的定时器对象

### 使用全局函数

  * 使用定时器

## 其他常用全局函数

  |函数名   |说明   |
  |---|---|
  |decodeURI()   |解码一个编码的 URI   |
  |decodeURIComponent()|解码一个编码的 URI组件|
  encodeURI()|把字符串编码为 URI
  |encodeURIComponent()|把字符串编码为 URI组件|
  |escape()|对字符串进行编码
  |unescape()|对由escape()编码的字符串进行解码
  |parseInt()|解析一个字符串并返回一个整数|
  |parseFloat|解析一个字符串并返回一个浮点数|
  |isNaN()|检查是否为NaN|
  |isFinite()|检查是否为有穷大的数字|
  |eval()|计算并执行以字符串表示的  JavaScript代码。