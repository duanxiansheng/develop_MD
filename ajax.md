```

	// 监听异步对象的响应状态
	// 0：创建了异步对象。但是还没有真正的去发送请求
	// 1.调用了send方法，正在发送请求
	// 2.send方法执行完毕了，已经收到服务器的响应内容--原始内容，还不可以使用
	// 3.正在解释数据
	// 4.响应内容解析完毕。可以使用
	
	//一个成功的响应有两个条件：1.服务器成功响应了  2.异步对象的响应状态为4(数据解析完毕可以使用了)


在js中通过JSON.parse（）方法将json格式的字符串转换为js数组或者对象：
	1.如果文件以[]来描述数据，那么就转换为数组
	2.如果文件以{}来描述数据，那么就转换为对象


节流阀
reset()重置，这是原生的，用jquery 的时候就应该在前面加[0],$('#red')[0],reset().

设置跨域请求 (在php里设置，设置响应头)
header('access-Control-Allow-Origin:*');*允许任何域
header('access-Control-Allow-Origin:http://day7.com');

1.模板在哪里创建？
   我们在script标签中创建
	// 1.设置了text/template类型，浏览器不会进行解析
	// 2.设置了id,方便后期的元素内容的获取。script本质上也是一个标签，所以可以通过dom的方式来获取里面的内容
	设置<script type="text/template" id="navTemp">
2.模板如何创建
        1.占位符可以采用<%=属性名称-值%>
        2.占位符中的值的名称一定要参照数据的属性名称
	如:<img src="<%=src%>" alt=""> <p><%=text%></p>

以前<%语法%> 现在{{语法}}

var html = template(模板id,数据(对象))
document.querySelector('ul').innerHTML = html;

artTemplate插件的使用
	调用script里template（）：如上
	调用script里有两种方法，value和items都是插件里面带的，两种引用的是不同的文件
	items是数组
	
可跨域属性有
	a里面的href和img的src，这两个属性有天然的跨域特性

1.主要是利用了script标签的天然的跨域特性来发送请求，
2.它的实现方式：在发送请求的时候传递一个函数名称给后台，后台返回数据的时候会返回一个跨域请求

面试题 jsonp的实现原理
	1.主要是利用了script的标签的天然的跨域特性来发送请求
	2.它的实现方式：在发送请求的时候传递一个函数名称给后台，后台返回数据的时候会返回这个函数的调用形式，并且在()中拼接参数
	3.ajax和jsonp的本质不一样，ajax的核心是通过XMLHttpRequest来发送请求，而jsonp是通过script标签来实现请求发送

```

### 什么是AJAX？

在页面不刷新的情况下请求服务器 ，局部刷新显示结果，不需要跳转页面。属于异步 (xhr)

说明：

> XMLHttp 客户端发送到服务器的东西称之为请求报文 ，服务端返回给客户端的东西称之为响应报文
>
> 请求报文： 
> 	1.请求行：请求方式，请求的url，协议    
> 		open（请求方式，请求url）
> 	2.请求头：客户端发送给服务器的额外信息
> 		setRequestHeader('key':'value')
> 	3.请求体：客户端传递给服务器的数据
> 		send(参数，key=value&key=value)
>
> 响应报文：
> 报文行：响应状态码，响应状态信息
> 报文头：服务器返回给客户端的一些额外信息
> 报文体：服务器返回给客户的数据 responseText：普通字符串  responseXML 符合xml格式的字符串
>
> 

示例：

```
1.var xhr = new XMLHttpRequest // 创建异步对象

2.// 设置 请求行open（请求方式，请求url,异步开关默认为true）
	// get请求如果有参数就需要在url后面拼接参数，
		xhr.open("get","validate.php?username ="+ name); 
	// post如果有参数，就在请求体中传递,post请求不需要拼接参数
		xhr.open("post","validate.php"); 
3.// 设置 请求头 setRequestHeader（'key':'value'）
		// get方式不需要设置请求头
		// post需要设置 Content-Type：application/x-www-form-urlencoded
	xhr.setRequestHeader("Content-Type","application/x-www-form-urlencoded");//post的请求头，.如果没有设置，参数无法正确的传递到服务器(本质上说，如果没有参数，也不一定需要设置，不会影响请求的发送)
4.//设置 请求体：发送请求 send(参数：key=value&key=value)
		// 如果有参数，post应该在这个位置来传递参数(如果有参数)
		// 对于get请求不需要在这个位置来传递参数，get的参数在url拼接了，所以不需要在这个函数中设置
	 xhr.send(null);// get的请求体
	// xhr.send("username="+name);post的请求体
5.	// 当异步对象的响应状态发生改变的时候，会触发一个事件： 			     //onreadystatechange js原生的方法
	xhr.onreadystatechange = function (res) {	
	 // 判断服务器是否响应      判断异步对象的响应状态
	 if(xhr.status==200 && xhr.readyState == 4) {
	 
	 }
	}
```



***

### Jquery的AJAX

语法: $.ajax({});

参数：
url 请求地址
type 请求方式
async 是否异步，默认异步
data 发送数据
dataType 服务器返回格式  默认json
timeout(毫秒) 设置请求超时.需要服务器的配合
complete 不管成功失败
error 请求失败
success 请求成功

beforeSend:function(){return:flase}发送请求之后的回调：在这个回调中我们可以进行一些请求之前的相关操作：如验证

示例1：

```
   $.ajax({
            type: "POST",
            url: "http://47.97.253.103/user/saveUser",
            data: { userid: abc[1] }, 
            dataType: "json",
            success: function(){ res => {
                console.log(res)
            }}
   });
```

示例2：

```
$.post("url",data,res =>{console.log(res)})
$.get(url,data,success,datatype):本质上只能发送get请求
```

### 问题

+ AJAX请求同步，堵塞主线程
  + H5以前。js是完成的单线程方式，主线程之外不存在其他线程。
  + 当JS加载到ajax的时候会吧页面所有的代码停止加载，页面出现假死状态。执行完成jajx后会继续运行其他代码，解除假死状态。







