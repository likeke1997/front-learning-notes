# 如何做好SEO

SEO（Search Engine Optimization， 搜索引擎优化）是一种利用搜索引擎的规则提高网站在有关搜索引擎内的自然排名的方式。

+ 合理利用`title`、`description`、`keywords`，搜索引擎对这三项的权重逐个减小。
```html
<head>
	<title>文档标题</title>
	<meta name="description" content="文档描述">
	<meta name="keywords" content="文档关键词1,文档关键词2,...">	
</head>
```
+ 语义化的 HTML 代码，这样利于搜索引擎理解网页。
+ 搜索引擎抓取 HTML 的顺序是从上到下，且抓取长度有限制，所以应该把重要内容的 HTML 代码放在最前面，保证重要内容被抓取到。
+ 搜索引擎不会抓取`iframe`元素中的内容，所有要少用`iframe`元素。
+ 爬虫不会抓取 js 生成的内容，所以重要内容不要用 js 输出。
+ 非装饰性图片必须设置`alt`属性，以提高可访问性。
+ 网站加载速度是搜索引擎排序的一个重要指标，所以应提高网站加载速度。

# 图片的title和alt属性的区别

+ `title`属性：当鼠标悬浮在元素上显示的文字内容。
+ `alt`属性：是`<img>`元素的特有属性，是图片内容的等价描述。当图片无法加载时显示，可以提高图片的可访问性。非装饰性图片必须设置`alt`属性。

# HTTP的几种请求方法

+ GET方法：发送一个请求来获取服务器上的某一资源。
+ POST方法：向URL指定的资源提交数据或附加新的数据。
+ PUT方法：跟POST方法相似，但PUT指定了资源在服务器上的位置，而POST没有。
+ DELETE方法：删除服务器上的某资源。
+ HEAD方法：只请求页面的头部信息。
+ OPTIONS方法：用于获取当前URL所支持的方法。请求成功后会返回包含类似“GET, POST"的信息。
+ TRACE方法：用于激发一个远程的，应用层的请求消息回路。__【?】__
+ CONNECT方法：把请求连接转换到透明的TCP/IP通。__【?】__

# 从浏览器地址栏输入URL到显示页面的过程

[从输入URL到浏览器显示页面发生了什么](https://www.cnblogs.com/kongxy/p/4615226.html)__【?】__

# 如何进行网站性能优化

+ content方面
  + 减少HTTP请求：合并文件、CSS精灵、inline Image
  + 减少DNS查询：DNS缓存、将资源分布到恰当数量的主机名
  + 减少DOM元素数量
+ Server方面
  + 使用CDN
  + 配置ETag
  + 对组件使用Gzip压缩
+ Cookie方面
  + 减小cookie大小
+ css方面
  + 将样式表放到页面顶部
  + 不使用CSS表达式
  + 使用`<link>`不使用@import
+ Javascript方面
  + 将脚本放到页面底部
  + 将javascript和css从外部引入
  + 压缩javascript和css
  + 删除不需要的脚本
  + 减少DOM访问
+ 图片方面
  + 优化图片：根据实际颜色需要选择色深、压缩
  + 优化css精灵
  + 不要在HTML中拉伸图片

