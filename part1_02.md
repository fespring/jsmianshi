## part1_02 检测数据类型的方法

##### 面试题中经常会考 js 数据类型检测，分享一下 js 中常用的几种方法来判断数据类型

### 数据类型分为以下两种 ：

1、基本数据类型

`String、 Number、 Boolean、 Symbol、 Undefined、 Null`

2、引用数据类型

`Object、 Function、 Array、 Date...`

基本类型也称为简单类型，指的是不同变量会分配不同的存储空间，为了便于提升变量查询速度，将其存储在栈中。

引用类型也称为复合类型，由于其值的大小会改变，将值存储在堆中。

### 怎么检测数据类型呢 ？

#### 一、typeof   检测数据类型的运算符

```console.log(typeof '');      //string

console.log(typeof 1);      //number

console.log(typeof Symbol());     //symbol

console.log(typeof true);      //boolean
 
console.log(typeof new Function());    //function

console.log(typeof undefined);     //undefined

console.log(typeof {});         //object

console.log(typeof null);     //object    无效

console.log(typeof []);         //object   无效

console.log(typeof new Date());         //object   无效

console.log(typeof new RegExp());         //object   无效
```


通过以上输出结果，可以看到 ：

对于基本类型，除 null 以外，均可以返回正确的结果。

对于引用类型，除 function 以外，一律返回 object 类型。

对于 null ，返回 object 类型。

对于 function 返回  function 类型。

#### 局限性：

1、因为 null 值表示一个空对象指针，所以这也正是使用 typeof 操作符检测 null 值时会返回 "object" 的原因，其实 null 的数据类型是 Null ; 

1、引用类型中的 数组、日期、正则 也都有属于自己的具体类型 ; 而 typeof 对于这些类型的处理，只返回了处于其原型链最顶端的 Object 类型。



#### 二、instanceof   检测某一个实例是否属于某个类


主要用来弥补 typeof 不能检测具体属于哪个对象的局限性。


```console.log("1" instanceof String);   //false

console.log(1 instanceof Number);   //false

console.log(true instanceof Boolean);   //false

console.log(null instanceof Object);   //false

console.log(undefined instanceof Object);  //false

console.log([] instanceof Array);  //true

console.log(function(){} instanceof Function);  //true

console.log({} instanceof Object);  //true
```

#### 局限性：

1、不能用于检测和处理字面量方式创建出来的基本数据类型值，即基本数据类型。

2、instanceof的特性：只要在当前实例的原型链上的对象，我们用其检测出来都为true。

#### 三、Object.prototype.toString.call()　原型链上的Object对象的toString方法

返回值的类型为string类型，是最全面也是最常用的检测数据类型的方式。


```Object.prototype.toString.call('') ;   // [object String]

Object.prototype.toString.call(1) ;    // [object Number]

Object.prototype.toString.call(true) ; // [object Boolean]

Object.prototype.toString.call(Symbol()) ; //[object Symbol]

Object.prototype.toString.call(undefined) ; // [object Undefined]

Object.prototype.toString.call(null) ; // [object Null]

Object.prototype.toString.call(new Function()) ; // [object Function]

Object.prototype.toString.call(new Date()) ; // [object Date]

Object.prototype.toString.call([]) ; // [object Array]

Object.prototype.toString.call(new RegExp()) ; // [object RegExp]

Object.prototype.toString.call(new Error()) ; // [object Error]
```







