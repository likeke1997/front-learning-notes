# 函数

基本结构：`function name(arg0, arg1, …) {…}`。

js 中不介意传递进来的参数个数和数据类型，因为参数在内部是用一个数组来标识的，函数接受的始终是数组，可以通过`arguments`对象来访问这个数组。所以实际上命名的参数只提供便利和注解，而不是必需的。

所有参数传递的都是值，不能通过引用传递参数。

函数会在执行完`return`语句之后停止并立即退出。

函数不能重载，即不能为一个函数编写多个定义。因为函数没有签名的概念（参数是由数组保存的），所以有多个同名函数时，后定义的函数会覆盖先定义的函数。

# 函数

定义函数的方式有两种：
```javascript
// 声明
sayHi();
function sayHi(){...}
// 表达式
var sayHi = function(){...}; // 匿名函数
```

关于函数声明，有一个重要特性是，函数声明提升，即执行代码sayHi()前，会先读取函数声明。

函数可以被当成值使用：`return function() {return ...;};`。

# 递归

递归函数是在一个函数通过名字调用自身的情况下构成的：
```javascript
// 在非严格模式下
function factorial(num){ 
	if (num <= 1){ 
		return 1; 
	} else { 
		return num * arguments.callee(num-1); // arguemtns.callee→factorial
	} 
}
// 无限制
var factorial = (function f(num) {
	...
	// 将arguemtns.callee替换为f即可
});
```

# 闭包

闭包是指有权访问另一个函数作用域中的变量的函数。

创建闭包的常见方式，是在一个函数内部创建另一个函数。

……