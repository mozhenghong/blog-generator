---
title: js里的数据类型
date: 2018-11-13 10:19:41
tags:
---
## 数据类型(7种)

1. 数值(Number)

- javaScript内部所有数字都是以<font color="red">64位浮点数</font>形式存储，即便整数也是如此。
- 数值的进制
     - 十进制： 没有前导0的数值，1+.1=1.1;1+1.1=1.1
     - 八进值：有前缀0o或0O的数值
     - 十六进制：有前缀0x或0X的数值
     - 二进制：有前缀0b或0B的数值
- 特殊数值--NaN
    - 非数字(not a number),主要出现在将字符串解析成数字出错的场合，数据类型依然是Number
    - 0除以0会得到NaN
    - NaN不等于任何值，包括它本身
    - NaN与任何值（包括它本身）的运算，得到的都是NaN

2. 字符串(string)

- ''（空字符串）和‘ ’（空格字符串）不一样，空字符串长度为0，空格字符串长度为1
- 若要在单引号内部使用单引号，就必须在内部的单引号前面加反斜杠\用来转义
   - `\'`:单引号
   - `\n`:回车
   - `\t`:制表符 
   - `\\`:一个反斜杠符号
- 多行字符串的书写
    - ‘1234’+<br>
      ‘5678’
- length属性

返回字符串的长度，该属性是无法改变的

- base64转码
   - btoa（）：任意值转为base64编码
   - atob（）：base64编码转为原来的值


3. 布尔值(Boolean)

- a&&b:a、b同时为真才为真
- a||b：a、b同时为假才为假
- 如果JavaScript预期某个位置应该是布尔值，会将该位置上现有的值自动转化为布尔值

4. symbol(一般不用)

5. null

- 表示空值，即该处的值现在为空

6. undefined

- 表示未定义
- 区别：
    - 变量没有赋值，为undefined
    - object不想给值，就给null，非对象不想给值就给undefined
    - null表示空对象，undefined表示非空对象

7. 对象(object)

- 对象是一种键值对的集合，是一种<font color="red">无序的符合数据集合</font>
- <font color="blue">对象的所有键名都是字符串</font>，如果键名不符合标识名的条件，且不是数字，必须加上引号，否则会报错
   - 第一个字符必须是一个字母、下划线（_）或一个美元符号（$）
   - 其他字符可以是字母、数字、下划线或者美元符号
   - 中文是合法的标识符，可以用作变量名。
- 空字符串也可以为键名

- 对象的引用
   - obj['keyname'],必须加‘’<br>
  ```
  var name='x'
  var obj={
      name:'mm'
  }
  obj[name]==>obj['x']==>undefined
  ```
   - obj.keyname(前提是keyname符合标识符命名规则)
   - 数值键名必须使用方括号运算符引用

- 属性的赋值

点运算符和方括号运算符不仅可以读取值，也可以赋值

- 属性的查看

查看一个属性本身的所有方法，可以使用`Object.keys(obj)`

- 属性的删除

    - delete命令用于删除对象的属性，删除成功后返回true:<br>
`delete  obj['keyname']`或`delete obj.keyname`<br>
*delete把值和value都变成undefinde,而obj.keyundefined=undefined只是把value变成undefined，键名依然存在*
    - 删除一个不存在的属性，delete不会报错，并且返回true，只有当该属性存在，且不得删除时，才会返回false
    - delete命令只能删除对象本身的属性，无法删除继承的属性

- 属性是否存在： in运算符

   - in运算符用于检查对象是否包含某个属性（检查啊的是键名不是键值），如果包含就返回true，不包含返回false<br>
`‘keyname’ in obj`
  - in 运算符不能识别哪些对象是自身的 哪些是继承的

- 属性的遍历：for...in循环

  - for...in循环用来遍历一个对象的全部属性，跳过不可遍历的属性，不仅遍历自身属性，还遍历继承的属性
  ```
  var person={
      name:'xxx',
      age:18
  }
    for(var key in person){
        console.log(key)
    }
    //name age
    ```
- typeof运算符

返回一个值的数据类型,特殊的只有两种<br>
   - `typeof null` //'object'
   - `typeof function` //'function'
