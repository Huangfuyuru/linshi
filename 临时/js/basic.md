# 基本概念

var data;
typeof data;//返回的是undefined 对定义但未初始化的变量

null 空指针对象
typeof null //返回的是obj 
alert(null == undefined) //true 

Boolean
数据类型		转换为true	转换为false
string		非空字符串	''
number 		非零数字		0和NaN
undefined			false
obj		任何对象		null

Number
+0 -0可以认为是相等
0.1+0.2 = 0.30000000000000004
永远不要测试某个特定的浮点数值。
NaN 搭配isNaN()函数,这个函数接受一个参数，该参数可以是任何类型，而函数会帮我们确定这个参数是否“不是数值”.
alert(isNaN(NaN)) //true
alert(isNaN(10))  //false
alert(isNaN("10")) //false
alert(isNaN("blue"))  //true
parseInt() 函数  可以指定第二个参数，使第一个参数按照进制转化
var num = parseInt("0xAF",16) //175
var num = parseInt("AF",16)    //175

String 
toString()方法，默认不传入参数,是10
var num =10;
alert(num.toString())     //10
alert(num.toString(2))   //1010
alert(num.toString(8))   //12

Object 类型是所具有的任何属性和方法也同样存在于更具体的对象中。Object的每个实例中都具有下列属性和方法。
constructor:保存着用于创建当前对象的函数
hasOwnProperty(propertyName):用于检查给定的属性在当前对象实例中，而不是在实例的原型中，是否存在。  o.hasOwnProperty("name")
isPrototypeOf(object) :用于检查传入的对象是否是传入对象的原型。
toLocaleString():返回对象的字符串表示
toString:返回对象的字符串表示
valueOf()：返回对象的字符串、数值或布尔值表示

原码：
第一位表示符号位，其余位表示值。
反码
正数的反码是其本身。负数的反码是在其原码的基础上，符号位不变，其余各位取反
补码
正数的补码是其本身。负数的补码是在其基础上，符号位不变，其余各位取反，最后加 +1
计算机中，负数是按照补码存储的，正数按照原码存储

按位非  ~ 操作数的负值减一 
var num1 = 25;	     0000 0000 0000 0000 0000 0000 0001 1001
var num2 = ~num1;    1111 1111 1111 1111 1111 1111 1110 0110
alert(num2)
按位与 & 
如果是两个负数，按照补码按位与，最后得到的也是补码，输出可以是真值
如果是一个负数一个正数，正数按照原码，负数按照补码进行按位与，如果结果符号为0，则是原码，如果符号为1，则是补码。
alert(25&3) //1
alert(-25&3)//3
alert(-25&-24) //-32
按位或 |       
alert(25|3)  //27
alert(-25|3) //-25
按位异或 ^   相同为0，不同为1
alert(25^3) //26
有符号位的移动
左移 << 会将数值的所有位向左移动指定的位数。2<<5 向左移动5为，变成64
左移不会影响操作数的符号位，将-2向左移动5位，结果将是-64
右移 >> 将数值向右移动，但保留符号位。
在移位过程中，原数值会出现空位，空位出现在原数值的左侧，符号位的右侧，而此时ECMAScript会用符号位的值来填充所有空位，以便得到一个完整的值。
-64>>2  //-2
过程 
-64 的补码是  1100 0000
向右移动5位，空位用符号位补齐 1111 1110
因为是补码 换成原码  1000 0010 //-2
无符号位的移动
右移>>>  无符号右移的空位用0补齐，对于正数无符号右移和有符号右移相同。但是对于负数有区别。
-64>>>5  //134217726