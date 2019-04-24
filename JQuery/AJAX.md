# load()方法

`load()`方法从服务器加载数据，并把返回的数据放入被选元素中：
```javascript
$(selector).load(URL, data, callback);
```

例如：
```javascript
$("button").click(function(){
	$("#div1").load("demo_test.txt", function(responseTxt, statusTxt, xhr){
		if(statusTxt=="success")
			alert("外部内容加载成功!");
		if(statusTxt=="error")
			alert("Error: "+xhr.status+": "+xhr.statusText);
	});
});
// 回调函数中：
	// responseTxt：包含调用成功时的结果文本
	// statusTXT：包含调用的状态文本
	// xhr：包含 XHR 对象
```

# get()和post()方法

+ GET 方法基本上用于从服务器获得数据。可能会缓存数据。
+ POST 方法也可用于从服务器获取数据。但不会缓存数据，并且常用于连同请求一起发送数据。

使用方法：
```javascript
$.get(URL, callback);
$.post(URL, data, callback); 
```

例如：
```javascript
$("button").click(function(){
  $.get("demo_test.php", function(data,status){
    alert("数据: " + data + "\n状态: " + status);
  });
});
```
```javascript
$("button").click(function(){
    $.post("/try/ajax/demo_test_post.php",
    {
        name:"菜鸟教程",
        url:"http://www.runoob.com"
    },
        function(data,status){
        alert("数据: \n" + data + "\n状态: " + status);
    });
});
```


