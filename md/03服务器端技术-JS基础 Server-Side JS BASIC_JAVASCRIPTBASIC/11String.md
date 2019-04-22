# String概述

---

## 包装类型

  * 什么是包装类型？专门封装原始值类型的数据，并提供对数据常用操作的内置引用类型。

  * 为什么要有包装类型？让原始类型的数据也可以像引用类型一样，拥有方法和属性

  * JavaScript中的包装类型有三个
    * String类型
    * Number类型
    * Boolean类型
  * 何时使用包装类型？只要用原始类型的数据调用方法或访问属性时，js引擎都会自动创建对应的包装类型对象。
  * 方法调用完，包装类型对象自动释放

## 文本 String

  * String对象用于处理文本字符串
  * 创建**原始类型**字符串变量：

    ```js
    var stuName = 'Smith'
    var gendrt = '男'
    var priceString = String)(150.5)
    ```

    >定义字符串值可以用英文单引号或双引号
  * 创建**引用类型**字符串对象:
  `var carTypr = new String('BMW528Li')`

## 转义字符

  * 编写JavaScript脚本时，可能需要显示一些具有特殊含义的字符，此时可以使用转义字符串:

    | 转义字符 | 含义说明                              |
    | -------- | ------------------------------------- |
    | \b       | 退格符（\u0008）                      |
    | \n       | 换行符（\u000A）                      |
    | \r       | 回车符 (\u000D)                       |
    | \t       | 水平制表符（\u0009）                  |
    | \'       | 单引号（\u0027）                      |
    | \''      | 双引号（\u0022）                      |
    | \\       | 反斜线（\u005c）                      |
    | \xNN     | 由两位十六进制数NN指定Latin-1字符     |
    | \uNNNN   | 由四位十六进制数NNNN指定的Unicode字符 |

## 字符串的使用

  * JavaScript中字符串的内容是**不可变**的。String对象的所有方法，返回的都是一个全新的对象，而不是修改原始字符串内容，例如：

    ```js
    var s1 = new String('Hello')
    var s2 = s1.toUpperCase()//把字符串转换为大写形式

    console.log(s1)//Hello
    console.log(s2)//HELLO
    ```

  * length属性返回字符串中字符的个数

    ```js
    var s3 = new String('abc一二三')
    console.log(s3.length)//6
    ```

    >JavaScript字符串默认采用Unicode字符集， 中文字符也只算一个字符
  
# 字符串常用操作

---

## 大小写转换方法

  * toLowerCase()方法返回字符串的完全小写形式
  * toUpperCase()方法返回字符串的完全大写形式

    ```js
    var msg = 'Heloo World'
    var lowerMsg = msg.toLowerCase()
    var upperMsg = msg.toUpperCase()

    console.log(msg)//Hello World
    console.log(lowerMsg)//hello world
    console.log(upperMsg)//HELLO WORLD
    ```

### 模拟输入验证码

  * 程序中暂时固定保存一个由大小写字母、数字组成的4位验证码。
    * 请用户反复输入验证码
    * 只要输入错误，就要继续输入。
    * 直到输入成功，页面显示登陆成功
    * 验证码比较时，不区分大小写。

## 获取指定位置的字符

  * charAt( index )方法用于获取指定下标处的字符

    ```js
    var msg='Hello你好'

    console.log(msg.charAt(0))//H
    console.log(msg.charAt(5))//你
    ```

  * charCodeAt( index )方法用于获取指定下标处的字符的Unicode码

    ```js
    var msg = 'aA一？'
    console.log(msg.charCodeAt(0))//97
    console.log(msg.charCodeAt(1))//65
    console.log(msg.charCodeAt(2))//19968
    console.log(msg.charCodeAt(3))//40869
    ```

    > String.fromCharCode()可用于将一个字符编码转换为对应的字符

### 获取指定位置的字符

  * 1.根据身份证判断性别
  * 2.将用户输入的一条信息编码为数字组成的字符串。
  * 每个字符必须统一编码为5位数字
  * 3.计算一段字符串中英文字符、中文字符、数字、其它字符的数量

## 检索字符串

  * indexOf( value, [fromIndex])返回第一次出现指定子串的下标
  * lastIndexOf( value, [fromIndex])返回最后一次出现指定子串的下标

    ```js
    var email = 'tom@163@sohu.com'

    console.log(email.indexOf('tom'))//0
    console.log(email.indexOf('@'))//3
    console.log(email.indexOf('@',5))//7
    console.log(email.lastIndexOf('@'))//7
    console.log(email.lastIndexOf('@',5))//3
    console.log(email.indexOf('Mary'))//-1
    ```

### 检索敏感词

  * 1、程序中保存一个固定的敏感词，比如：“no”
    * 请用户输入一句话
    * 用程序检索用户输入中包含的所有敏感词的位置。
  * 2、使用从后向前查找的方式实现以上功能

