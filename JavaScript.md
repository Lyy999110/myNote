；

# JavaScript基础：语法

[TOC]

​	

## 第一章：数据类型

​	js中有6种数据类型，包括5种基本数据类型(Number、String、Boolean、Undefined、Null) 加一种复杂数据类型(Object)。

### 1.1 number类型

	代码列				结果列			解释列
	typeof 123		'number'      typeof 获取变量类型
	typeof 123.0	'number'
	typeof 123e1	'number'
除了数字外是数据类型，还有NaN、infinity 也是number类型

```
代码列						      结果列			解释列
var num = NaN;
num;							NaN
typeof num					    'number'

判别一个数是否是一个数据类型							方法 isNaN(args)
isNaN(num);						true
```



```
代码列						      结果列			解释列
num = Infinity ;
typeof num	 ;					'number'
```

##### 注意事项：浮点运算

​	1. 尽量避免使用浮点运算，因为存在精度损失问题

```
代码列						      结果列			解释列
console.log((1/3)===(1-2/3)) 		 false
```

#### 1.1.1 number的方法

1. toString数字变字符,可以传递一个表示基数的参数，告诉它返回几进制数值的字符串
2. num.toLocaleString()

```js
var num	= 10;
num.toString()			'10'
num.toString(16)		'a'
双点解析
10..toString()
加空串
10+''
```

​	3.toFixed() 按照指定的小数位返回数值的**字符串**形式，会进行4舍5入。

```js
var num	= 10;
num.toFixed(3)		'10.000'   保留3位小数点
var tenp = 10.0005
tenp.toFixed(3)		'10.001'    保留3位小数点，四社五入
tenp.toFixed(2)		'10.00'		保留2位小数点。
```

​	4.toPrecision() 返回**固定长度的字符串**数字，会进行4舍5入。	

```js
var num = 9.8584
num.toPrecision(4)			'9.858'
num.toPrecision(2)			'9.9'
```



### 1.2 string类型

​	不可变对象；不可以被任意修改 

```
代码列					结果列			解释列
typeof 'abcdefg'	'string'
typeof "abcdeg"		'string'
var name = "ding"; 
typeof `${name}`  	'string'
```

不可变对象；不可以被任意修改 

```
代码列					结果列			解释列
name[0]='L';
name[0]	;				'd'
name[0] = 'L';		
name;					'ding'    	无法被修改：不可变对象；不可以被任意修改 
```

字符变数字

```
parseInt(str)
parseFloat(str)
```



