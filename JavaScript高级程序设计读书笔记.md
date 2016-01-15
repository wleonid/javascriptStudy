#***JavaScript高级程序设计读书笔记***
---

##第三章 基本概念

###主要内容：
* 语法
* 数据类型
* 流控制语句
* 函数

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