#***JavaScript高级程序设计读书笔记***
---

##第三章 基本概念

###主要内容：
* 语法
* 数据类型
* 流控制语句
* 函数

###3.1语法

####3.1.1JavaScript区分大小写
其实个人感觉语言都区分大小写就好了吧，懒得记哪些区分哪些不区分了

####3.1.2标识符
第一个字符必须是一个字母，下划线或者美元符号，感觉综合了C和PHP
标识符中的字母也可以包含扩展的ASCII或Unicode字母字符（汉字都可以拿来当标识符，不错不错）

####3.1.3注释
跟C的一样

####3.1.4严格模式
ECMAScript 5引入的一个概念，为JavaScript定义了一种不同的解析和执行模型。在严格模式下，ECMAScript3中的一些不确定的行为将得到处理，而且对于某些不安全的操作也会抛出错误，想在哪启用严格模式，可以在他的顶部添加"use strict"，比如整个脚本或者函数内部，支持严格模式的浏览器有IE10+、Firefox 4+、Safari5.1+、Opera 12+和Chrome。
>我想知道不确定行为和所谓的不安全的操作都有哪些

####3.1.5语句
语句结尾的分号不是必需，但是如果忘写而又要压缩js代码的话，就蛋疼了

###3.2关键字和保留字

全部关键词

| break   | do       | instanceof | typeof | case    |
|---------|----------|------------|--------|---------|
| else    | new      | var        | catch  | finally |
| return  | void     | continue   | for    | switch  |
| while   | debugger | function   | this   | with    |
| default | if       | throw      | delete | in      |
| try     |          |            |        |         |

*保留字就不抄了，反正很大可能性没用，把高亮脚本改下，碰到这些词的时候，来个不一样的颜色就是了，彩虹色怎么样*

###3.3变量

ECMAScript变量是松散类型的，可以用来保存任何类型的数据。意思就是说，前一刻这个变量是Number类型，下一刻就可以赋值成String类型了，声明的变量如果没有初始化的话，会默认设为undefined，用var声明的变量是声明这个变量的作用域中的局部变量，不用var的话，会把它创建成一个全局变量。

###3.4数据类型

ECMAScript中有5种数据类型，Number、Undefined、Null、Boolean、String和Object，不支持任何创建自定义类型的机制

####3.4.1 typeof操作符

返回变量或者字面值常量的类型，返回的可能除了五大类型之外还有一个，那就是function

####3.4.2 Undefined类型
对于未声明的变量，只能进行一项操作，即使用typeof检查它的数据类型，会返回一个undefined

####3.4.3 Null类型

逻辑上表示一个空指针对象；用typeof检测时会返回object；
如果定义的变量准备在将来用于保存对象，那最好将它初始化为null，这样只要直接检查Null值就可以知道相应的变量是否已经保存了一个对象的引用
实际上，undefined的值是派生自null值的，因此null==undefined为true

####3.4.4 Boolean类型

Boolean类型的字面值是区分大小写的，True和False都不是Boolean值
其他类型的值都可以转换成这个类型；

####3.4.5 Number类型

整数可以通过八进制或十六进制的字面值来表示，八进制前导0，十六进制前导0x，超出范围（如09）将被当成十进制，十六进制超出范围会报错，进行计算的时候会被转成十进制

超过浮点数范围的数，如果是正数会被换成Infinity，如果是负数会被换成-Infinity
如果某次计算返回了正或负的Infinity值，那这个值将无法继续参与下一次的运算，因为Infinity不是能够参与计算的数值。可以用isFinite()函数检测数值是否超出计算范围，没超出返回true;

NaN,非数值，当返回而未返回数值的情况，如0/0；任何涉及NaN的操作都会返回Nan，NaN跟认识值都不等，包括它本身，所以要检测一个值是不是NaN,要使用isNaN()函数，任何不能被转换为数值的值都会让这个函数返回true;


###3.5操作符

###3.6语句

###3.7函数

###3.8小结












###严格模式：
use strict

###数据类型
number,bool,string,null,undefined,object

####数值转换
Number()、parseInt()、parseFloat()
备注：parseInt("",base)，base指定解析字符串中的数的基数

####转义字符
|  字符  |                   含义                  |         举例        |
|--------|-----------------------------------------|---------------------|
| \xnn   | 以十六进制代码nn表示的一个字符（ASCII） | \x41表示A           |
| \unnnn | 以十六进制代码nnnn表示的一个Unicode字符 | \u03a3表示希腊字符Σ |

####toString()
调用数值的toString()函数，可以传递一个参数作为转成字符数字的基数

####Object的每个实例都具有下列属性和方法
constructor:保存着用于创建当前对象的函数。
hasOwnProperty(propertyName):用于检查给定的属性在当前对象实例中（而不是实例的原型中）是否存在
toLocaleString():返回对象的字符串表示，该字符串与执行环境的地区对应
toString():返回对象的字符串表示
valueof():返回对象的字符串、数值或布尔值表示。通常与toString()方法的返回值相同。

####ECMAScript中switch语句中可以使用任何数据类型，每个case的值不一定是常量，可以是变量，甚至是表达式。
example1:

    switch("hello world"){
        case "hello"+" world.":
            alert("Greeting was found.");
            break;
        case "goodbye":
            alert("Closing was found.");
            break;
        default:
            alert("Unexpected message was found.");
    }

example2:

    var num=25;
    switch(true){
        case num<0:
            alert("Less than 0.");
            break;
        case num>=0&&num<=10:
            alert("Between 0 and 10.");
            break;
        case num>10&&num<=20:
            alert("Between 10 and 20.");
        default:
            alert("More than 20.");
    }


####function的参数
ECMAScript的函数参数是以一个包含零或多个值的数组的形式传递的。所以不介意传进来多少个参数，也不在乎传进来参数是什么数据类型。
传入function的参数自动形成一个arguments数组
可以通过arguments.length获取参数的个数

##第四章 变量、作用域和内存问题

###执行环境及作用域

###instanceof
result = variable instanceof constructor
如果变量是给定引用类型，返回true