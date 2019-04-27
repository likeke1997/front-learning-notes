# 特性

js中描述属性的各种特征的东东，叫做特性，特性是内部值，一般标识为`[[attribute]]`。

+ 数据属性：包含一个数据值的位置。在这个位置可以读取和写入值。特性有：
	+ `[[Configurable]]`：表示能否删除、重新定义属性，及修改属性特性和类型，默认为true。
	+ `[[Enumerable]]`：表示能否通过`for-in`循环返回属性，默认为`true`。
	+ `[[Writable]]`：表示能否修改属性的值，默认为`true`。
	+ `[[Value]]`：包含这个属性的值，读取值时从这个位置读，写入的时候从写到这个位置，默认为`undefined`。

+ 访问器属性：不包含数据值，包含`getter`和`setter`函数。特性有：
	+ `[[Configurable]]`，`[[Enumerable]]`。
	+ `[[Get]]`：读取属性时调用的函数，默认为undefined。
	+ `[[Set]]`：写入，同上。

定义属性：
```javascript
// 定义单个属性
Object.defineProperty(
	objectname, 
	'propertyname', 
	{attributename: value, …}
);
// 定义多个属性
Object.defineProperties(
	objectname, 
	{peopertyname1:{attributename1:value1, …},…}
);
```

读取属性：
```javascript
Object.getOwnPropertyDescriptor(objectname, 'propertyname');
```

# 创建对象

js中没有类的概念，所以它的对象与基于类的语言中的对象有所不同。

js中的对象是无序属性的集合。对象的每个属性或方法都有一个名字，而每个名字都映射到一个值。

创建对象有两种：
```javascript
// 工厂模式
// 没有解决对象识别问题，即无法确定某个对象的类型
function createPerson(pro1, …) {
	var o = new Object();
	o.pro1 = value1;
	…
	p.func1 = function() {…};
	return o;
}
var person1 = createPerson('xxx', …); // 直接调用会将其添加到全局环境中
// 构造函数模式
// 将属性赋给了this对象，且没有return语句
function Person(…) {
	this.pro1 = pro1;
}
var person1 = new Person(…); // 返回一个对象并赋给person
```

任何函数只要通过new操作符调用，都可以作为构造函数，否则为普通函数。

在构造函数模式中，`person1`含有`constructor`构造函数属性，该属性指向`Person`，这意味着它的实例可以被识别为`Person`类型。`person1 instanceof Person`返回`true`。

# 原型模式

构造函数有一个缺点，每个方法会在每个实例上重新创建一遍，为了解决这个问题，可以：

```javascript
function Person() {
	this.sayName = sayName; // 引用同一个全局环境下的函数
}
function sayName() {…}
```

但是这样会定义很多个全局函数，自定义的类型也无封装性可言了，所以需要使用原型模式。
			
原型模式：创建的每个构造函数都有一个`prototype`属性，这个属性是一个指针，指向的对象是原型对象，即通过调用构造函数而创建的哪个对象实例的原型对象。

```javascript
function Person() {}
Person.prototype.pro1 = value1;
Person.prototype.func1 = function() {};
```

这样一来，`pro1`和`func1`都被添加到了`Person`的`prototype`属性中，构造函数变成了空函数，但同时创建的新对象还会具有相同的属性和方法。
	
可以通过`Person.prototype.isPrototypeOf(person1);`的返回值确定实例和原型是否有关系。取得对象原型`Object.getPrototypeOf(person1) == Person.prototype`，返回true。

在访问实例属性的时候，会先在实例中搜索，如果没找到会自动到其原型中搜索并返回值。实例中的属性会屏蔽原型中的同名属性。

删除属性：使用`delete person1.name;`会删除实例的属性，并恢复原型中同名属性的连接
属性是否存在原型中：`hasPrototypeProperty(objectname, 'propertyname');`。
属性是否存在对象中：`'property' in objectname;`，存在实例或原型中都会返回`true`。
属性是否存在实例中：`person1.hasOwnProperty('propertyname');`，来自实例会返回`true`，来自原型会返回`false`。

返回所有可枚举的属性：
```javascript
Object.keys(objectname); // 返回实例属性
Object.keys(Person.prototype); // 返回原型属性
```

设置原型属性的更简便方法：
```javascript
function Person(){ 
} 
Person.prototype = { 
	constructor : Person, // 这一行很重要
	name : "Nicholas", 
};
```

原型具有动态性，如果先创建实例后修改原型值，属性也能反映在实例中；除非重写了原型对象
构造函数和原型模式一般组合使用，前者放实例属性，后者放方法和共享属性。

# 借用原型链继承

原型链是作为实现继承的主要方法。

```javascript
SubType.prototype = new SuperType();
```

将`SubType`默认提供的原型换成`SuperType`的实例，所以新原型内的指针指向`supertype`的原型，但又包含`SubType`的原型属性。但因为`SubType`的原型的指针指向`SuperType`的一个实例，所以`SuperType`实例的属性方法会被共享。

搜索路径：实例→`SubType`原型→`SuperType`原型→`Object`原型。所有的引用类型默认都继承了Object，所以实际上所有的自定义类型都会继承Object的属性和方法。

# 借用构造函数继承

```javascript
function SuperType(name) {
	this.name = 'abc';
}
function SubType(name) {
	SuperType.call(this);
}
var instance1 = new SubType('name');
```

如此一来，`SubType`继承了`SuperType`的`name`属性。这种方法使用起来简单，但是缺点也很明显，即属性、方法都只能在函数内部定义，无法复用函数。

# 组合继承

指借用原型链继承原型的属性和方法，借用构造函数继承实例的属性。

# 原型式继承

```javascirpt
function object(o){ 
      function F(){} 
      F.prototype = o; 
      return new F(); 
}
```

在`object()`函数内部，先创建了一个构造函数`F()`，然后将其原型设置为参数对象，并返回构造函数。从本质上来讲，`object()`对对象`o`进行了一次浅复制。对象中的引用类型值是共享的。

ES5中，新增了`Object.create()`方法规范了原型式继承，第一个参数为作为新对象原型的对象，第二个参数为定义属性的对象。

# 寄生式继承

在原型式继承的基础下，新增自己的方法：

```javascript
function createAnother(original){ 
	var clone = object(original);
	clone.sayHi = function(){ alert("hi"); }; 
	return clone; 
}
```

# 寄生组合式继承

```javascript
function inheritPrototype(subType, superType){ 
	var prototype = object(superType.prototype);
	prototype.constructor = subType;
	subType.prototype = prototype; 
}
```