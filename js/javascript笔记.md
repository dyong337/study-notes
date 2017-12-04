##游览器注册部分
1. shell(贝壳；外形)
2. 内核

##js三大部分
ECMAScript、DOM、BOM

##javascript特点
1. 解释性语言
2. 单线程

##轮转时间片

##主流游览器
IE  		trident
Chrome		webkit/blink
firefox  	Gecko
Opera		presto
Safari 		webkt

##如何引入js
1. 页面内嵌
	<script type=text/javascript">
	</script>
2. 外部引入文件
	<script type="text/javascript" src=""></script>

##web标准（w3c标准中的一项）结构、样式、行为相分离，通常会采用外部引入

##js基本语法
var a ;//变量声明
var b = 200;//声明变量b,并把200赋值给b
var a,
	b,
	c,
	d,
	e;
原始值(stack数据)：
 Nubmer、Boolean 、String undefined null; 
引用值heap数据)：
	array Object function ... data RegExp
	
stack:先进后出

错误：
1. 语法解析错误：
2. 逻辑错误：

短路语句：

##&&
var a = 1 &&2; //第一个表达式为真，返回第二个表达式；false，返回第一个表达式
第一语句为真，执行第二条语句；
if(2 > 1)
document.wtrite("a");
2 >1 && document.wtrite("a");
data $$ fn(data);

##||
div.onclick = function(e){
	//IE游览器中e没有值
	var event = e || window.event;
	
}

##编程形式的区别
1. 面向过程
	
2. 面向对象

##typeof()/ type a; 
##类型转换
1. 隐形类型转换
2. 显性类型转换
	var demo = Number('123');//null 为0 ，boolean值为0,1，string 类型有数值为数子，没输字为NaN；undefined为NaN
	var num = parseInt("123");//只有string类型的数子可能转换，并且为整形，保存整数位
	
	两者的区别： 1. Number转化为number;
				2. parseInt(demo,2-32);//2-32位 
				3. parseInt从数字为读到非数字位 

	toStrign():null,undefined不能使用
	
	typeof(null) : "object"
	+undefined 	:	NaN
	!!" " =true;
	
##函数(应用数据类型 )
高内聚， 弱耦合(重复)；
弱数据类型语言、解释性语言不输出地址
1. 声明函数
2. 命名函数表达式(表达式是匿名的) 
3. 匿名函数表达式

arguments --[11,2,3] 实参列表
形参参数长度--函数名.length
形参和实参列表里的值是映射关系，它变我也变
实参比形参少时，不会发生映射，arguments[funtionName.length-1] = undefined;

函数终止：return;

##js执行三部曲
1. 语法分析过程
2. 预编译:函数声明，整体提升；变量 声明提升(不赋值)；
	
		1. 情况1:输出a
		function test(){
				console.log("a");	
		}
		test();
		2. 情况2 ：输出a
		 test();
		function test(){
				console.log("a");	
		}
		3. 情况3:输出123；
		function test(){
			console.log(a);	
		}
		var a = "123";
		test();
		4. 情况:不会报错，a是全局的，只是undefined
		function test(){
			console.log(a);	
		}
		//var a = "123";
		5.
		function test(){
			var b = 123;
		}
		console.log(window.b);//输出undefined
		console.log(b);//报错b is not defined 
		
	预编译前奏
	1. imply global 暗示全局变量：即任何变量，如果变量未做声明就赋值，此变量就为全局对象所有。window.a = 10;
	2. 一切声明的全局变量，全是window的属性;window就是全局的域-
	window{
		a : 123;
	}
	function test(){
		var a = b = 123;//现将123赋值给b，再申明a，把b的值赋值给a;此处b未声明就赋值，是window的属性(全局变量)；
	}
	
	预编译过程:
	function fn(a){
			console.log(a);
			
			var a = 123;
			
			console.log(a);

			function a(){}
			
			console.log(a);

			var b = function(){}
			
			console.log(b);
			
			function d(){}
		}
		
		fn(1);
		
		//预编译发生在函数执行的前一刻
		1. 创建AO 对象 Activation Object(执行期上下文,存储空间库)
		2. 找形参和变量声明，将变量和形参名作为AO属性名，值为undefined
		3. 将实参 和形参同意
		4. 在函数体里面找函数声明，值赋予函数体
		
		AO{
			a : function a(){},//一步一般执行变化 123 
			b : undefined,		//function(){}
			d : function d(){}
		}
		
		最终输出: 
		function a(){}
		123
		123
		function b(){};
		
	函数预编译：
	全局预编译： 
		1. 生成了一个GO 对象 Global Object
		2. GO === window   
		
	if里面不能声明function
	

3. 解释执行

##作用域
函数对象 

##闭包
函数累加器
可以做缓存
实现封装，实现属性私有化
模块化开发，防止污染全局变量

1. 立即执行函数 针对初始化功能的函数：立即执行，执行完就销毁
	(function (a,b,){
	}(1,2,3))

使用方式:
(function (){}());w3c建业使用第一种
(function (){})();
只有表达式才能被执行符号执行
##


##题
1. (window.foo || window.foo = "bar")//Uncaught ReferenceError: Invalid left-hand side in assignment
2. (window.foo || (window.foo = "bar"));window.foo的值：
	解题：先看里面的括号，window.foo = "bar";最后window.foo的值为"bar" 