#### 1.2.1 字符串方法

 1. length属性

    ```
    代码列					结果列			解释列
    str = "159753" ;			
    str.length；				6
    ```

 2. 下标索引

    [index]+返回字符串中指定下标（位置）的字符串

    ```
    代码列					结果列			解释列
    str = "159753" ;
    str[1]					'5'
    str[11]					undefined    角标不能越界
    ```

    charAt(index)+返回字符串中指定下标（位置）的字符串

    ```
    代码列					结果列			解释列
    str = "159753" ;
    str.charAt(2)			'9'
    str.charAt(11)			''			角标可以越界
    ```

    charCodeAt(index)+返回字符串中指定索引的字符 unicode 编码

    ```
    代码列					 结果列			解释列
    str = "159753" ;
    str.charCodeAt(2);		57
    str = "中国";
    str.charAt(1);			'国'
    str.charCodeAt(1);		22269
    ```

 3. 获取子串索引

    indexOf(subStr[,startIndex]):  Search from left to right

    startIndex：起始搜索位置

    返回字符串中一个子串第一处出现的索引（从左到右搜索）。如果没有匹配项，返回 -1 。

    ```
    代码列													结果列			解释列
    str = "I gradually donot love you anymore.";
    str.indexOf("gradually")								2
    ```

    ```
    代码列						结果列			解释列
    str ="more and more";
    str.indexOf("more",1)		9			下标1之前的不寻找
    str.indexOf("more",2)		9
    str.indexOf("more",8)		9
    str.indexOf("more",9)		9
    str.indexOf("more",10)		-1
    ```

    lastIndexOf(subStr[,startIndex]):返回指定文本在字符串中最后一次出现的索引，如果没有匹配项，返回 -1

    本质是反向搜索

    ```
    代码列									结果列			解释列
    str ="more and more";
    str.lastIndexOf("more");				9
    str[9]									'm'
    str.lastIndexOf("more",10)				9
    str.lastIndexOf("more",9)				9
    str.lastIndexOf("more",8)				0
    str.lastIndexOf("more",1)				0
    str.lastIndexOf("more",0)				0
    ```

 4. 子串位置查询

    search()方法搜索特定值的字符串，并返回匹配的位置：

    支持正则匹配：

    ​		[(12条消息) 正则表达式_唐朝-CSDN博客](https://blog.csdn.net/qq_36007881/article/details/115707536)

    ```
    代码列						结果列			解释列
    str ="less is more";
    str.search("more")			8
    str.search('(more)$')		8
    str.search(' ')				4
    ```

    ```
    代码列							结果列			解释列
    str ="More is more";		
    str.search(/more/)				8
    str.search(/more/i)				0			忽略js的大小写敏感
    ```

    ```
    代码列								结果列			解释列
    var tell = "tell13895099873:"
    tell.search(/[1-9]{1,}/)			4
    ```

    

 5. 子串获取

    slice(a[,b]) ： 切片[a,b) 	 		a,b可负

    substring(a[,b]) 切片[a,b)  	   a,b不可负

    ```
    代码列								结果列			解释列
    var tell = "tell13895099873:"
    tell.slice(4,-1)				'13895099873'
    tell.substring(4,15)			'13895099873'
    ```

    substr(startindex,length) :获取指定长度字符串

    ```
    代码列								结果列			解释列
    var tell = "tell13895099873:"
    tell.substr(4,11);				'13895099873'
    ```

 6. 子串替换

    ​	replace('src','tar'):

    ​	用另一个值替换在字符串中指定的值，不会改变调用它的字符串。它返回的是新字符串。

    ​	默认地，`replace()`只替换首个匹配，并对大小写敏感：

    ```
    代码列													结果列			解释列
    var tell = "tell13895099873:"
    var newtell = tell.replace(/[0-9]{1,}/,'614856415');
    newtell												'tell614856415:'
    tell												'tell13895099873:'   `replace()`只替换首个匹配
    ```

    ##### 注意：

    ​		如需执行大小写不敏感的替换，请使用正则表达式 /i（大小写不敏感）,

    ​		如需替换所有匹配，请使用正则表达式的 g 标志（用于全局搜索）：

 7. 大小写转换

    ​	toUpperCase(),toLowerCase()

 8. 多字符串连接

    ​	concat(a[,b[,c[,....]]])

 9. 删除字符串两端空白

    ​	trim()

 10. 字符串切分转数组

     split(reg)

 11. 是否包含子串

     includes(substr)

 12. 字符串填充

     padStart(maxLength,fillString='')

     padEnd(maxLength,fillString='')

     ```js
     date.getSeconds().toString().padStart(2,'0')
     ```

     

 13. 

 14. 

     

### 1.3 Boolean类型

​	ture 和 false

```
代码列				结果列			解释列
typeof true		'boolean'
typeof false	'boolean'
```

 转换boolean

```
代码列						  结果列
Boolean("ture")				true
Boolean({})					true
Boolean("a")				true
```





### 1.4 undefined类型

使用var声明了变量，但未给变量初始化值，那么这个变量的值就是undefined。

```
代码列						结果列			解释列
typeof undefined		'undefined'
var a ;
typeof a				'undefined'
undefined == undefined		true
undefined === undefined		true
null == null				true
a === undefined				true
```

undefine做条件等于false,

null也是一样视为false，

空串也是false

0也是false

'0'也是false

```
a = undefined;			
var flag ;
if (!a){
	flag=true}
else{
	flag=false}
flag								true

a = null ;
flag = null ;
if (!a){
	flag=true}
else{
	flag=false}
flag								true
```



### 1.5 null类型

​	null类型被看做空对象指针，前文说到null类型也是空的对象引用

```
代码列			  结果列			解释列
a = {};
a= null;
a				null			a指向空
typeof a		'object'      	a是空的对象引用
```

```js
undefined === undefined		true
null == null				true
```



### 1.6 object类型

​	js中对象是一组属性与方法的集合。这里就要说到引用类型了，引用类型是一种数据结构，用于将数据和功能组织在一起。引用类型有时候也被称为对象定义，因为它们描述的是一类对象所具有的属性和方法，故称为对象object。

#### 1.6.1 js中三大引用类型

##### 	1. object类型:

​			创建方式一：new object()创建

​					var obj  = new Object();

​					obj.name = "dingzhiqiang" ;

​			创建方式二：花括号{}

​					var obj = {name:"dingzhiqiang"} ;

​            遍历方法：

​					for ... in  遍历     						for (index in obj)

​					Object.keys()遍历 					配合 forEach

​					Object.getOwnPropertyNames()遍历 （等价于Object.keys()） 配合 forEach

##### 	2.Array类型

​			创建方式一：new Array(elem1,elem2,....,elemK)  

​							elemi(i=1,...,K)可为6种数据类型中的任何一种

​					var  arr = new Array(1,"2",true,undefined,{},null) ;

```
代码列						结果列
var  arr = new Array(
1,"2",true,undefined,
{},null) ;				
arr						(6) [1, '2', true, undefined, {…}, null]
```

​			创建方式二：中括号[]

​					 var arr = [1,"2",true,undefined,{},null]

```
代码列						结果列
var arr = [1,"2",true,
undefined,{},null] ;
arr						(6) [1, '2', true, undefined, {…}, null]
```

[方法见后面](#5.2Array对象)



##### 3.function类型

​	每个函数都是Function类型的实例，而且都与其他引用类型一样具有属性和方法。

```
function sum(num1,num2){
　　return num1 + num2;
};
等价于
var sun = function (){
　　return sum1 + sum2;
};
```

#### 1.6.2 值类型与引用类型

​	[局部变量存放在栈空间、对象存在堆空间 ]

​	看两段代码：

```
var a = 100;  
var b = a;
a = 200;
console.log (b);
a,b都是局部变量；存的值是值类型--> number ,string ,boolean
证明：
代码列			结果列
var a=10;
var b = a;
b;				10
typeof b;		'number'

```

```
var a = {age : 20};
var b = a;
b.age = 21;
console.log(a.age);
a,b都是局部变量；存的值是引用类型-->指针
证明：
var a = {age:10};
var b = a;		
typeof b;		'object'
```

------

### 1.7 运算符	

| 算数运算符                     | 结果    | 例子  |
| ------------------------------ | ------- | ----- |
| +  -  *  /  %  ++  --          | number  | 5.1+2 |
| 赋值运算符                     |         |       |
| =   +=   -=    *=    /=   %=   | number  |       |
| 比较运算符                     |         |       |
| ==    ===(相同类型相同值)   != | boolean |       |
| !==  >   <                     |         |       |
| 逻辑运算符                     |         |       |
| &&  \|\|  ！                   | boolean |       |
|                                |         |       |

## 第二章：变量及常量

### 2.1变量

2.1 变量的定义

​				let   :是块级作用域，函数内部使用let定义后，对函数外部无影响

​				const :      const定义的变量不可以修改，而且必须初始化。

​				var	:**let声明的变量支持块级作用域，var声明的变量不支持块级作用域.var声明的变量会绑定到window对象上**

```
for (var i =0 ;i <5 ;i++){
   for(var j =0 ;j<5;j++){
       	continue
    }
 }
console.log(i)     5
console.log(j)     5
window.i   		   5
```

总结
1.var定义的变量会绑定到window上，let和const不会
2.const声明的同时必须初始化,不初始化直接报错
3.let支持块级作用域
4.const声明的变量不可以被修改，但是变量里面的属性可以被修改，若想连属性也不能被修改，需要用Object.freeze(obj);冻结变量


#### 2.2 变量的分类

## 第三章：流程控制

### 2.1 条件控制

​	条件控制共有4这种方式，它们各有特点，可以应对不同的场合。

​	方式一：if (condition){}else{}

​	方式二：if(condition){}else if(condition){}else{}

​	方式三：switch(k){

​							case 1: code ;break;

​							case2: code ;break;

​							...

​							default:code;break;

​					}

```
代码  							结果				结果解释
var a ;
switch(3){ 
	case 1: a=1;
	case 3:a=3;
	case 5 :a=5;break; 
	default: a=100;break;}
a								5  				case 3:没有break直接进入5
```

```
代码  							结果				结果解释
var a ;
switch(3){ 
	case 1: a=1;
	case 3:a=3;break; 
	case 5 :a=5;break; 
	default: a=100;break;}
a								3  				case 3:有break不进入5
```

	代码  							结果				结果解释
```
var a ;
switch(3){ 
	default: a=100;break;
	case 1: a=1;
	case 3:a=3;break; 
	case 5 :a=5;break; }
a								3  				default :没有break最终进入3
```

方式四：三元运算符

​					condition ？yes-code : no-code

```
代码块													结果
1>2 ? console.log("yes"):console.log("no")   	 		no
```



### 2.2 循环控制

forEach和for in

示例一：对象遍历

```js
var date = { Q0: '0', Q1: '0',Q2: '0', Q3: '0', Q4: '0',Q5: '0',Q6: '0',
			 Q7: '0',Q8: '0',Q9: '0',Q10: '0',Q11: '0',Q12: '0',
			 Q13: '0',Q14: '0',Q15: '0',Q16: '0',Q17: '0' }
Object.keys(date).forEach(func(item[,index[,arr]]){ ... })
//or
for (let i in date){
   console.log(i+""+date[i])
}
```



### 2.3 异常处理

#### 2.3.1 javaScript错误类型

​		js 的报错信息共分为两大类：分别是【语法错误】、【异常错误】。语法错误是会在预解析过程中遇到的，它会导致整个js文件无法执行；异常错误会导致出错行之后的js代码无法执行。

7类错误：

​		1.语法错误：SyntaxError

​		2.引用错误：Uncaught ReferenceError（不能捕获的引用错误）

​		3.范围错误：RangeError

​		4.类型错误：TypeError

​		5.URL错误：URLError

​		6.eval()函数执行错误:EvalError

​			ES5以上的JavaScript中已经不再抛出该错误，但依然可以通过new关键字来自定义该类型的错误提示。

​		7.Error()错误

#### 2.3.2创建错误对象

​	

```
语法： 
/**
* @param message: 错误信息 
* @param fileName: 发生错误所在文件名     
* @param lineNumber: 发生错误所在行号 
*/ 
new Error([message[, fileName[,lineNumber]]])


```



#### 2.3.3 try-catch处理异常

```
try {
    //可能会导致错误的代码
} catch (error) {
    //在错误发生时怎么处理
} finally {
 	//发生错误也必须要执行的语句
}
```

```
try {
    someFunction();
} catch (error) {
    if (error instanceof TypeError) {
        //处理类型错误
    } else if (error instanceof ReferenceError) {
        //处理引用错误
    } else {
        //处理其他类型的错误
    }
}finally {
 	//发生错误也必须要执行的语句
}
```



#### 2.3.4 throw抛出异常

```
try {
    throw new Error("我故意扔出一个异常")
} catch (error) {
    console.log(error.message)
}finally {
 	console.log("必须被执行的语句")
}
结果：
    我故意扔出一个异常
    必须被执行的语句
```

```js
try {
	if (true) throw new Error("我故意扔出一个异常")
} catch (error) {
    console.log(error.message)
}finally {
 	console.log("必须被执行的语句")
}
结果：
    我故意扔出一个异常
    必须被执行的语句
```

## 第四章：函数

### 3.1普通函数

```js
let fun0  = function myalert(){
	alert("你好啊！")
 }
 fun0()
```

### 3.2 构造函数

```js
function Person(name, gender, hobby) {
    this.name = name;
    this.gender = gender;
    this.hobby = hobby;
    this.age = 6;
}
var p1 = new Person('zs', '男', 'basketball');
```

### 3.3 匿名函数

```js
let fun1 = function(){
			
}
```

匿名函数的立即执行方式

```js
(function (str){
		    console.log("丁志强"+str);
})("好帅！")
```



### 3.4 箭头函数

#### 	3.4.1 Arrow Function

​		使用格式：参数

​				· 一个参数:参数括号可以省略 

​						x => x*x ;

​				· 0个参数：参数括号必须写

​						()=> 3.14

​				· 多个参数：参数括号必须写

​						(x,y,z) => x+y+z

​		使用格式：函数体

​				· 函数体内只含一条表达式：return 和{} 可以省略

​						同上

​				· 函数体内包含多天表达式：return 和{} 不可省略

​					x => { var temp = x*x ; var pi = 3.14 ;retuen temp+pi }

#### 3.4.2 箭头函数特点（重要）

​		箭头函数看上去是匿名函数的一种简写，但实际上，箭头函数和匿名函数有个明显的区别：

​		箭头函数内部的`this`是词法作用域，由上下文确定。

```
	var obj = {    
		birth: 1990,    
		getAge: function () {  
       		//this = obj
			var b = this.birth; // 1990        
			var fn = function () {            
				//this = window
				return new Date().getFullYear() - this.birth; // this指向window或undefined
            };        
            return fn();
     	}
    };
    obj.getAge(); // undefined
    改写1
    var obj = {    
		birth: 1990,    
		getAge: function () {        
			var b = this.birth; // 1990        
			var fn = function () {            
				return new Date().getFullYear() - b; // 改this为b ,说明函数内的函数的this不指向obj
            };        
            return fn();
     	}
    };
    obj.getAge()   //31
    改写2
    birthday = 1995 ;
    var obj = {    
		birth: 1990,    
		getAge: function () {        
			var b = this.birth; // 1990        
			var fn = function () {            
				return new Date().getFullYear() - this.birth; //说明函数内的函数的this指向window
            };        
            return fn();
     	}
    };
    obj.getAge()   //26
```



```
	var obj = {
    	birth: 1990,
        getAge: function () {
        	var b = this.birth; // 1990
            var fn = () => new Date().getFullYear() - this.birth; // this指向obj对象
           	return fn();    
        } 
   	}; 
   	obj.getAge(); // 31
   	箭头函数完全修复了`this`的指向，this总是指向词法作用域，也就是外层调用者`obj`
```

### 3.5 this调用详解

```js
1.对象方法模式探究
```

```js
//第一种
//对象模式
name = "OA"
let obj = {
	name : "XA" ,
	speak:function(){
		alert(this.name)
	}
}
obj.speak() 								//XA
//对象模式,箭头函数的this是词法作用域,
name2 = "OB"
let obj2 = {
	name2 : "XB",
	speak:()=>{alert(this.name2)}
}
obj2.speak()								// OB
------------------------------------------------------------------------------------------------------------
//第二种
//对象模式，this指向对象本身
name = "OA"
let obj = {
	name : "XA" ,
	speak:function(){
		setTimeout(function(){
			alert(this.name)
		},500)
	}
}
obj.speak()									//OA
//对象模式,箭头函数的this是词法作用域,从内层到外寻找this
name2 = "OB"
let obj2 = {
	name2 : "XB",
	speak:function(){
		setTimeout(()=>{
				alert(this.name2)
			},500)
	}
}
obj2.speak()								//XB	
------------------------------------------------------------------------------------------------------------
//第三种
name = "OA"
let obj = {
	name : "XA" ,
	speak:function(){
		// this = obj
		setTimeout(function(){
			//this = window 
			setTimeout(function(){
				//this = window
				alert(this.name)   // OA
			},500)
			//this = window 
			setTimeout(()=>{
				alert(this.name)   //OA
			},500)
		},500)
		
		// this = obj
		setTimeout(()=>{
			//this = obj
			setTimeout(function(){
				//this = window
				alert(this.name)  //OA
			},500)
			//this = obj
			setTimeout(()=>{
				//this = obj
				alert(this.name)  //XA
			},500)
		},500)
	}
}
obj.speak()
```

🏷2.函数调用模式

```
var name = "window";
function sayName() {
   console.log(this.name);
}
sayName();
当一个函数并非一个对象的属性时；那么他就会被当作函数来调用。
这种模式下，this会被绑定为全局对象。这里this就代表window对象本身。
```

🏷3.构造函数模式

```
function Obj() {
  this.name = "kxy";
}
var person = new Obj();
console.log(person.name);  //kxy
ObJ作为构造函数被使用，函数体内的this被绑定为新创建的person对象。
```

4.apply调用模式

```
var name = "window";
var person = {
  name: "kxy"
};
function sayName() {
  console.log(this.name);
}
sayName();  //window
sayName.apply(person);  //kxy
sayName.apply();  //window

当用apply模式调用sayName，并给他传入person参数时，sayName中的this就被绑定成了person对象。如果不给apply传入任何参数，则this代表window。
```

### 3.6回调函数

​	本质：回调函数是闭包，是将一个函数作为参数传给另一个函数

#### 3.6.1实现回调函数的基本原理

1.使用命名或者匿名函数作为回调

2.传递参数给回调函数

3.在执行之前确保回调函数是一个函数

```
function getInput(options, callback){
  allUserData.push(options);  

  //确保callback是一个函数  
  if(typeof callback === "function"){
    //调用它，既然我们已经确定了它是可调用的
     callback(options);
  }
}
```

#### 3.6.2使用this对象的方法作为回调函数的问题（还是不太懂）

```
//定义一个拥有一些属性和一个方法的对象 
//我们接着将会把方法作为回调函数传递给另一个函数
var clientData = {
  	id: 094545,
  	fullName :"Not Set",
  	//setUsrName是一个在clientData对象中的方法
  	setUserName: function (firstName, lastName){
  		//构造函数
    	//这指向了对象中的fullName属性
    	this.fullName = firstName + " " + lastName;
  	}
}
clientData.setUserName("a","b")
clientData.fullName										'a b'


function getUserInput(firstName, lastName, callback){
  //在这做些什么来确认firstName/lastName ?

  //现在存储names
  callback(firstName, lastName);
}

getUserInput("Barack","Obama",clientData.setUserName);
console.log(clientData.fullName);  //Not Set
//fullName属性将在window对象中被初始化    
console.log(window.fullName);  //Barack Obama
```

使用call和apply函数来保存this

javaScript中的每个函数都有两个方法：Call 和 Apply 。这些方法被用来设置函数内部的this对象以及给此函数传递变量。

Call 接受的第一个参数 为 用来在函数内部当作this的对象，传递给函数的参数被挨个传递。

Apply函数的第一个参数也是在函数内部作为this的对象，然而最后一个参数是传递给函数的值的数组。

```
//注意到我们增加了新的参数作为回调对象，叫做“callbackObj”
function getUserInput(firstName, lastName, callback， callbackObj){
    //在这里做些什么来确认名字

 	//把callback中的this指向了callbackObj
    callback.apply(callbackObj, [firstName, lastName]);
}
```

## 第五章：参数传递



















## 第六章：常用对象

### 5.1JSON

#### 5.1.1 json 转字符串

```js
代码										结果
var content2 = {name: 'Alice', age: 23};
JSON.stringify(content2);				'{"name":"Alice","age":23}'
typeof JSON.stringify(content2);		'string'
```
#### 5.1.2字符串转json

```
代码										结果
var a = '{"name":"Alice","age":23}'
JSON.parse(a)					{name: 'Alice', age: 23}
```



### 5.2Array对象

Array 对象用于在单个的变量中存储多个值。

创建见[1.6.1](#2.Array类型)

#### array对象方法：

   🏷forEach遍历

​		arr.forEach(function(item,index,arr){},this);

​		参数item：数组当前遍历的元素

​		参数index:数组当前遍历的元素在数组中的下标

​		参数arr：当前数组本身

​		参数this: 回调函数中this的指向

```js
var arr = ['a','b','c','d']
var obj = {a:1}

arr.forEach(function(item,index,arr){
    console.log(index)
    console.log(obj)  //打印obj本身
},obj)
```

​	🏷push:向数组的末尾添加一个或更多元素，并返回新的长度。

```js
代码										返回值
var arr = new Array();
arr.push([1,2,3])						1
arr										[Array(3)]0: (3) [1, 2, 3]length: 1[[Prototype]]: Array(0)
arr.push(4,5,6)							4
```

​	unshift:  将新元素添加到数组的开头，并返回新的长度。

```js
代码										返回值
arr.unshift(15)								2
arr
									(2) [15, Array(3)]
										0: 15
										1: (3) [1, 2, 3]
```

  sort：排序函数

```
array.sort(sortfunction)
list.sort((a,b)=>{return a.id-b.id})
```

​	indexOf:搜索数组中的元素，并返回它所在的位置。

​	splice： 删除数组中元素(index,number)

```
let li = [0,1,2,3,4,5,6,7,8,9]
li.splice(3,1)
li								[0, 1, 2, 4, 5, 6, 7, 8, 9]
```

​	some: 方法用于检测数组中的元素是否满足指定条件（函数提供）。

​					依次执行数组的每个元素：如果有一个元素满足条件，则表达式返回*true* , 剩余的元素不会再执行检测

	list.some((item,index)=>{
	    if(item.id == id){
	    	list.splice(index,1)
	    	return true;
	    }
	})

​	findIndex：返回符合传入测试（函数）条件的数组元素索引。

```
var inde = list.findIndex(item => {
    if (item.id == id) {
    	return true
    }
})
list.splice(inde, 1)
```

​	filter:检测数值元素，并返回符合条件所有元素的数组。

	list.filter(item => {
	    if (item.name.includes(keywords)) {
	    	return item
	    }
	})

### 5.3Date对象

#### 5.3.1创建Date对象

	代码								结果
	var today = new Date()；
	today；							Sat Sep 25 2021 14:38:12 GMT+0800 (中国标准时间
	
	var b = new Date(today)

注释：Date 对象自动使用当前的日期和时间作为其初始值。

#### 5.3.2获取date内容

​	语法： date.getXxx()

```
代码									结果
var today = new Date()；
today.getDate()							25
new Date().getTime()
```

date方法链接：https://www.runoob.com/jsref/jsref-obj-date.html



```js
var date = new Date(dateSrc);
var pattern = 'yyyy-mm-dd'
let yyyy = date.getFullYear();
let mm = date.getMonth() + 1 ;
let dd = date.getDate();
if (pattern.toLowerCase() === 'yyyy-mm-dd') {
	return `${yyyy}-${mm}-${dd}`;

} else {
	var hh = date.getHours() ;
	var MM = date.getMinutes() ;
	var ss = date.getSeconds();
	return `${yyyy}-${mm}-${dd} ${hh}:${MM}:${ss}`
}
```



#### 5.3.3 计时器

1.setTimeout()

​	语法格式：setTimeout(function, milliseconds, parameter1, parameter2, ...);

​	**参数：**	

​		**第一个参数**是你要执行的 JavaScript 函数。传递函数的时候可以直接写函数，也可以引用一个命名函数，

​		**第二个参数**`milliseconds`，这将是 JavaScript 在执行代码函数之前等待的时间。

​			倘若该参数未添加，则要执行的代码会在程序空闲时调用，一般理解为最后调用

​		**其他参数**传递给可以在JavaScript 函数内部使用

​	**返回值：**

​		该函数也有一个数值类型返回值，利用clearTimeout()对其进行清除，实现停止执行javascript函数体

```
代码：
function greeting(name, role){
  console.log(`Hello, my name is ${name}`);
  console.log(`I'm a ${role}`);
}
setTimeout(greeting, 3000, "Nathan", "Software developer");
console.log("here");

结果：
    here   先打印
    Hello, my name is Nathan
    I'm a Software developer
```

setTimeout只运行一次，运行完后即结束。



疑问？

​	现在你可能会想，“为什么不直接将参数传递给函数呢？”

```js
这是因为如果你像这样直接传递参数：
setTimeout(greeting("Nathan", "Software developer"), 3000);
```

JavaScript 将立即执行函数而无需等待，因为你传递的是**==函数调用==**而不是==**函数引用**==去作为第一个参数



2.setInterval()

​		参数同上，返回一个intervalid，利用它clearInterval(intervalid)终止

​	例子：

```js
shot30(){
    for(let i=0 ;i<30;i++){
        (function(i){
            setTimeout(()=>{
            	console.log("第"+i+"次")
            },100*i)
        })(i)
    }
}
```



### 5.4 base64编解码

​	window.atob()  base64 解码 4字节变3字节

​	window.btoa()  base64 编码 3字节 变4字节  结果类型：字符串



### 5.5浏览器前端Cookie

Cookie详解：

```
<table>
<tr>
    <td>用户名：</td>
    	<td><input id="demo_input1" type="text"  name="username" value="999"/></td>
    <td>密码：</td>
    	<td><input id="demo_input2" type="text" name="pwd" value="888" /></td>
</tr>
<tr>
    <td colspan="2" align="center">
    	<input id="demo_button1" type="button" value="设置Cookie" /></td>
    <td colspan="2" align="center">
    	<input id="demo_button2" type="button" value="获取Cookie" /></td>
</tr>
</table>
```

<table>
		    <tr>
		        <td>用户名：</td>
		        <td><input id="demo_input1" type="text"  name="username" value="999"/></td>
		        <td>密码：</td>
		        <td><input id="demo_input2" type="text" name="pwd" value="888" /></td>
		    </tr>
		    <tr>
		        <td colspan="2" align="center">
					<input id="demo_button1" type="button" value="设置Cookie" /></td>
		        <td colspan="2" align="center">
					<input id="demo_button2" type="button" value="获取Cookie" /></td>
		    </tr>
		</table>

```
<script type="text/javascript">	
	    $("#demo_button1").click( function(){
	        var cookie_username=$("#demo_input1").val();
	        var cookie_password=$("#demo_input2").val();
			alert(cookie_username+cookie_password)
			
	        setCookie("username",cookie_username,30);
			setCookie("password",cookie_password,30);
	    })
		$("#demo_button2").click( function(){
		   var name = getCookie("username");
		   var pass = getCookieObj().password ;
		   alert(name+''+pass) ;
		})
</script>
```

工具包：util.js

```
/**
 *  func  getCookie()  获取单个cookie的值
 *  pram  cookieName  cookie的名称
 **/
 // 用法  getCookie("name");
function getCookie(cookieName) {
	var cookieObj = {},
		cookieSplit = [],
		// 以分号（;）分组
		cookieArr = document.cookie.split(";");
	for (var i = 0, len = cookieArr.length; i < len; i++)
		if (cookieArr[i]) {
			// 以等号（=）分组
			cookieSplit = cookieArr[i].split("=");
			// Trim() 是自定义的函数，用来删除字符串两边的空格
			cookieObj[cookieSplit[0].trim()] = cookieSplit[1].trim();
		}
	return cookieObj[cookieName];
}
/**
 *  func  getCookieObj()  获取所有cookie的值并将其保存为对象的属性
 **/
 // 用法
 //  	var cookieObj=getCookieObj();
 // 	cookieObj.name;
function getCookieObj() {
	var cookieObj = {},
		cookieSplit = [],
		// 以分号（;）分组
		cookieArr = document.cookie.split(";");
	for (var i = 0, len = cookieArr.length; i < len; i++)
		if (cookieArr[i]) {
			// 以等号（=）分组
			cookieSplit = cookieArr[i].split("=");
			// Trim() 是自定义的函数，用来删除字符串两边的空格
			cookieObj[cookieSplit[0].trim()] = cookieSplit[1].trim();
		}
	return cookieObj;
}
// 使用方法：setCookie('username','Darren',30)
function setCookie(c_name, value, expiredays){
　　　　var exdate=new Date();
　　　　exdate.setDate(exdate.getDate() + expiredays);
　　　　document.cookie=c_name+ "=" + escape(value) + ((expiredays==null) ? "" : ";expires="+exdate.toGMTString());
　　}


```



## 第六章:DOM

### 6.1获取对象文本内容

​	格式  读 ： innerXXX

​				写： innerXXX = xxx

```html
<div class="outer">
    <div class="middle">
        人点烛，鬼吹灯
        <div class="inner">
        	"寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"
        </div>
    </div>
</div>
```

​	 innerHTML:  

​						设置或获取标签所包含的HTML+文本信息

​						(从标签起始位置到终止位置全部内容，包括HTML标签，但不包括标签自身)

```js
var idname = document.querySelector(".inner") ;
idname.innerHTml ==> "寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"

var idname = document.querySelector(".middle") ;
idname.innerHTml ==> "人点烛，鬼吹灯"
					<div class="inner"> "寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。" </div>

var idname = document.querySelector(".outer") ;
idname.innerHTml ==>
					<div class="middle">
                        "人点烛，鬼吹灯"
						<div class="inner">
							"寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"
						</div>
					</div>
```

​	innerText:

​					设置或获取标签所包含的文本信息

​				（从标签起始位置到终止位置的内容，去除HTML标签，但不包括自身）

```js
var idname = document.querySelector(".inner") ;
idname.innerText ==> "寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"

var idname = document.querySelector(".middle") ;
idname.innerText ==> "人点烛，鬼吹灯""寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"

var idname = document.querySelector(".outer") ;
idname.innerText ==> "人点烛，鬼吹灯""寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"
```

​	outerHTML: 设置或获取标签自身及其所包含的HTML+文本信息（包括自身）

```js
var idname = document.querySelector(".inner") ;
idname.outerHTML ==> <div class="inner">
							"寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"
						</div>

var idname = document.querySelector(".middle") ;
idname.outerHTML ==> <div class="middle">
                        "人点烛，鬼吹灯"
						<div class="inner">
							"寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"
						</div>
					</div>

var idname = document.querySelector(".outer") ;
idname.outerHTML ==>  <div class="outer">
                           <div class="middle">
                                人点烛，鬼吹灯
                                <div class="inner">
                                    "寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"
                                </div>
                            </div>
                        </div>
```

​	outerText: 设置或获取标签自身及其所包含的文本信息（包括自身）

```js
var idname = document.querySelector(".inner") ;
idname.outerText ==> "寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"

var idname = document.querySelector(".middle") ;
idname.outerText ==>"人点烛，鬼吹灯""寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"

var idname = document.querySelector(".outer") ;
idname.outerText ==> "人点烛，鬼吹灯""寻龙千万看缠山，一重山是一重关；关门若有千重锁，定有王侯居此间。"
```

### 6.2表单的取值	

​	1. input 取值

```
<input type="text" id="url" value="https://www.baidu.com/">
var targeurl = document.getElementById("url").value;
```

### 6.3自动聚焦

```js
<input autofocus="autofocus" id="input">
//or js
document.getElementById('input').focus();//我执行这句语句的时候光标没有自动聚焦，还是blur状态
```

### 6.3样式style

```
document.getElementById('input').style.color ='red';
```

### 6.4元素拖曳

https://www.cnblogs.com/weiqinl/p/7886049.html

每一个可拖动的元素，在拖动过程中，都会经历三个过程，`拖动开始`-->`拖动过程中`--> `拖动结束`。

元素设置为可拖曳

​	draggable=”true"

拖动

| 针对对象     | 事件名称  | 说明                     |
| ------------ | --------- | ------------------------ |
| 被拖动的元素 | dragstart | 在元素开始被拖动时候触发 |
|              | drag      | 在元素被拖动时反复触发   |
|              | dragend   | 在拖动操作完成时触发     |

| 目的地对象 | dragenter | 当被拖动元素进入目的地元素所占据的屏幕空间时触发 |
| ---------- | --------- | ------------------------------------------------ |
|            | dragover  | 当被拖动元素在目的地元素内时触发                 |
|            | dragleave | 当被拖动元素没有放下就离开目的地元素时触发       |

释放

| 针对对象   | 事件名称 | 说明                                                         |
| ---------- | -------- | ------------------------------------------------------------ |
| 目的地对象 | drop     | 当被拖动元素在目的地元素里放下时触发，一般需要取消浏览器的默认行为。 |



```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8">
		<meta http-equiv="X-UA-Compatible" content="IE=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<title>Document</title>
		<script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></script>
		<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
	</head>
	<body>
		<style type="text/css">
			#src {
				width: 50px;
				height: 50px;
				background-color: goldenrod;
			}

			#dest {
				width: 50px;
				height: 50px;
				background-color: palegreen;
			}
		</style>
		<div id="src">
			<span draggable="true">12</span>
		</div>
		<hr>
		<div id="dest">
			<span>34</span>
		</div>
	</body>
	<script>
		//功能：
		//1.将src中的span 标签拖到dest中
		//2.删除dest中的span便签及其内容
		//3.删除src 中的span标签及其内容
		//步骤：
		//1. 定位src及dest
		var dragSrc = document.getElementById('src')
		var target = document.getElementById('dest')
		//2.src拖曳过程各个状态进行函数绑定
		//元素被开始被拖动时进行触发的函数
		// dragSrc.ondragstart = handle_start
		//元素在拖曳过程中一直会促发的函数
		// dragSrc.ondrag = handle_drag
		//元素在拖曳操作完成时进行的促发的操作，即松开鼠标就视为拖曳完成
		dragSrc.ondragend = handle_end


		function handle_start(e) {
			console.log('dragstart-在元素开始被拖动时候触发')
		}

		function handle_drag() {
			// console.log('drag-在元素被拖动时候反复触发')
		}

		function handle_end() {
			console.log('dragend-在拖动操作完成时触发')
			src.innerHTML=''
		}

		//3.src在拖曳到dest时促发的函数，这里对其进行绑定
		//当被拖动元素进入目的地元素所占据的屏幕空间时触发，从鼠标指针进入dest空间开始计算
		// target.ondragenter = handle_enter
		//当被拖动元素在目的地元素内时反复触发
		target.ondragover = handle_over
		//当被拖动元素没有放下就离开目的地元素时触发
		// target.ondragleave = handle_leave

		target.ondrop = handle_drop

		function handle_enter(e) {
			console.log('handle_enter-当元素进入目的地时触发')
			// 阻止浏览器默认行为
			e.preventDefault()
		}
		//必须的函数
		function handle_over(e) {
			console.log('handle_over-当元素在目的地时一直触发')
			// 阻止浏览器默认行为
			e.preventDefault() //必须存在不能丢
		}

		function handle_leave(e) {
			console.log('handle_leave-当元素离开目的地时触发')
			// 阻止浏览器默认行为
			// e.preventDefault()
		}

		function handle_drop(e) {
			console.log('handle_drop-当元素在目的地放下时触发')
			target.innerHTML = ''
			target.append(src.innerText)
			e.preventDefault()
		}
	</script>
</html>

```

