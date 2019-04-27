# 引用数据类型

引用数据类型是一种数据结构，其值（对象）是引用类型的一个实例。

```javascript
var person = new Object();
```

`new`是操作符，`Object()`是构造函数。这行代码创建了`Object`类型的一个新实例，并将实例保存在了变量`person`中。

# 基本类型和引用类型

变量松散类型的本质，决定了它只是在特定时间用于保存特定值的一个名字而已。

+ 基本数据类型：Undefined、Null、Boolean、Number、String，按值访问，是简单的数据段。
+ 引用数据类型：按引用（指针）访问，是由多个值构成的，保存在内存中的对象，所有引用类型的值都是`Object`对象类型的实例。

两者的区别：
+ 复制变量：基本数据类型`var2 = var1`会传递值的副本，两变量不会相互影响；引用会传递值的指针，即两个变量实际上将引用内存中的同一个对象，会互相影响。
+ 传递参数：参数均按值传递。
+ 检测类型：基本数据类型用`typeof`，引用用`objname instanceof type`，如`person instanceof Object|Array`。

# Object对象

`Object`是一个基础类型，其他所有类型都继承了其基本行为。

创建的方式有两种：
```javascript
// 构造函数
var person = new Object();
person.name = 'tom';
person.age = 29;
```
```javascript
// 字面量表示法
var person = {
	name: 'tom', // 属性名可使用字符串，也可以不用
	age : 29
};
```

访问属性有两种表示方法，点表示法（推荐）`person.name`以及方括号表示法`person['name']`。

# Array数组

数组内的元素可以是不同类型的，且大小可以动态调整。

创建方式有两种：
```javascript
// 构造函数
var colors = new Array();
var colors = new Array(20);
var colors = new Array('red', 'green', 'blue');
```
```javascript
// 字面量表示法：
var colors = ['red', 'green', 'blue']
```

+ 访问数组中的值，使用索引：`colors[i];`。

+ 访问数组长度：`colors.length;`，其可读可写，多余的空位用`undefined`填充。

+ 判断是否是数组：`Array.isArray(colors);`。

+ 数组的转换：
	+ `toLocalString()`，`toString()`，`valueOf()`方法都会返回以逗号分隔的字符串形式。
	+ `join(str)`方法返回以参数为分隔字符的字符串。

+ 栈方法：在js中，数组可以表现得像栈一样，后进先出，推入和弹出值发生在栈的顶部。
	+ `push()`：末端推入元素并返回数组长度，可有多个参数。
	+ `pop()`：末端弹出元素并返回该元素。

+ 队列方法：队列在列表的末端添加项，从列表的前端移除项，先进先出。
	+ `push()`。
	+ `shift()`：前端移除元素并返回该元素。
	+ `unshift()`：前端插入版的`push()`。

+ 重排序方法：
	+ `reverse()`：前后翻转数组。
	+ `sort()`：排序数组，可插入一个比较函数作为参数，如从小向大排序：
```javascript
function compare(value1, value2) { 
	if (value1 < value2) { 
		return 1; 
	} else if (value1 > value2) { 
		return -1; 
	} else { 
		return 0; 
	} 
}
```

两个方法的返回值都是经过排序后的数组。

+ 操作方法：
	+ `concat(arr)`：连接数组。
	+ `slice(i1, i2)`：返回`i1`到`i2`位置的项（不包括结束位置的项），`i2`可省略。
	+ `splice(i1, i2, el1, el2, …)`：删除从`i1`位置开始的`i2`个数的项，并在此位置上插入`e1`，`e2`，……。
		+ `arr.splice(0, 1)`：删除首项。
		+ `arr.splice(1, 0, eg1, eg2)`：在索引1元素后面添加`eg1`和`eg2`。
		+ `arr.splice(1, 1, eg)`：把索引2位置元素替换为`eg`。

+ 位置方法：
	+ `indexOf(eg, i)`：找`eg`，返回索引，没找到返回`-1`，`i`为开始查找的位置。
	+ `lastIndexOf(eg ,i)`： 倒着找。

+ 迭代方法：
	+ `forEach(func)`：对每一项执行函数 。
	+ `every(func)`：对每一项执行函数，如果每一项都返回`true`，则返回`true`。
	+ `some(func)`：对每一项执行函数，如果有任意一项返回`true`，则返回`true`。
	+ `filter(func)`：返对每一项执行函数，返回`true`项组成的数组。
	+ `map(func)`：对每一项执行函数，返回调用结果组成的数组。

`func`传入三个参数`item`，`index`，`array`。这些方法都不会修改数组。
	
+ 归并方法：
	+ `reduce(func)`：迭代，第一次1、2项，第二次第一次结果和第3项。
	+ `reduceRight(func)`：倒着迭代。

`func`传入四个参数`prev`，`cur`，`index`，`array`（第一次迭代`index`为1）。
	
# Date时间

js使用自UTC国际协调时间1970年1月1日午夜开始经过的毫秒数来保存日期。
+ GMT：天文学时间，不够准确，基本不使用。
+ UTC：原子物理时间，基本无误差，优先使用。

创建方法：
```javascript
// 构造函数
var now = new Date();
```

