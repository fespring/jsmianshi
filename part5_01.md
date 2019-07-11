## 补充面试题

**我们在日常面试中遇到过许多面试题，下面我就在来补充一些常见的面试题** 

#### 1.

```javascript
var arr = []; //空数组
arr[0] = "a"; 
arr[1] = "b"; 
arr[10] = "c"; // 直接到下标为10的元素 中间默认补齐 为空

```
问题1：这个数组的 length 是多少？

问题2：arr[5] = ???

**问题分析：**

可以看到 一个空数组 依次往里边 赋值 

arr [0] 下标为 0 的元素 是 a

arr [1] 下标为 1 的元素 是 b 

arr [10] 下标为 10 的元素是 c

那输出 arr 数组 会得到

**["a","b",empty * 8,"c"]**	

**empty** 是空的意思，也就是 arr[1] 到 arr[10] 中间默认给补齐了，但是 是没有任何值的 所以

问题 1 的答案是 长度是 **11**

那么问题 2 就能解决了，arr[5] 是空的 访问一个不存在的元素，那输出结果肯定是 **undefined**


####2.

```javascript

console.log(a);
var a = 100;

function foo() {
    console.log(a);
    var a = 200;
    console.log(a);
}
foo();
console.log(a);


```

问题 都输出什么结果？

**问题分析：**

我们都知道 **变量** 有 **前置** 属性，**函数**也有 **前置** 属性， **变量前置** 优先于 **函数前置** 

前置是 **声明语句** 前置， **赋值不会前置**

所以上面的代码执行顺序是这样的

```javascript

var a;

console.log(a);

a = 100;

function foo(){
	
	var a;

	console.log(a);

	a = 200;

	console.log(a);

}

foo();

console.log(a);

```

所以输出的结果依次是：

**undefined**

**undefined**

**200**

**100**



####3.

```javascript

function test(){
	
	console.log(foo);
	console.log(bar);

	var foo="Hello";

	console.log(foo);

	var bar = function(){
		return "world";
	}

	function foo(){};

}

test();

```

问题 依次输出的结果？

**问题分析：**

还是上一题的 **前置** 问题

变量前置，函数内变量也前置

上述代码实际执行顺序是

```javascript

function test(){
	 var foo;
	 var bar;
	 function foo() {}

	 console.log(foo);
	 console.log(bar);

	 foo = 'Hello';
	 console.log(foo);

	 bar = function() {
	 	return 'world'; 
	 }
}

test();

```

所以输出的结果依次是：


**function(){}**

**undefined**

**Hello**





