# WEB Worker 概述

---

## 什么是WEB Workers

Web Workers是运行在后台的JavaScript。

* 充分利用多核CPU的优势
* 对多线程支持非常好
* 不会影响页面的性能
* 不能访问Web页面和DOM API
所有主流浏览器均支持 web worker ，除了Internet Explorer

# WEB Workers API

---

## WEB Workers API

检测浏览器对 Web Worker 的支持性
创建 Web Worker 文件
创建 Web Worker 对象
与 Web Worker 进行通信

* onMessage 事件：该事件用于监听 Web Worker 传递的消息
* postMessage()方法：该方法用于 Web Worker 传递消息

终止 Web Worker

## 检测 Web Worker

在创建 Web Worker 之前，需要先检测用户的浏览器是否支持。

```js
if( typeof(Worker) !== "undefined "){
	//表示当前用户浏览器支持 Web Worker
} else {
	//表示当前用户浏览器不支持 Web Worker
}
```

## 创建 Web Worker 对象

在HTML页面中，通过 Worker 的构造器创建 Web Worker 对象
`var w = new Worker( "myworker.js" )`
  
	* Worker 的构造器接受的参数：表示指定调用的 Web Worker 文件的路径。

### 测试耗时任务

创建一个 js 文件，模拟一个耗时操作
使用 Web Worker 改进
测试 DOM操作

## Web Worker 事件

创建普通的 JS 文件，都可以用于 Web Worker 文件。
Web Worker 文件可以调用通信的事件和方法

* onMessage 事件
* postMessage()方法
  HTML页面只能通过 Worker 对象调用Web Worker 的 JS 文件

## 与 Web Worker 通信

	onMessage 事件

		```js
		w.onMessage = function( event ){
		...
		}
		```

    * 用于监听 Web Worker 传递消息，通过回调函数接受传递的消息
    * 通过回调函数的参数 data 属性可以获取传递的消息

	postMessage()方法
		w.postMessage( "worker success" )

    * 通过postMessage()方法传递消息内容

## 终止 Web Worker

	在 HTML 页面中，通过调用 Web Worker 对象的 terminate() 方法终止 Web WorkerWeb Worker。
	w.terminate()

### 使用 Web Worker

	- 实现计数器案例
	- 实现双向通信