# 组件生命周期

---

## 声明周期状态

  * 自定义组件（ReactCompositeComponent）的生命周期主要通过三种状态进行管理，它们负责通知组件当前所处的状态，应该执行生命周期中的哪个步骤，是否可以更新 state。

  * 三种状态如下：
    Mounting 已经插入真实DOM
    Updating 正在被重新渲染
    Unmounting 已经移出DOM

## 处理方法

  * 插入相关方法
    * componentWillMount() 准备插入
    * componentDidlMount() 已经插入

  * 更新相关方法
    * componentWillUpdate(object nextProps,object nextState) 准备更新
    * componentDidUpdate(object prevProps,object prevSate) 已经更新

  * 删除相关方法
    * componentWillUnmount() 准备从DOM中移除。

## 使用组件生命周期方法

  * 之前学习ref时提到过吗，ref的使用必须等到组件插入到真实的DOM节点之后，才能使用；
  接下来在组件中通过componentWillMount以及componentDidMount方法，在其中分别通过console将组件中的属性显示出来

  * 分析：
    * 组件构成：一个h1标签，指定ref
    * 实现生命周期方法：通过ref找到h1，直接打印出来，验证这个对象是否可用

# 事件处理

---

## 事件系统

  * React 标准化了事件对象，因此在不同的浏览器中都会有相同的属性。
    * 组件createClass后创建的是许多方法组成的对象。

  * 组件中使用的方法分别为React自有的方法与用户自定义的方法：
    * React自有方法是组件生命周期中的方法，如：render、componentWillUpdate、componentDidMount等
    * 用户自定义的方法可以起符合JS命名规范的方法就可以（最好使用驼峰命名），如：handleClick、handleChange、handleMouseover等。

## 常用事件

  * 鼠标类
    * onClick/onContextMenu/onDoubleClick
    * onMouseDown/onMouseEnter/onMouseLeave
    * onMouseMove/onMouseOut/onMouseOver
    * onMouseUp

  * 拖拽类
    * onDrop/onDrag/onDragEnd/onDragEnter
    * onDragExit/onDragLeave/onDragOver/onDragStart

  * 触摸（只在移动端有效）
    * onTouchCancel/onTouchEnd
    * onTouchMove/onTouchStart
  * 键盘
    * onKeyDown/onKeyPress/onKeyUp
  * 剪切类
    * onCopy/onCut/onPaste
  * 焦点事件
    * onFocus/onBlur
  * 组成事件
    * onCompositionEnd/onCompositionStart
    * onCompositionUpdate
    * ...

### 使用事件处理

  * 练习使用click、change、mouseEnter、mouseLeave事件

  * 分析
    * 组件构成：button、input
    * 功能：点击button，获取input内容；同时通过change事件监听input输入的内容，并在鼠标移入/出button时通过console打印到控制台

# state

---

## state

  * 组件免不了要与用户互动，React的一大创新，就是将组件看成一个状态机，一开始就有一个初始状态，然后用户互动，导致状态变化，从而触发重新渲染UI。

  * 具体实现起来，React里有个state，只要更新组件的state，然后根据state重新渲染用户界面（不要操作DOM），React来决定如何最高效的更新DOM。
  * 注意事项：
  * 在React中设置class是：
    * 不能直接class= "centerBox"
    * 而要写成className= "centerBox"
  * 在React中设置样式时：
    * 不能直接 style="opacity:{this.state.opacity}"
    * 而要写成style={{opacity:this.state.opacity}}

## 常用方法

  * 方法1：getInitialState 定义初始状态，也就是一个对象
  * 方法2：this.state.** 可以获取getInitialState中定义的对象；如果需要修改状态值，可以调用setState，每次修改后，都将自动调用this.render方法，从而实现组件的渲染

### 使用state

  * 使用state，实现如下功能：
    在组件中指定一个div，对这个div绑定绑定wheel（鼠标滚动事件），实现鼠标滚动，随机修改div的颜色

  * 分析：
    * 组件构成：一个div
    * 状态：初始化一个state为背景色，在div中指定背景色为 状态值
    * 时间绑定：对div指定onWheel事件，在回调函数中修改state（状态为颜色值），

# 表单

---

## 表单

  * 状态属性
    * value，对应`<input>`和 `<textarea>` 所有
    * checked，对应类型 checkbox 和 radio 的 `<input>` 所有
    * selected，对应`<option>`所有
  * 对于设置了上面提到的对应“状态属性”值的表单元素就是受控表单组件

    ```html
    render:function(){
      return <input type="text" value="hello"/>
    }
    ```

## 受控组件

  * 一个受控的表单组件，它所有状态属性更改涉及 UI 的变更都由 React 来控制（状态属性绑定 UI）

  * 使用这种模式非常容易实现类似对用户输入的验证，或者对用户交互做额外的处理

## 非受控组件

  * 和受控组件相对，如果表单元素没有设置自己的“状态属性”，或者属性值设置为 null，这时候就是非受控组件。

### 使用表单

  * 使用表单实现如下页面，并在点击提交按钮时，通过console将所有信息输出

# 虚拟DOM算法简析

---

## 虚拟DOM算法简析

  * 步骤1：用JavaScript 对象结构表示 DOM 树的结构；然后用这个树构建一个真正的 DOM 树，插到文档当中

  * 步骤2：当状态变更的时候，重新构造一棵新的对象树。然后用新的树和旧的树进行比较，记录两棵树差异

  * 步骤3：把2所记录的差异应用到步骤1所构建的真正的DOM树上，视图就更新了