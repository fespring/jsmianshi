# 提取 URL 请求参数

**网址 URL ( uniform resource location ) 统一资源定位符** 

在 WEB 开发中，时常会用到 javascript 来获取当前页面的 url 网址信息，在这里是我的一些获取 url 信息的小总结.

下面我举例一个 UPL ，然后获得它的各个组成部分。

例：

http://www.xxxx.com/aaa.html#abc?a=1&b=2&c=&d=xxx

```
function getParameter(url) {
				var index = url.indexOf('?')	//查询参数 未找到返回-1
				var paraObj = {};

				if (index > -1) {
					var cxcs = url.substr(index + 1); //查询参数
					//var cxcs1=url.substring(index+1) //这里也可以使用 substring 方法

					var cxcsArray = cxcs.split('&'); //字符串转化成数组  输出得到 a=1,b=2,c=,d=xxx

					for (var i = 0, l = cxcsArray.length; i < l; i++) {
						
						var pa = cxcsArray[i].split('='); //在将字符串转化成数组 输出得到 a,1 b,2 c, d,xxx
						
						paraObj[pa[0]] = decodeURI(pa[1]);
					}
				}
				
				return paraObj;
			}


		alert(getParameter(url));

```

这样我们就能获取 URL 中的各个信息了。

当然还有其他的方法

**正则法**

```
function getParameter(name){
	var reg = new RegExp('(^|&)' + name + '=([^&]*)(&|$)', 'i');

	var r = window.location.search.substr(1).match(reg);

	if(r! = null){
		return unescape(r[2]);
	}

	return null;
}

alert(getParameter("参数名"));

```

**通过 window.location 属性来访问**


1、 window.location.href ( 设置或获取整个 URL 为字符串 )

```
var getParameter = window.location.href;
console.log(getParameter);

输出：http://www.xxxx.com/aaa.html#abc?a=1&b=2&c=&d=xxx

```

2、 window.location.protocol ( 设置或获取 URL 的协议部分 )

```
var getParameter = window.location.protocol;
console.log(getParameter);

输出：http:
```

3、 window.location.host ( 设置或获取 URL 的主机部分 )

```
var getParameter = window.location.host;
console.log(getParameter);

输出：www.xxxx.com

```

4、 window.location.port ( 设置或获取与 URL 关联的端口号码 )

```
var getParameter = window.location.port;
console.log(getParameter);

输出：空字符
( 如果采用默认的 80 端口( update :即使添加了: 80 )，那么返回值并不是默认的 80 而是空字符 )

```

5、 window.location.pathname ( 设置或获取与 URL 的路径部分（就是文件地址） )

```
var getParameter = window.location.pathname;
console.log(getParameter);

输出：aaa.html

```

6、 window.location.search ( 设置或获取 href 属性中跟在问号后面的部分 )

```
var getParameter = window.location.search;
console.log(getParameter);

输出：?a=1&b=2&c=&d=xxx

```

7、 window.location.hash ( 设置或获取 href 属性中在井号“#”后面的分段 )

```
var getParameter = window.location.hash;
console.log(getParameter);

输出：abc

```



















