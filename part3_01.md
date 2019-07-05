# part3_01变量声明前置

我们先了解清楚 `Javascript` 工作方式：先解析代码，从上到下获取所有被声明的变量，然后再依次从上到下赋值

变量声明定义：变量声明前置就是在一个作用域块中，所有的变量都被放在块的开始出声明，通俗的讲：函数里面声明的变量，只是声明前置，而不会声明赋值，下面举几个例子你就明白了。


```js
alert(x);   //  undefined  变量声明前置
var x = 10; // 
```

>实际上是这个样子:

```js      
var x;     //注：声明被前置！实际是定义一个变量
alert(x);  // undefined  注：未定义的变量，所以输出了 undefined
x=10;   
```

>增加一行代码：

```js
alert(x);   //  undefined   注：变量声明前置
var x = 10; //   注：将10赋值给x
alert(x);   // 10 
```

>上面就清晰了，输出结果是 `undfined` 和 `10` ，我们再增加两行代码：

```js
alert(x);   
var x = 10; 
alert(x);  
x = 20;    
function x() {}  // 输出结果是多少呢？ 
```
>分析：首先js运行先进行解析代码，这里的变量 `var x` 会被前置；函数 `function x(){}` 也会被前置。

>小知识点：变量声明比函数声明置前。

>分析结果如下：

```js
var x；   // 变量前置
function x() {} // 函数前置，位置在变量后 
alert(x);   // function x(){}  注：输出整个函数
x = 10;    // 将10赋值给 x
alert(x);  // 10
x = 20;    
```

>最后让我们再增加一行代码，看看自己是否理解了声明前置!

```js
alert(x);   //function x(){}
var x = 10; 
alert(x);  10
x = 20;
function x() {}
alert(x);  //20
```


>再来一个例子：

```javascript
console.log(a, b); // 输出: undefined   fn b(){}
function b() {}
var a= 1;
console.log(a, b);  // 输出: undefined   fn b(){}
```


>为什么这样就会输出 `undefined` 和 `function b(){}` 呢？是因为在这个作用域执行的时候会进行变量声明前置。

```javascript
var a;   //声明被前置！实际是定义一个变量
function b() {} //定义一个方法 
console.log(a, b); // 输出: undefined   fn b(){}
a= 1; //给a赋值1
console.log(a, b);  // 输出: 1   fn b(){}
```

### 下面的例子如果可以独立完成思考，你就理解了变量前置：

```js
var a = 1;
function main() {
     console.log(a);
     var a = 2;
 }
main();
```

>调用这个函数，结果输出是 2 

>因为在这个里面，变量已经被前置了,解析结果：

```js
var a = 1;
function main() {
	 var a; //定义一个变量 a 
     console.log(a); // undefined 注：输出变量 a 
     a = 2;
 }
main();
```

#### 为什么要了解并理解变量前置

 1.面试需要。
 
 2.自己写 `Javascript` 的时候就应该将声明放在作用域开始的地方，避免出现问题。
 
### 题目:
###### 目的：加深记忆

```javascript
console.log(a); //undefined
console.log(b); //function b(){console.log(a)};
function b() {
	console.log(a); //undefined
}
b();
var a = 10;
console.log(a); //10
```

```javascript
var a=1;
function test(){
	console.log(a);
	var a=1;
}
test();
```

```javascript
var t=10;
function test(t){
	var t=t++;
	console.log(t); //10  注： t 按照从上自下顺序运行，先将自己赋值给 t，此时左面的 t 就是 10 ，所以输出的 t 就是10
}
test(t);
console.log(t); //10
```
难点题目：
```javascript
var t = 10;
fucntion test(test) {
	t = t + test;
	console.log(t);
	var t = 3;
}
test(t);
console.log(t);
```
我们分析下最后这个题目，首先是解析成如下结果：
```javascript
var t = 10;
fucntion test(test) {
	var t;
	t = t + test;
	console.log(t);
	t = 3;
}
test(t);  
console.log(t);
```
#### 分析步骤：

> 1 . 首先调用了函数 `test` 代入 `t` ，此时 `t = 10` ，可以看做是：`function test(10){}`,
> 
> 2 . 往下走，`var t`，这是声明了一个变量 t ， 
> 
> 3 . 往下走，`t = t + test`; `t` 是 未定义 也就是 `undefined` ，`test` 是 `10` 。往后面执行的话，`undefined` 会转化成数字类型 `NaN` ，`NaN` 和任何数字相加，结果都是 `NaN` ,所以执行后 ： `t = NaN`
> 
> 4 .在最后的语句，需要输出 `t` ，全局的 `t = 10` ，输出就是 `10`
> 
> 5 .最后输出结果： `NaN` `10`

###### 要时时刻刻提醒自己，在js中变量要求声明后再使用。而且js是解释性语言，它的代码执行规律，自上向下执行的。