构造函数接收参数`Date.parse()`和`Date.UTC()`：
```javascript
var someDate = new Date(Date.parse("May 25, 2004")); // 格式种类比较多
var allFives = new Date(Date.UTC(2005, 4, 5, 17, 55, 55)); // 2005/5/5/17:55:55
```

也可以省去两个参数函数：
```javascript
var someDate = new Date('May 25, 2004');
var allFives = new Date(2005, 4, 5, 17, 55, 55);
```

获取当前时间：
```javascript
var start = Date.now();
var stop = Date.now();
var result = stop - start;
```

格式化方法：
```javascript
toDateString() // 返回星期几，月，日，年
toTimeString() // 返回时，分，秒，时区
toLocaleDateString() 
toLocaleTimeString() 
toUTCString() // 返回UTC格式日期
```

[其他方法](http://www.w3school.com.cn/js/jsref_obj_date.asp)

# RegExp正则表达

创建：
```javascript
// 构造函数
var experssion = new RegExp(pattern, flags); // 需要使用\转义
// 字面量模式
var expression = /pattern/ flags;
// flags g全局模式，i不区分大小写模式，m多行模式，可多选
```

`var pattern1 = /[bc]at/i;`与`var pattern2 = new RegExp("[bc]at", "i");`等价。

属性：
+ `global boolean`：表示flags中是否有g。
+ `ignoreCase boolean`：表示是否有i。
+ `multiline boolean`：表示是否有m。
+ `lastIndex number`：表示开始搜索的位置，从0开始。
+ `source string`：按照字面量形式返回pattern。

实例方法：
+ `exec()`：接受一个参数，即待匹配的字符串，返回值包含两个属性`index`匹配位置和`input`输入的字符串，以及一个数组，类似于python中的`groups()`。
+ `test()`：接收字符串参数，匹配成功返回`true`，失败返回`false`。

# Function函数

由于函数是对象，所以函数名实际上是一个指向函数对象的指针。`sum = null;`并不是把函数归为`null`，而是让`sum`和函数断绝关系，函数本身还是存在着的。

函数名本身是变量，所以函数可以作为值，作为参数使用。
+ 函数名加圆括号，表示返回执行结果。
+ 函数名不加圆括号，表示返回函数的指针、。

函数声明`function sum() {}`与函数表达式`var sum = function() {};`等价。
+ 解析器会率先读取函数声明，使其在任何代码之前都可访问。
+ 函数表达式则要等到执行到它所在的代码行才会被解释执行。

属性：
+ `arguments`：一个类数组对象，包含着传入的所有参数，其属性`callee`是一个指向该函数的指针。
+ `this`：引用的是函数据以执行的环境对象（函数在局部对象或全局对象`window`中）。
+ `caller`：保存着调用当前函数的函数的引用，比如`outer`函数调用了`inner`，则`inner`的`caller`指向`outer`。
+ `length`：期望的参数个数，即声明时圆括号内参数的个数。
+ `prototype`：第六章详解。

方法：
+ `apply()`：接收两个参数，作用域和参数数组。
+ `call()`：接收多个参数，第一个为作用域，后面的为其他参数。
+ `bind()` 如`var varname = somefunction.bind(objectname);`，可以创建一个函数的实例，相当于在`object`中写入`somefunction`。

# 基本包装类型

Boolean、Number、String是三个特殊的引用类型，实际上，每当读取一个基本类型值的时候，后台回自动创建一个对应的基本包装类型的对象，从而让我们能够调用一些方法来操作这些数据。例如，访问字符串时，后台会自动完成下列处理：创建String类型的一个实例→在实例上调用方法→销毁实例。

可以显式的使用`new String('xxx')`来创建基本包装类型的实例，对此调用`typeof`会返回`Object`。

`Boolean`类型：`var booleanObject = new Boolean(true);`，不建议使用。
`Number`类型：`var numberObject = new Number(10);`，不建议使用。
`String`类型：`var stringObject = new String("hello world");`。

# 单体内置对象

不依赖宿主环境的对象，在程序执行之前就存在，比如`Object`、`Array`、`String`，还有
`Global`（不属于其他对象的属性和方法，如全局属性和方法，最终都是它的属性和方法）。

Global对象：方法有`isNaN()`，`isFinite()`，`parseInt()`，`parseFloat()`，以及
`URI`编码方法和`eval()`方法。`eval()`方法只接受一个参数，会将参数当作实际的语句来解析，比如`eval("alert('hi')");`等价于`alert('hi');`。在`eval()`中创建的任何变量和函数都不会被提升，外部也访问不到内部创建的变量和函数。浏览器中一般用`window`对象扮演ECMAScript中规定的`Global`对象的角色。

Math对象：提供计算功能。
+ 属性：`E`→常量e，`LN10`→10的自然对数，`LN2`→2的自然对数，`LOG2E`，`LOG10E`，`PI`，`SQRT1_2`，`SQRT2`。
+ 方法：
	+ `min()`，`max()`：接收多个参数，返回数组的最大值：`Math.max.apply(Math, arr);`。
	+ `ceil()`，`floor()`，`round()`：分别是向上舍入，向下舍入（保留整数部分），四舍五入。
	+ `random()`：返回[0,1)区间内的一个随机数。
	+ `abs()`绝对值，`exp()`，`log()`，`pow()`，`sqrt()`，`sin()`，`asin()`，……
	