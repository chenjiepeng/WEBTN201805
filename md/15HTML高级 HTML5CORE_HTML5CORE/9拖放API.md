# 拖放API

---

## Web拖放

在桌面应用程序上，可以将元素从一个位置拖放到另一个位置，但在Web上，开发者没有没有一种能够实现这种操作的标准技术，从而在Web上去实现这个功能并不太容易。
在HTML5标准中引入了拖放API，从而使我们有可能开发出与桌面应用程序完全相同的Web应用程序。

## 源元素事件

在拖放API中引入了一些新的事件，其中有一些元素是由源元素（拖放的元素）触发，称之为源元素事件。另一些事件是由目标元素触发（源元素投放的事件）。
源元素事件：

* dragstart：当拖动操作开始，触发这个事件。
* drag：与mousemove事件相似，它是在源元素发生拖动时触发的。
* draged：当拖动操作结束（无论是否成功）时，源元素就会触发这个事件。

  ```js
  function initial(){
    source1=document.getElementById("image")
    source1.addEventListener('dragstart',mDragStart,false)
    source1.addEventListener('drag',mDrag,false)
    source1.addEventListener('dragend',mDragendt,false)
  }
  ```

  `<img id="image" src="img/monster3.gif"/>`

  ```js  
  function mDragStart(){
    dStart=document.getElementById('start')
    dStart.innerHTML = "Drag Start。。"}
    function mDrag(e){
      dDura=document.getElementById('dura')
      dDura.innerHTML = e.pageX + ":" + e.pageY + "<br/>"}
    function mDragend(){
      dend=document.getElementById('end')
      dend.innerHTML = "Drag end。。。"
    }
  ```

## 目标元素事件

下面是目标元素触发的事件：

* dragenter：拖放操作过程中，当鼠标指针第一次进入目标元素区域时，就会触发这个事件。
* dragover：当对象拖动到目标对象时触发。
* drop：当拖动操作在目标元素内执行投放时，目标元素会触发这个事件。
* dragleave：在拖动过程中，当被拖动对象离开目标对象时触发。
  注意：执行以上方法前，需要通过e.preventDefault()阻止默认行为。

  ```js
  function initial(){
    drop=document.getElementById("div2")
    drop=addEventListener('dragenter',mDragEnter,false)
    drop=addEventListener('dragover',mDragOver,false) drop=addEventListener('drop',mDrop,false)
    drop=addEventListener('dragleave',mDragLeave,false)
  }
  ```

  ```js  
  function mDragEnter(e){
    e.preventDefault()
    dEnter=document.getElementById('enter')
    dEnter.innerHTML="Enter first。。。"
  }
  function mDragOver(e){
    e.preventDefault()   dOver=document.getElementById('over')
    dOver.innerHTML="Moved。。。"
  }
  ```

  ```js
  function mDrop(e){
    e.preventDefault()
    dDrop=document.getElementById('drops')
    dDrops.innerHTML="Dropped。。。"
  }
  function mDragLeave(e){
    e.preventDefault()
    dLeave=document.getElementById('leave')
    dLeave.innerHTML="Element was leaved。。。"
  }
  ```

### 使用拖放事件

* 添加拖拽源对象
* 实现源对象可拖拽
* 模拟桌面图标删除功能
  
# dataTransfer对象

---

## 什么是dataTransfer对象

dataTransfer对象提供了对于预定义的剪贴板格式的访问，以便在拖放中使用。它使得自定义处理拖放操作成为可能。
可以通过dataTransfer对象保存拖放过程中各组件所涉及到的数据

## 如何获取dataTransfer对象

在HTML5中，可以通过事件参数event对象获取 dataTransfer对象
代码如下：

  ```js
  var transfer=e.dataTransfer
  function mDragStart(event){
    dStart=document.getElementById('start')
    dStart.innerHTML = "Drag Start。。。"
    event.dataTransfer.setData("Text","http;//www.tarena.com.cn")
  }
  ```

## 方法

dataTransfer对象提供了一些方法用于在源元素与目标元素中共享数据。
方法

* setData(type,data)：用于声明所发送的数据与类型
* getData(type)：返回指定type的数据
* clearData(type)：删除指定类型的数据
  type取值：
  Text：保存普通文本

```js
function mDragState(e){
  source1=document.getElementById('image')
  e.dataTransfer.setData("text",source1.src)
}
funciton mDrop(e){
  e.preventDefault()
  msg=e.dataTransfer.getData('text')
  drop.innerHTML="<img src='"+msg+"'/>" }
```

## setDragImage()

setDragImage方法用于在拖放操作过程中，修改鼠标指针所指向的图像。
语法：
event.dataTransfer.setDragImage(image,x,y)

  ```js
  function mDragStart(e){
    elem=e.target
    e.dataTransfer.setData('text',
    elem.getAttribute("id"))
    e.dataTransfer.setDragImage(e.targetimage,120,130)
  }
  ```  

### 使用 dataTransfer 对象

实现拖放效果
实现左右互移效果