# Cookie

---

## 什么是Cookie

  Cookie 是由服务器生成并存储在客户端文件系统（.txt格式）中的key/value对。当浏览器再次请求该站点上的页面时，就会把保存的Cookie发回服务器。

  Cookie使得浏览器可以在访问同一个站点的不同请求间传递数据，让服务器程序识别不同的客户端

  典型应用：保存用户登陆状态、跟踪用户行为、页面定制、保存购物车等需要保存全局变量的场合
    出于隐私保护的考虑，浏览器可以选择禁用Cooie，或者手动删除

## Cookie 的存放

Cookie保存在客户端某个特定的目录下的一个.txt文本文件中，且不同站点的Cookie数据保存不同的文件中
Cookie数据一般都是加密后保存的

## 有效期和作用域

有效期：Cookie可以指定一个expires值，定义其生存周期，在这个周期内Cookie有效，超出周期Cookie就会被清除。有些页面将Cookie的生存周期设置为“0”或负值，这样在关闭浏览器时，马上就清除Cookie，不会记录用户信息，更加安全。

作用域：默认情况下，某个站点保存的Cookie只能自己访问，不能被其它站点使用。但可以设置Cookie的domain和path值，限定哪个域名下的哪些路径可以访问此Cookie
  “广告联盟”是个亟待规范的问题

## 保存 Cookie

  Cookie可以由服务端程序（如Java、PHP等）创建并发送给客户端保存；也可以由客户端JavaScript脚本创建并保存

  ```js
  //保存一个简单Cookie
  document.cookie='uname=tom'
  //保存一个内容复杂的Cookie
  document.cookie='msg='+
  encodeURIComponent('Hi, JS 你好')
  //保存一个具有指定超时时间的Cookie
  document.cookie='uid=7788;expires='+
  new Date().toGMTString()
  ```

    Cookie键值中不能包含分号，逗号，等
    号，空格，同时为了防止中文乱码问题，
    键值应该用encodeURIComponent()
    函数进行编码  

    上述三行语句可以创建并保存
    三个Cookie，而不是只有一个！

## 读取 Cookie

  可以使用document.cookie获取当前站点可以读取的所有Cookie（多个Cookie间用;分隔）

  ```js
  var cookies = documen.cookie
  console.log(cookies)        //多个Cookie用;分割
  var arr = cookies.split(';')
  for(var i=0;i<arr.length;i++){
    var cookie = arr[i]      //键值对用=分割
    var cookiePair = cookie.split('=')  
    console.log(cookiePair[0] +'='+ cookiePair[1])
  }
  ```

    注意cookie键名中可能会被浏览器
    添加的空白字符，需要trim()操作

## Cookie 的生命周期

若没有指定expires属性，创建的Cookie其实只是保存在内存中，浏览器一关闭也就被销毁了

可以在保存Cookie时使用expires指定其生存周期

  ```js
  document.cookie='uid=7788'//单会话Cookie
  var time = new Date().getTime() + 1000*3600*24*30
  var exp = new Date(time)
  docunment.cookie='uname=tom;expires='+ exp.toGMTString()       //30天后失效的Cookie
  ```

    同理，可以把expireshe设置为一个过去的
    时间，就可以实现删除Cookie的效果

### 使用 Cookie

实现“两周内不再登陆”的功能
  
# 两个存储系统

---

## 两个存储系统

万维网最初的设想，是作为展示信息的一种方式。信息处理时后来才出现的，但Web的实质并没有变——信息在服务器上处理，然后显示给用户。因为系统没有利用用户计算机资源，所以复杂操作都是在服务器上完成的。

对于任何程序来说，能够实现数据存储是必备功能之一，并且在需要的时候能够提供数据。但在过去的Web用户端，没有能够支持数据存储的有效机制。

cookie曾用来在客户端存储少量信息，但受其性质所限，cookie只能存储一些短的字符串

在HTML5中提供了Web存储API，它是在cookie之上的增强。这个API允许我们在用户的硬盘上存储数据，并在日后使用这些数据。

这个API可以分成两个部分：
  信息必须且只在会话过程中使用——sessionStorage
  信息必须长期保存且由用户决定时长——localStorge
  
# sessionStorage

---

## 什么是sessionStorage

sessionStorage这部分API就像是会话cookie的替代。cookie以及sessionStorage都是在特定的时间段内保持数据可用。但cookie使用浏览器作为引用，而sessionStorage使用单个窗口作为引用，这就意味着，窗口关闭之后，sessionStorage就不能再使用。

## 创建数据

  sessionStorage和localStorage都将数据存储为项。项采用键/值对的组合格式。

  语法：
  setItem(key,value)：用键和值创建项。如果键已经存在，则更新值，所以也可以用这个方法更新值。
  getItem(key)：指定要获取的项的键，根据键得到对应的值。
  //设置数据
  sessionStorage.setItem('uname','Naruto')
  //读取数据
  var name=sessionStorage.getItem('uanme')

## 读取数据

  API提供了更多的方法和属性来操作项，使得代码变得更有用。
  
  属性：
    - length：返回应用程序在存储空间中积累的项的数量。
  
  方法：
    - key(index)：获取指定索引对应的项的键

    ```js
    var len=sessionStorage.length
    for(var i=0;i<len;i++){
      var key=sessionStorage.key(i)
      alert(sessionStoarage.key(i))
    }
    ```

## 删除数据

API中提供了两个方法可以删除项
  -removeItem(key)：根据项的键删除指定项。
  -clear()：清空整个存储空间。每个项都被删除。

  ```js
  sessionStorage.removeItem('uname')
  sessionStorage.clean()
  alert(sessionStorage.length)
  ```

### 使用 sessionStorage 保存并读取数据
  
  -创建登录页，记载用户信息
  -其他页面读取用户信息
  
# localStorage

---

## 什么是localStorage

在窗口会话期间有一个可靠的系统来存数据，在某些情况下可能有用。但是，想在Web上模拟强大的桌面应用程序，则一个临时的数据存储系统就不够用。

为了解决这个问题，API提供了另外一个系统，为每个来源保留一存储空间，并保持信息持久可用——localStorage。

利用localStorage，可以保存大量数据，并由用户决定信息是否有用，是否保留。

localStorage与sessionStorage拥有相同的接口，所以sessionStorage的方法和属性对于local Storage同样有效。

## storage事件

由于localStorage向加载同一程序是打开的每个窗口都提供信息，所以产生了至少两个问题
  -各个窗口间如何通信
  -如何更新当前没有活动或没有得到焦点的窗口信息

为解决以上两个问题：API中提供了storage事件。

storage事件：存储空间每次发生变化时，都会触发这个事件。所以可以通过这个事件通知同一程序的每个窗口。

语法：
  -window.addEventListener('storage',upadteNum,false)

### 简单Web留言本

  该Web留言本具有新建、保存、修改、删除及全部删除功能
    - 新建功能：新建一个留言内容
    - 保存功能：将编辑的留言内容保存到localStorage，并读取所有留言内容
    - 修改功能：在读取的所有留言内容中，选择需要修改的留言，点击【修改】按钮进行修改
    -  删除功能：在读取的所有留言内容中，选择需要删除的留言，点击【删除】按钮进行删除
    -  全部删除功能：删除之前已保存的所有留言内容