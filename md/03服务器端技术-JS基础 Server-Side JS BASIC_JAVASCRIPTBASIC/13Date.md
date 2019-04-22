# Date 对象

---

## 创建 Date 对象

  * Date对象用于对时期和时间进行存储和计算

    ```js
    //使用指定的年月日[时分秒]进行初始化
    var d1 = new Date(2008,7,8)
    var d2 = new Date(2008,7,8,20,18,18)
    var d3 = new Date('2008/8/8')//把string转换为Date

    //初始化为系统时间
    var d3 = new Date()
    var d4 = new Date
    //var d5 = Date()//构建一个string，值为当前系统时间

    //初始化为距离计算机元年指定毫秒数的时间
    var d6 = new Date(0)
    var d6 = new Date(1000*3600*24*365)
    ```

      >注意：月份是从0~11
  
## 获取时间信息

  * 可以使用下述方法获取Date对象中的时间信息

    | 方法名              | 描述                                                  |
    | ------------------- | ----------------------------------------------------- |
    | getDate()           | 返回Date对象”日期“部分数值（1~31）                  |
    | getDay()            | 返回Date 对象“星期”部分的数值（0~6）                |
    | getFullYear()       | 返回Date对象“年份”部分的实际数值                    |
    | getHours()          | 返回Date对象“小时”部分的数值（0~23）                |
    | getMilliseconds()   | 返回Date对象“毫秒”部分的数值（0~999）               |
    | getMinutes()        | 返回Date对象“分钟”部分的数值(0~59)                  |
    | getMonth()          | 返回Date对象“月份”部分的数值（0~11）                |
    | getSeconds()        | 返回Date对象“秒”部分的数值（0~59）                  |
    | getTime()           | 返回Date对象与UTC时间1970年1月1日午夜之间相差的毫秒数 |
    | getTimezoneOffset() | 返回本地时间与格林威治标准时间(GMT)的分钟差           |
  
## 修改时间信息

  * 可以使用如下方法修改Date对象中的时间信息

    | 方法名            | 描述                                              |
    | ----------------- | ------------------------------------------------- |
    | setDate()         | 设置Date对象中“日期”分的数值（1~31，但不限于）  |
    | setFullYear()     | 设置Date对象中“份”部分的数值                    |
    | setHours()        | 设置Date对象中“小时”分的数值（0~23，但不限于）  |
    | setMilliseconds() | 设置Date对象“毫秒”部分的数值（0~999，但不限于） |
    | setMinutes()      | 设置Date对象中“分钟部分的数值（0~59，但不限于）  |
    | setMonth()        | 设置Date对象中“月份”分的数值（0~11，但不限于）  |
    | setSeconds()      | 设置Date对象中“秒”分的数值（0~59，但不限于）    |
    | setTime()         | 以毫秒设置Date对象                                |

## 时间格式转换

  * Date对象可以使用如下方法进行格式化

    | 方法名               | 描述                                                             |
    | -------------------- | ---------------------------------------------------------------- |
    | toString()           | 返回Date对象的字符串形式                                         |
    | toDateString()       | 返回Date对象“日期”部分（年月日）的字符串形式                   |
    | toTimeString()       | 返回Date对象“时间”部分（时分秒）的字符串形式                   |
    | toLocaleString()     | 基于本地时间格式，返回Date对象的字符串形式                       |
    | toLocaleDateString() | 基于本地时间格式，返回Date对象“日期”部分（年月日）的字符串形式 |
    | toLocaleTimeString() | 基于本地时间格式，返回Date对象“时间”部分（时分秒）的字符串形式 |
    | toGMTString()        | 基于GMT时间格式，返回Date对象的字符串形式                        |
    | toUTCString()        | 基于UTC时间格式，返回Date对象的字符串形式                        |

### Date 对象

  * 1、计算合同到期时间等：
    * 创建Date对象保存员工入职日期：如2012年-6-30
    * 合同到期3年，求合同到期时间？
    * 合同到期前，需要提前1个月续签。但如果提前一个月的续签时间刚刚好是周末，则需要提前到上一个周五。求续签时间？
    * 要求在续签时间前一周，向员工发出续签提醒。求提醒时间？
    * 要求：每次计算都要保留上次计算的Date对象。
  * 2、计算明天开始，任意个工作日之后的日期
  * 3、自定义format函数，格式化日期和时间格式

# Number 对象

---

