# 简介

HTML DOM 是：
+ HTML 的标准对象模型。
+ HTML 的标准编程接口。
+ W3C 标准。

HTML DOM 是关于如何获取、修改、添加或删除 HTML 元素的标准。

可通过 JavaScript 对 HTML DOM 进行访问。

# 节点

HTML 文档中的所有内容都是节点：
+ 整个文档是一个文档节点。
+ 每个元素是元素节点。
+ 元素内的文本是文本节点。
+ 每个属性是属性节点。
+ 注释是注释节点。

节点树中的节点彼此拥有层级关系。我们常用父（parent）、子（child）、同胞（sibling）等术语来描述这些关系。

# 方法

HTML DOM 方法是我们可以在节点上执行的动作（比如添加或修改元素）。

```javascript
getElementById(id) // 返回带有指定 ID 的元素
getElementByTagName(tag) // 返回包含带有指定标签名称的元素的节点
getElementsByTagName(tag) // 返回包含带有指定标签名称的所有元素的节点列表
getElementByClassName(class) // 返回包含带有指定类名的元素的节点
getElementsByClassName(class) // 返回包含带有指定类名的所有元素的节点列表
appendChild(node) // 添加子节点
removeChild(node) // 删除子节点
replaceChild(node1, node2) // 替换子节点
insertBefore(node1, node2) // 在指定的子节点前面插入新的子节点
createElement(tag) // 创建元素节点
createAttribute(attribute) // 创建属性节点
createTextNode(text) // 创建文本节点
getAttribute(attribute) // 返回指定的属性值
setAttribute(attribute, value) // 把指定属性设置或修改为指定的值
```


# 属性

HTML DOM 属性是我们可以在节点上设置和修改的值（比如节点的名称或内容）：
```javascript
nodeType // 节点类型（元素1，属性2，文本3，注释8，文档9）
nodeName // 节点名称（标签名或属性名）
nodeValue // 节点值（属性值和文本内容）
innerHTML // 文本值
parentNode // 节点的父节点
childNodes // 节点的子节点
firstChild // 第一个子节点
lastChild // 最后一个子节点
attributes // 节点的属性节点，比如style.color指style属性的color属性的值
```

两个特殊的属性：
```javascript
document.documentElement // 全部文档
document.body // 文档的主体
```

# 事件

可以使用 HTML DOM 为元素指定事件：
```javascript
document.getElementById("myBtn").onclick=function(){displayDate()};
```

# 实例

请点击[这里](http://www.runoob.com/htmldom/htmldom-examples.html)。