# 简介

Webpack 是德国开发者 Tobias Koppers 开发的模块加载器兼打包工具，webpack可以把各种资源当成一个模块，例如JS（含JSX）、coffee、样式（含less/sass）、图片等都作为模块来使用和处理。不同的模块有不同的加载器（loader）。

# 安装

首先需要安装`node.js`和`npm`。

```bash
npm install webpack -g
```

安装完成后，使用`webpack -v`查看webpack版本。

# 初始化

```bash
mkdir testapp
cd testapp
npm init
name:(testapp) <name>
author: <author>
```

随后会在该目录下生成名为`package.json`的配置文件。

可以将webpack安装在该目录下：

```bash
npm install webpack --save-dev
```

安装完成后，该目录下会生成一个`node_modules`的目录，这里面会存放通过npm安装的模块。

# 使用

在目录下创建`index.html`和`app.js`。

```html
<!-- index.html -->
<html>
<head>
	<meta charset="utf-8">
</head>
<body>
	<h1 id="app"></h1>
	<script src="build.js"></script>
	<!-- 注意这里引入的不是我们创建的文件，而是用webpack生成的文件 -->
</body>
</html>
```

```javascript
/*** app.js ***/
document.getElementById('app').innerHTML="hello world!";
```

开始打包：

```javascript
webpack app.js build.js
```

打包完成后，生成`build.js`。

可以在`app.js`中引入其他包，这样在打包时，其他包会被自动打包进`build.js`中。

```javascript
require("./button.js");
```

# 加载器（loader）

Webpack 本身只能打包 js 文件，如果要处理其他类型的文件，就需要使用 loader 进行转换。可以将 loader 理解为模块和资源的转换器，它本身是一个函数，接受源文件作为参数，返回转换的结果。这样，我们就可以通过require来加载任何类型的模块或文件，比如VUE、JSX、SASS 或图片。

譬如CSS的转换，需要引入两个 loader：

```bash
npm install css-loader style-loader --save-dev
```

然后在`app.js`中添加：

```javascript
require("./test.css");
```

打包时再添加`--modulle-bind "css=style-loader\!css-loader"`参数即可。

# 来源

[十分钟上手webpack包教包会 from 痞子达](https://www.jianshu.com/p/dabcdb41cc62)