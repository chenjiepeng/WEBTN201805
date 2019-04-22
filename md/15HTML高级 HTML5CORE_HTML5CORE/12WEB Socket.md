# Web Socket 概述

## Web Socket 是什么

Web Socket是HTML 5 提供的在Web应用程序中客户端与服务端之间进行的非HTTP的通信机制。

Web Socket实现了用HTTP不容易实现的服务器端的数据推送等智能通讯技术。

## Web Socket 的特点

Web Socket可以在服务端与客户端之间建立一个非HTTP的双向连接。
-这个连接是实时的，也是永久的。
-服务端可以主动推送消息。
-服务端不再需要轮询客户端的请求。
-服务器端与客户端之间通信无需重新建立连接。
  
# Web Socket API

---

## Web Socket 对象

调用 Web Socket 对象的构造器来建立与服务器之间的通信连接：
var websocket = new WebSocket("ws://localhost:8005/socket")

    - URL字符串必须以”ws“ 或 ”wss“（加密通信）文字作为开头。
    - 客户端可以通过 WebSocket 这个 URL 字符串重新获取连接。

## Web Socket 方法

使用 WebSocket 对象的 send()方法对服务器发送数据：
webSocket.send("data")

- send()方法只能发送文本数据。
- 使用 JSON 对象把任何 JavaScript 对象转换为文本数据后进行发送。
  
通过 WebSocket 对象的 close()方法来关闭socket，切断通信连接：
    webSocket.close()

## Web Socket 事件

通过获取 onmessage 事件来接收服务器传来的数据：

```js
webSocket.onmessage = function(event){     var data = event.data
}
```

通过获取 onopen 事件来监听 socket 的打开事件：

```js
webSocket.onopen = function(event){
    //开始通信时的处理
}
```

通过获取 onclose 事件来监听 socket 的关闭事件：

```js
webSocket.onclose = function(event){
    //通信结束时的处理
}
```

## readyState 属性

通过读取 readyState 的属性值来获取 WebSocket 对象的状态。

readyState 属性存在以下几种属性值：
-CONNECTING（数字值为0），表示正在连接。
-OPEN（数字值为1），表示已建立连接。
-CLOSING（数字值为2），表示正在关闭连接。
-CLOSED（数字值为2），表示已关闭连接。
  
# Web Socket 示例

## Web Socket 示例概述

在服务端指定使用的 socket 用程序，并在服务端指定该 socket 应用程序的主机与端口

编写在客户端使用的Web Socket 实现与服务器端进行连接并收发消息。

## WEB Socket 示例代码

Web Socket 客户端页面关键代码：

```js
<h1>Websocket客户端示例</h1>
<div id="message"></div>
<p>请输入一些文字：</p>
<input id="text" type="text"></input> <button id="connect" onclick="connect()">建立连接</button>
<button id="send" onclick="send">发送数据</button>
<button id="disconnect" onclick="disconnect()">断开连接</button>
```

Web Socket 客户端JavaScript关键代码，connect()方法：

```js
function connect(){
    webSocket = new webSocket(host)   webSocket.onopen = function(){
        ...
    }
    webSocket.onmessage = function(event){
        ...
    }
    webSocket.onclose = function(){
        ...
    }
}
```

Web Socket 客户端JavaScript关键代码，send()方法：

```js
function send(){
    var text = ...
    var message = ...
    if(text==""){
        ...
        return
    }
    webSocket.send(text)
    ...
}
```

Web Socket 客户端JavaScript关键代码，disconnect()方法：

```js
function disconnec(){
    webSocket.close()
}
```

### 实现聊天客室户端

- 利用 Web Scocket 实现聊天室的客户端