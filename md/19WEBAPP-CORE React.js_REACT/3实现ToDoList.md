# 实现ToDoList

---

## 实现ToDoList

  * 结合React组件的核心思想以及各个知识点，实现一个经典的综合项目ToDoList，效果如下图：

    输入内容，点击add按钮会在待做列表中添加所输入数据

    删除按钮，点击即将该行删除

    此内容为之前所添加的信息

    实时显示上述列表的总数

## 需求分析

  * 1、拥有输入框、列表和统计信息
  * 2、可以增加Todos 条目
  * 3、可以删除指定Todos 条目
  * 4、自动刷新列表和统计信息

## 概要设计

  * 考虑到使用React来实现，可以充分利用“复用组件”的特性，将整个小应用，进行组件化，比如：

    ToDoBox
      ToDoInput
      ToDoList
        ToDoItem

## 详细设计之搭建原型

  * 整体模块起名为：ToDoBox
    * 在 ToDoBox 中，有两部分构成，分别如下：
      * 输入区域：ToDoInput
      * 列表区域：ToDoList 该列表有两部分构成，分别为各个ToDoItem，以及一个总数显示区域
  
  * 将应用进行组件化，首先先讲原型搭建起来，也就是去通过createClass方法去创建各个组件，然后拼接成一个复合组件

    ```react
    var ToDoBox = React.createClass({
      render:function(){
        return(
          <div>
            <ToDoInput/>
            <ToDoList/>
          </div>
        )
      }
    })
    var ToDoInput = React.createClass({
      render:function(){
        return(
          <div>
            <input placeholder='请输入'/>
            <button>add</button>
          </div>
        )
      }
    })
    var ToDoList = React.createClass({
      render:function(){
        return(
          <div>
            <ul>
              <ToDoItem/>
              <ToDoItem/>
            </ul>
            <span>当前待做事项3</span>
          </div>
        )
      }
    })
    var ToDoItem = React.createClass({
      render:function(){
        return(
          <div>
            <button>删除</button>
            <span>Hello React</span>
          </div>
        )
      }
    })
    ```

## 详细设计之数据处理

  * 数据可以直接通信吗？
    * 输入添加数据后，我们需要在ToDoInput模块中进行，而添加成功后，我们需要在ToDoList中显示，这是两个平级的模块，并不能进行相互间的通信。

  * 数据处理方案：
    * state是一个模块的状态信息，存储一个模块的运行数据，在程序运行时，可能会随时改变其中某项的值；
    * props 则是通过父元素传递而来，属于模块的属性信息，不能进行修改。
  * React中，组件通信多通过state来实现，所以在复合组件中需要将state指定好；
  * 这里由于业务数据是一个列表，所以可以考虑将state初始化为一个数组，这样所谓的数据add/delete，都是围绕着状态中的数组进行操作。
  * 当然如果要将数组中的数据显示在ToDoList中，还需要通过props进行值或者方法的传递。
  * 增加数据逻辑
    * ToDoInput模块中点击“Add”按钮后，把item 数据传递给父模块（ToDoBox），父模块接收到这条数据后，再将其传递给ToDoList，由其更新list里面的数据

  * 删除数据的逻辑
    * 从父元素传递到ToDoList，然后由ToDoList传递给ToDoItem，这样，在ToDoItem 中点击特定item的delete按钮后，就能通过这个方法一层一层传递给父元素，从而通过父元素更新state，用来刷新列表。