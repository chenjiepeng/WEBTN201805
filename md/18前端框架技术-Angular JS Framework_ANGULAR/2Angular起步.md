# Angular概述

---

## 什么是Angular

  * Angular诞生于2009年
  * 由Misko Hevery 等人创建
  * 后为Google所收购

  * Angular 是一个 JavaScript 框架
  * 致力于开发单页面应用程序（Single Page Application）
  * 易于构建页面CRUD操作
  * 基本操作思路与DOM及jQuery的“先查找元素再操作元素”不同——**“创建数据、绑定数据、修改数据、更新数据”**——一切操作都以数据为中心

## 七大核心概念

  * 与传统的JavaScript代码相比，Angular具备七大核心概念：
    1. 模块
    2. 指令
    3. 组件
    4. 模板
    5. 数据绑定
    6. 服务
    7. 依赖注入
   这些略显晦涩的概念，更多的是借鉴了其它后台编程语言的概念

## 工作原理

  * Angular工作示意图
    使用Angular 扩展语法编写 HTML **模板**，用**组件类**管理这些模板，用**服务**添加应用逻辑，用**模块**打包发布组件与服务。然后，我们通过**引导根模块**来启动该应用。

    Angular 在浏览器中接管、展现应用的内容，并根据我们提供的操作指令响应用户的交互

# TypeScript

---

## TypeScript介绍

  * Angular选择使用TypeScript作为官方最主要的构建语言，TypeScript的本质是向JavaScript语言添加了静态类型和基于类的面向对象编程，同时也支持诸如接口、命名空间、装饰器等特性
  * TypeScript设计目标是开发大型应用，然后转译成JavaScript。由于TypeScript是JavaScript的严格超集，任何现有的JavaScript程序哦都是合法的TypeScript程序

## 配置环境

  1. 安装npm
  2. npm install -g typescript
  3. 创建test.ts文件，在文件中写上：let a = 3
  4. 在命令行窗口，通过tsc执行以下语句：
      tsc test.ts
    将在同一目录下生成test.js

### 配置环境

  * 配置使用 TypeScript 的环境

## TypeScript基本数据类型

  * 布尔类型
    * 布尔类型是最简单的数据类型，只有true和flase两种值：let flag: boolean = true
  * 数字类型
    * TypeScript支持二进制、八进制、十进制、十六进制
    * let num1:number = 0b1010//二进制
    * let num2：number = 0o744//八进制
    * let num3：number = 6 //十进制
    * let num4：number = 0xf00d //十六进制
  * 字符串类型
    * let name：string = "Angular"
  * 数组类型
    * let arr:number[] = [1,2]
    * let arr2:Array\<number> = [1,2]
  
  * Void类型
    * Void表示没有任何类型，例如一个函数没有返回值时，意味着返回值类型时void
  * 任意值类型
    * 任意值类型是在类型不明确的变量使用的，常用于变量的值会动态变化及存储各种类型数据的数组
    * let list: any[] = [1,' car' ,false]
    * let x: any = 1;x=false
  * Null和undefined
    * 默认情况下，可以赋值给其他类型
    * 但是在typescript，如果启动严格的空校验特性（--strictNullChekcs），null和undefined只能赋值给void或本身对应的类型

## 声明

  * 在typeScript中，支持var、const、let这样的声明方式
  * Let
    * 不同于var，let声明的变量只在块级作用域内生效；在相同作用域中，let不允许变量被重复声明
  * Const
    * Const声明的是常量，常量不能被重新赋值，否则将编译报错；如果是对象，对象中的属性值可以被重新赋值

## 函数

  * 函数定义的两种方式
    * 声明式

      ```ts
      function maxA(x:number,y:number):numbe{
        return x>y ? x: y}
      ```

    * 函数表达式

      ```ts
      let maxB = function(x:number,y:number):number{
        return x>y?x:y}
      ```

  * 可选参数
    * js中，被调函数的每个参数是可选的，在typescript中，都是必传的；同时也支持可选参数
    * js中，被调函数的每个参数是可选的，在typescript中，都是必传的；同时也是支持可选参数，在参数名旁边加上 ? 来使变成可选参数

      ```ts
      function maxA(x:number,y?:number):number{
        return x>y?x:y}
      ```

  * 默认参数
    * 如函数的某个参数设置了默认值，当函数被调用时，如果没有给参数传值，或者传值为undefined，参数的值就是设置的默认值
  * 剩余参数
    * 当需要操作多个参数时，或者不知道会有多少参数传递进来时，可以使用剩余参数

      ```ts
      function get (x:number,...list:number[]):number{
        return list.length}
      ```

  * 函数重载
    * 函数重载通过为同一个函数提供多个函数类型定义来达到上限多种功能的目的
  * 箭头函数
    * Typescript提供的箭头函数，在函数创建时就绑定了this

### 使用函数

  * 1、使用不同的数据类型
  * 2、创建并使用函数

## 类

  * 三大封装（封装、继承、多态）
  * 封装
    * 把对象的行为和数据组织起来
  * 继承
    * class MotoCar extends Cars{..}
    * 通过extends继承父类，字类可以访问父类的属性和方法

      ```ts
      class Car{
        engine:string
        constructor(engine:string){
          this.engine = engine
        }
        drive(){
          console.log( 'drive' )
        }
      }
      ```

  * 多态

    ```ts
    class Jeep extends Car{
      engine:string
      constructor(engine:string){
        this.engine=engine
      }
      drive(){console.log( 'Jeep is driving..' )}
    }
    ```

      Jepp类的dive()方法重写了Car类的drive方法，这样就能在不同的类中实现不同的功能，就是多态

  * 修饰符
    * Public
      * 类中成员默认是public，可以被自由的访问
    * Private
      * 类成员被标记为private，则不能在类的外部访问
    * Protected
      * 与private相似，但是在派生类中仍可以访问
  * 抽象类
    * 抽象类是给其他类继承的基类，不能直接被实例化，可以通过abstract定义抽象类和抽象方法。抽象类的抽象方法不包含具体实现，并且必须在派生类中实现

### 使用类

  * 1、定义类
  * 2、实现封装和继承

### 模块

  * 模块导出
    * Export
  * 模块导入
    * Import
  * 模块默认导出
    * Default

### 使用模块

  * 1、倒入模块
  * 2、使用模块
