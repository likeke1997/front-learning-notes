# window对象

BOM的核心对象是`window`，他表示浏览器的一个实例。`window`对象有双重身份，一是js访问浏览器的一个接口，二是扮演了ES中规定的`Global`对象。这意味着全局变量都可以通过`window`对象访问。

区别在于，直接在`window`对象上定义的属性能通过`delete`操作符删除，而全局变量不可以。

访问框架：
```javascript
top.frames[i];
top.frames['name'];
```

跨浏览器获取窗口位置：
```javascript
var leftPos = (typeof window.screenLeft == "number") ? 
	window.screenLeft : window.screenX; 
var topPos = (typeof window.screenTop == "number") ? 
	window.screenTop : window.screenY;
```

移动窗口位置：
```javascript
// 将窗口移动到左上角
window.moveTo(0,0); 
// 将窗口向下移动100px
window.moveBy(0,100); 
// 将窗口移动到(200, 300)
window.moveTo(200,300); 
// 将窗口向左移动50px
window.moveBy(-50,0);
```

获取页面视口大小：
```javascript
var pageWidth = window.innerWidth, 
	pageHeight = window.innerHeight;
```

调整窗口大小：
```javascript
// 调整至100x100px
window.resizeTo(100, 100); 
// 宽、高分别增加100px和50px
window.resizeBy(100, 50); 
```

打开和关闭窗口：
```javascript
// 等价于< a href="http://www.wrox.com" target="topFrame"></a> 
var window1 = window.open("http://www.wrox.com/", "topFrame");
window1.close();
```

# location对象

# navigator对象

# screen对象

# history对象