## 创建 Number 对象

  * Number对象表示数值数据和数字常数，主要用于对数字进行指定格式的输出

    ```js
    //构造新的Number对象——引用类型的变量
    var num1 = new Number(5)//[Number:5]
    var num2 = new Number("1.5")//[Number:1.5]
    var num3 = new Number()//[Number:0]
    var num4 = new Number("hello")//[Number:NaN]
    var num5 = new Number("123abc")//[Number:NaN]

    //将数据转换为Number数据类型——值类型的变量
    var num6 = Number(5)//5
    var num7 = Number("1.5")//1.5
    var num8 = Number()//
    var num9 = Number("hello")//NaN
    var num10 = Number("123abc")//NaN
    ```

## Number 对象属性

  * Number对象具有如下静态常量属性

    | 方法名            | 描述                      |
    | ----------------- | ------------------------- |
    | MAX_VALUE         | JS可表示的最大数值        |
    | MIN_VALUE         | JS可表示的最小数值        |
    | NaN               | 表示非数字值              |
    | NEGATIVE_INFINITY | 负无穷大，溢出时返回该值  |
    | POSITIVE_INFINITY | 正无穷大， 溢出时返回该值 |
  
## Number 对象方法

  * 可以使用下述方法获取Date对象中的数字信息

    | 方法名          | 描述                                                   |
    | --------------- | ------------------------------------------------------ |
    | toExponential() | 把数字转换为指数数法的字符串，并具有指定的小数位数     |
    | toFixed()       | 把数字转换为定点表示法示的字符串，并具有指定的小数位数 |
    | toPrecision()   | 把数字格式化为具有定有效位数的字符串                   |
    | toString()      | 把数字转换为指定进制（默认十进制）表示的字符串         |

# Boolean 对象

---

## Boolean 对象

  * Boolean对象表示一个布尔值对象（true或false）

    ```js
    //构造新的Boolean对象——引用类型对象
    var b1 = new Boolean()//false
    var b2 = new Boolean(false)//false
    var b3 = new Boolean(0)//false
    var b4 = new Boolean(null)//false
    var b5 = new Boolean(undefined)//false
    var b6 = new Boolean(NaN)//false
    var b7 = new Boolean("")//false
    var b8 = new Boolean(0.0)//false
    ```

    ```js
    //除了上页中值被视作false外，其他任意值均被视作true
    var b9 = new Boolean(Infinity)//true
    var b10 = new Boolean(Number.NEGATIVE_INFINITY)//true
    var b11 = new Boolean("0")//true
    var b12 = new Boolean("null")//true
    var b13 = new Boolean([])//true
    var b14 = new Boolean({})//true

    //将参数值转换为boolean值类型变量
    var b15 = Boolean()//false
    var b16 = Boolean(0)//false
    var b17 = Boolean(new Object)//true
    var b18 = Boolean("hello")//true
    ```

# 错误处理

---

## 什么是错误处理
  
  * 错误，指程序中的非正常运行状态，在其它编程语言中称为“异常”或错误。解释器会为每个错误情形创建并抛出一个Error对象，其中包含错误的描述信息
  * ECMAScript定义了六种类型的错误。除此之外，还可以使用Error构造方法创建自定义的Error对象，并使用throw语句抛出该对象。
    >EvalError、RangeError、ReferenceError、SyntxError、TypeError、URIError
  * 通过使用JS提供的异常处理语句，可以使用结构化的方式来捕捉发生的错误，让异常处理代码与核心业务代码实现分离，最终是我们能够集中精力编写主业务功能代码。

## Error对象

  * Error对象用于封装异常的相关描述信息
  * Erro对象具有如下成员属性：
  
    属性名|描述
    ---|---
    message| 封装异常的描述信息
    name| 封装异常的类型名称
    stack| 返回错误或异常的代码跟踪信息，例如“@http://127.0.0.1/login.html:10:15” 非标准属性，Firefox/Chrome/IE10+支持

  * Error对象具有如下成员方法

    方法名|描述
      ---|---
    toString()| 返回包含相关错误信息的字符串

## try/catch

  * ECMAScript中使用try...catch...finally...结构来执行异常处理功能，捕捉由系统生成或程序创建并抛出的Error对象，对错误情形加以处理。它的基本语法如下：

    ```js
    try{
      //此处是主业务功能代码
      //主业务功能代码中可能产生并抛出错误
    }catch(error){
      //此处是负责错误处理的代码
    }[finally{
      //此处是出口语句，不论错误发生与否都要执行
    }]
    ```

### 错误处理

  1. 使用try...catch...实现浏览器兼容性校验。
  2. 程序员甲：实现了一个round函数，可按任意小数位数四舍五入。但如果传入的数据不是数字或不能被隐式转换为数字，则会抛出异常。
      程序员乙：实现了一个结账checkout。可输入总价，收款金额，计算找零。其中，为了处理舍入误差，调用了程序员甲的round函数。乙如何进行异常处理？
      分别实现round函数和checkout函数。