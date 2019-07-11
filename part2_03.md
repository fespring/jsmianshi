## JS 中的数据类型及其转换

**Js中的数据类型一共有六种，即number、string、boolean、undefined、null、object。**


### 一、number

Number 数字类型，可以为整数，也可以是浮点数。

### 二、string

字符串由零个或多个字符构成，需要注意的是
字符串必须放在引号里（单引号或双引号）。

### 三、boolean

布尔类型        (true  false) 用来表示判断的结果

* 非零的数都表示 true , 0 表示 false。

* 非 “” 空字符串表示 true , “” 空字符串表示 false 。

### 四、undefined

指的是没有赋值的变量 （未定义）

### 五、null

值为空(空对象)

### 六、object

对象类型

* 常见的对象有array、window、document等。

### 七、数据类型的转换

**在 js 中我们经常需要知道某些变量的数据类型，并将其转换为我们所需要的数据类型。**

**数据的转换中，我们经常用到的是将变量转换成字符串或数字。**

* 转换成字符串要使用 toString（）。

* 转换成数字时，有两种方法，parseInt() 转换成整数，parseFloat() 转换成浮点数。

		例：
	
			var test = parseInt(“blue”); 			// NaN
 
			var test = parseInt(“1234blue”); 	// 1234
 
			var test = parseInt(“22.5”);   // 22

			var test = parseFloat(“1234blue”); // 1234
 
			var test = parseFloat(“22.5”); // 22.5

* NaN  跟任意数据类型运算都是   NaN 。

* undefined、null、NaN 转为数字都是 0 。

* undefined、null、NaN 转为布尔值都是 false 。

### 划重点：

* null == undefined  // true

* null == ''   //false

* null == null   //true

* !null    //true

* undefined == 0   //false

* undefined == ''   //false

* undefined == false  //false

* !undefined   //true

* false == ''  //true

* !false   //true

* false == false   //true

* !''   //true


**例：**

	1. var a;    //undefined  未定义

	2. var b = a*0;  //a 是 undefined, 转换为Number类型是NaN,结果 b 是 NaN

	3.if(b == b){    //false
		console.log(b*2+"2"-0+4);   //0*2+"2"-0+4
	  }else{
		console.log(!b*2+"2"-0+4); //!b 是 true, 所以：1*2+'2'-0+4=26
	  }
	  //注意：加的话只要有一边是字符串， 要把旁边的转换为字符串， 减乘除的一边不是数字也转为字符串。












