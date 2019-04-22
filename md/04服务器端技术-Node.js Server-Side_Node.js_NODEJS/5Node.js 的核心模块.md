# 工具模块

---
  
## QueryString

  * Query String 模块提供了处理 URL 中的查询字符串部分的相关操作

    ```js
    const querystring = require('querystring')
    从查询字符串中解析出数据对象 querystring.parse
    将数据对象转换为查询字符串 querystring.stringify
  URL
    URL 模块提供了处理 URL 中不同部分的相关操作
    解析出URL中的各组成部分 url.parse
    将查询字符串解析为对象 url.format
  测试常用工具模块
  Path
  Util
FS 模块
  FS 模块概述
    fs 模块是 Node.js 核心模块之一，提供了文件的读写、更名、删除、遍历目录等操作
    操作有同步和异步两种形式
      在I/O 操作密集的应用中，推荐使用异步调用方式，以避免整个处理进程的阻塞
    常用class
      fs.Stats：文件或目录的统计信息描述对象
      fs.ReadStream：stream.Readable 接口的实现对象
      fs.WriteStream：stream.Writable接口的实现对象
      fs.FSWatcher：可用于监视文件修改的文件监视器对象
    常用方法
      fs.mkdir()：创建目录
      fs.rmdir()：删除目录
      fs.readFile()：读取文件内容
      fs.writeFile()：向文件中写出内容
      fs.appendFile()：向文件中追加内容
      fs.unlink()：删除文件
      fs.rename()：重命名文件
  文件信息统计
    fs.stat()和 fs.statSync 方法用于返回一个文件或目录的统计信息对象（fs.Stats 类型）
    fs.Stats 对象方法可用于检查文件的物理特性，比如
      stats.isFile()：是否为文件
      stats.isDirectory()：是否为目录
  操作目录
    操作目录的常用方法
      fs.mkdir(path[,mode],callback)：创建指定目录
      fs.rmdir(path,callback)：删除指定目录
      fs.readdir(path[,options],callback)：读取目录下内容
  读写文件
    对于数据量不是很大的文件，可以一次性的读写其中的全部内容
      fs.readFile(file[,option],callback)：读取文件内容
    写文件时，若目标文件1不存在，则writeFile 方法会自动创建该文件；若目标文件存在，则方法会覆盖愿所有内容
      fs.wrtieFile(file,data[,options],callback)：写出内容
    向文件中追加内容时，如果目标文件不存在，则appendFile 方法会自动创建该文件； 若目标文件存在，该方法会在原有内容后面追加新内容
      fs.appendFile(fiel,data[,options],callback)：追加内容
  使用 FS 模块
    使用 FS 模块
      读取文件
      写入文件
      追加内容
HTTP 模块
  HTTP 协议
    HTTP 协议概述
      浏览器与Web服务器之间的通信消息格式遵守HTPP协议 它是典型的基于“请求-响应”模型的协议，只有客户端发出了请求消息，服务器才会给出响应消息，并且一个请求消息只会得到一个响应消息
    请求消息
      请求消息是客户端构建。发送给Web服务器的消息
      一个请求消息由四部分构成：
        请求起始行
        请求头部
        CRLF
        请求主体（可能没有）
    请求方法
      请求起始行中的请求方法描述了当前请求的目的
      常见的请求方法有：
        GET：表示客户端想“获取”服务器上的指定资源
        POST：表示客户端想向服务器“传递并保存”数据
        PUT：一般用于表示客户端想向服务器“传递并更新”数据
        DELETE：一般表示客户端想从服务器“删除”指定数据
      只有 POST 和 PUT 请求才能有请求主体
      HTML表单只能使用发起 GET 和 POST 请求 XHR 对象可以发起任意的 HTTP 请求
    响应消息
      响应消息是Web服务器根据客户端的请求，返回给客户端的消息
      一个响应消息由四部分构成：
        响应起始行
        响应头部
        CRLF
        响应主体（可能没有）
    响应状态码
      响应起始行中的响应状态码用于标识响应消息的状态，可能有如下五类可能：
        1xx：请求-响应继续进行
        2xx：成功的响应
        3xx：响应重定向到其它地址
        4xx：客户端请求错误
        5xx：服务器端运行错误
    观察请求消息和响应消息
  HTTP 模块
    HTTP 模块概述
      Node.js 内置的 HTTP 模块提供了一种非常底层的方法，用于创建使用 HTTP 协议的客户端应用或者服务器端应用
      具体用途可以分为：
        创建并发起请求消息，等待并解析响应消息——实现Web 客户端
        接受并解析请求消息，构建并发送响应消息——实现Web 服务器
    HTTP 客户端
      http.request 是一个客户端工具，用于向 HTTP 服务器发起请求消息，实现访问
        可以模拟浏览器向任意的 Web 服务器发起 HTTP 请求消息，并获取该站点返回的响应数据
      上述方法返回一个 http.ClientRequest 对象，用以描述一个 HTTP 请求消息
        其中的参数 options 可以指定请求消息起始行和请求消息头部
      创建一个 HTTP 请求头消息对象 http.request
      创建一个 HTTP GET 请求消息对象 http.get
      ClientRequest 常用方法：
        write(chunk)：向服务器追加请求主体数据
        end(chunk)：提交请求消息主体结束
        setTimeout(time,fn)：设置请求消息超时时间
        abort()：终止请求
      ClientRequest 常用事件：
        response：接受到响应消息
        abort：请求终止事件
        error：请求发生错误
    HTTP 服务器
      http.server 是一个基于事件的 HTTP 服务器，其核心由Node.js 下层 C++ 部分实现，接口由 JS 封装，兼顾了高性能与易用性
        用于创建一个非常底层的 Web 服务器应用，用以接受客户端请求消息，并返回响应消息，提供 Web 内容服务
        上述方法返回一个 http.Server 类型的对象，用以描述当前所创建的Web服务器
        创建一个基于 HTTP 协议的 Web 服务器 http.createServer
      http.Server 常用方法：
        listen(port,[host])：监听指定的服务端口
        close()：停止服务器的运行
        setTimeout(timeout,fn)：设置服务器响应消息超时时间
      http.Server 常用事件：
        connection：出现客户端连接
        request：接收到请求消息
        close：服务器停止事件
        error：响应过程发生错误
      使用 createServer 时
        可以使用一个可选参数：参数为一个回调函数
        如果不用参数，则监听该方法创建对象的 request 事件
      Server 对象的 response 事件回调函数中
        第一个参数是一个 IncomingMessage对象，封装着客户端提交的请求消息数据
        第二个参数是一个 ServerResponse对象，用于构建向客户端输出的响应消息数据