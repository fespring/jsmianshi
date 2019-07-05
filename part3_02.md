# port3_02 函数声明前置

在变量声明前置中，我们也涉及到了函数声明前置，再举例几个例子带大家感受下声明前置。

>先让我们回顾下，直接上题目：
```javascript
var x = 1;
console.log(x+'——'+y);  // 1——undefined 注：var y 会前置
var y=2;
```
这个是字符串拼接。

下面进入我们的函数声明前置内容中：
```javascript
function setName(){
	name="张三";  // name 没有声明，说明是全局变量，相当于在 function 上方 有一个 var name；
}
setName();
console.log(name); // 张三
```

知识点：

没有使用 var 关键字的赋值语句变量  -> 为全局变量

```javascript
var b=2;
function test2(){
	window.b=3;
	console.log(b);  //3
}
test2();
```
知识点：

window 是浏览器提供的全局对象，我们声明的全局变量 `b=2` 会挂载在 window 对象下，作为属性来存在。

我们可以将 `window.b=3` 看成是 b = 3 ；这样就好理解了，将 3 赋值 给 b 。

输出结果：3

```javascript
c=5;
function test3(){
	window.c=3;  // 
	console.log(c);  //
	var c;   
	console.log(window.c); //
}
test3();
```

```javascript

```

```javascript

```
```javascript

```