## 截取字符串

  * slice(start, [end])返回从start到end-1范围内的子串；若省略end，则直接获取到字符串结尾。
  * substring(start, [end])返回从start到end-1范围内的子串；若省略end，则直接获取到字符串结尾。

    ```js
    var msg='abc一二三'

    console.log(msg.slice(2,4))//c一
    console.log(msg.substring(2,4))//c一
    console.log(msg.slice(2))//c一二三
    console.log(msg.substring(2))//c一二三

    console.log(msg.slice(-3,-2))//一
    ```

### 截取字符串

  * 1、解析一个邮件地址，分别获得其中的用户名和服务器域名
  * 2、根据身份证号输出生日，比如：1990年6月29日
    * 要求：利用三个函数分别实现

## 分隔字符串

  * split( separator, [count]）使用指定分隔符对字符串进行拆分

    ```js
    var data = '||Tom||Mary||John||'
    var arr1 = data.split('||')
    for(var i=0;i<arr1.length;i++){
      console.log(i+'='+arr1[i])
    }
    ```

      >0=
      >1=Tom
      >2=Mary
      >3=John
      >4=

    ```js
    var data = '||Tom||Mary||John||'
    var arr1 = data.split('||',3)
    for(var i=0;i<arr1.length;i++){
      console.log(i+'='+arr1[i])
    }
    ```

      >0=
      >1=Tom
      >2=Mary

### 分隔字符串

  * 1、解析一个邮箱地址，分别获得其中的用户性和服务器域名（使用分隔字符串实现）
  * 2、将一句英文中的每个单词首字母转为大写。
  * 3、假设浏览器接收到游戏服务器返回的如下格式的一些字符串。如：Tom@补给兵@60%#Mary@医疗兵@80%#John@特种兵@30%
    规则：#分隔每个角色
          @分隔每个角色的姓名，兵种和剩余生命
    试将其解析并显示出来：
  * 4、计算字符串中每个字符出现的次数

## 连接字符串

  * concate( str1, str2... strn）用于拼接两个或多个字符串

    ```js
    var s1 = 'AA'
    var s2 = s1.concat('BB','CC',55)

    console.log(s1)//AA
    console.log(s2)//AABBCC55
    ```

  * 此外，还可以使用+做字符串拼接

    ```js
    var s3 = 'AA'
    var s4 = s3 + 'BB' + 'CC' + 66

    console.log(s4)//AABBCC66
    ```

# 模式匹配

---

## 修饰符

  * 模式匹配中可以使用如下三个属性修饰符

    | 修饰符 | 描述                                                         | 示例    |
    | ------ | ------------------------------------------------------------ | ------- |
    | i      | ignoreCase，执行对大小写不敏感的匹配                         | /is/i   |
    | g      | global，执行全局匹配（查找所有匹配而不是第一次匹配之后停止） | /is/g   |
    | m      | multiline，允许多行匹配                                      | /^is$/m |

    >修饰符可以组合应用
    >修饰符m对^和$匹配会产生影响

## 替换子字符串

  * replace(substr/regexp, replacement) 方法用于在字符串中用一些字符替换特定的字符，或替换一个与正则表达式匹配的子串
  * 注意：原始字符串内容不会发生改变

    ```js
    var data = 'Microsoft is a big Company,microsoft's
    color is red and has MICROSOFT logo like microsoft'

    console.log(data.replace('microsft','oracle'))
    console.log(data.replace(/microsft/,'oracle'))
    console.log(data.replace(/microsft/i,'oracle'))
    console.log(data.replace(/microsft/g,'oracle'))
    console.log(data.replace(/microsft/ig,'oracle'))
    ```

## 匹配

  * match(value/regexp)方法可以在字符串内检索指定的值，或找到一个或多个与正则表示式匹配的的子串
  * 该方法类似 indexOf() 和 lastIndex()，但是它返回指定的值，而不是字符串的位置

    ```js
    var data = 'Microsoft is a big Company,microsoft's
    color is red and has MICROSOFT logo like microsoft'

    console.log(data.match(/microsft/,'oracle'))
    console.log(data.match('microsft','oracle'))
    console.log(data.match(/microsft/i,'oracle'))
    console.log(data.match(/microsft/g,'oracle'))
    console.log(data.match(/microsft/ig,'oracle'))
    ```

## 查找

  * search(regexp)方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串
  * 返回第一个与regexp相匹配的子串的起始位置 如果没有找到任何匹配的子串，则返回-1

    ```js
    var data = 'Microsoft is a big Company,microsoft's
    color is red and has MICROSOFT logo like microsoft'

    console.log(data.search(/microsft/,'oracle'))
    console.log(data.search('microsft','oracle'))
    console.log(data.search(/microsft/i,'oracle'))
    ```

      >search()方法不支持全局匹配，将忽略标志g

### 字符串的模式匹配

  * 1、使用模式匹配和非模式匹配两种方式实现替换字符串中的关键字no为**。替换后，显示共替换多少处。