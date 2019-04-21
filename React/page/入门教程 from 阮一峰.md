# 1.React的结构和导入方法

```html
<!DOCTYPE html>
<html>
  <head>
    <script src="../build/react.js"></script>
    <script src="../build/react-dom.js"></script>
    <script src="../build/browser.min.js"></script>
  </head>
  <body>
    <div id="example"></div>
    <script type="text/babel">
      // ** Our code goes here! **
    </script>
  </body>
</html>
```

引入的库共有三个：核心库`react.js` 、与DOM相关功能`react-dom.js`、JSX转为js语法`Browser.js`（实际上线时，应该放到服务器中）。

注意，`<script> `标签的 `type` 属性应为 `text/babel` 。

# 2.ReactDOM.render()

这是React最基本的方法，用于将模板转换为HTML语言，并插入指定DOM节点：

```javascript
ReactDOM.render(
	<h1>hello world</h1>,
	document.getElementById('example');
);
```

# 3.JSX语法

在上一个例子中，HTML语言直接写在js中，不加任何引号，这种HTML和js混写的形式就是JSX语法。

```javascript
var arr = [<h1>title1</h1>, <h2>title2</h2>];
ReactDOM.render(
	<div>{arr}</div>,
	document.getElementById('example')
);
```

遇到`<`用HTML规则解析，遇到`{`用js规则解析。

其中，数组会自动展开（map）。

# 4.组件

React的代码可以封装成组件`Component`，然后像插入普通HTML标签一样，在网页中插入这个组件。`React.createClass`方法用于生成一个组件：
```javascript
var HelloMessage = React.createClass({
	render: function() {
		return <h1>Hello {this.props.name}</h1>;
	}
});
```

`HelloMessage`是一个组件类，模板插入`<HelloMessage />`时，会自动生成该组件的实例。其中的render方法，用于输出组件。

注意，组件类里只能含一个顶层标签，否则会报错。

访问属性使用`this.props.propertyname`。特殊的，`class`属性要写成`className`，`for`属性要写成`htmlFor`，因为`class`和`for`是js的保留字。

`class`的`style`属性要用双层花括号括起来，一层表示js语法，一层表示样式对象：`style={{opacity: this.state.opacity}}`。

```javascript
ReactDOM.render(
	<HelloMessage name='keke' />,
	document.getElementById('example')
);
```

这样就可以创建一个该组件的实例并插入到指定节点中。

# 5.this.props.children

`this.props.children`表示组件的所有子节点：

```javascript
var NoteList = React.createClass({
	render: function() {
		return (
		<ol>
		{
			React.Children.map(this.props.children, function(child) {
				return <li>{child}</li>;
			})
		}
		</ol>
		)
	}
});
ReactDOM.render(
	<NoteList>
		<span>hello</span>
		<span>world</span>
	</NoteList>,
	document.body
);
```

如果当前组件没有子节点，返回`undefined`；一个节点，返回一个`Object`；多个节点，返回`Array`。

无论有多少子节点，都可以用`React.Children.map(this.props.children, func)`进行处理。

# 6.PropTypes

给组件类设置`PropTypes`属性，可以验证组件实例的属性是否符合要求：

```javascript
propTypes: {
	title: React.PropTypes.string.isRequired, // 规定title属性是必需的且应是字符串类型
}
```

而`getDefaultProps`方法可以用来设置组件属性的默认值：

```javascript
getDefaultProps: function() {
	return {
		title: 'hello world'; // 属性默认值为'hello world'
	}
}
```

# 7.获取真实的DOM节点

```javascript
var MyComponent = React.createClass({
	handleClick: function() {
		this.refs.myTextInput.focus(); // 设置焦点到ref属性为myTextInput的真实节点
	},
	render: function() {
		return (
			<div>
				<input type='text' ref='myTextInput' />
				<input type='button' value='focus the text input' onClick={this.handleClick} />
			</div>
		)
	}
});
```

除了`Click`事件外，React组件还支持`Change`、`KeyDown`、`Copy`、`Scroll`等事件。

 

# 8.this.state

React将组件看成是一个状态机，一开始有一个初始状态，互动后，状态变化，就会触发重新渲染UI。

```javascript
var LikeButton = React.createClass({
	getInitialState: function() {
		return {liked: false} // 初始化liked为false
	},
	handleClick: function(event) {
		this.setState({liked: !this.state.liked}); // liked变化
	},
	…
});
```

`this.props`和`this.state`都是一个对象。`this.props`表示一旦定义，就不再改变的特性。`this.state`表示随着用户互动而变化的特性。

一旦某状态值发生改变，会自动调用`this.render`方法重新渲染组件。

# 9.表单

```javascript
var Input = React.createClass({
	getInitialState: function() {
		return {value: 'Hello!'};
	},
	handleChange: function(event) {
		this.setState({value: event.target.value});
	},
	…
});
```

既然是表单，就需要使用到`this.state`。

通过`event.target.value`可以读取`<input>`、`<textarea>`、`<select>`、`<radio>`等表单元素的值。

# 10.组件的生命周期

组件的生命周期分成三个状态：

+ `Mounting`：已插入真实DOM。
+ `Updating`：正在被重新渲染。
+ `Unmounting`：已移出真实DOM。

这些周期对应着如下处理函数：

+ `componentWillMount()`：插入前。
+ `componentDidMount()`：插入后。
+ `componentWillUpdate(object nextProps, object nextState)`：重新渲染前。
+ `componentDidUpdate(object prevProps, object prevState)`：重新渲染后。
+ `componentWillUnmount()`：移出前。

处理函数是组件类的方法：`componentDidMount: function() {…};`。

# 11.AJAX

关于JQuery和Promise，看不懂，先搁着。

# 来源

[React入门教程 from 阮一峰](<http://www.ruanyifeng.com/blog/2015/03/react.html>)（使用的是2015年的React版本）
