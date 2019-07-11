
## 运算符和 NaN

**一、 +号**

**任何值和字符串进行加法运算, 都会先转换为字符串之后再运算**

* +号两侧都是数字类型   作用 ：求两个数字的和。

例：

	var a = 11 + 5;

	console.log(a);          // 16

* +号有一侧是字符串类型或者是引用值时 其作用都是字符串拼接。

例：

	var b = 'sed' + 'abc';
	var c = 'dfsf' + 12;
	console.log(b);       // sedabc
	console.log(c);       // dfsf12

**二、 -号**

* -号两侧都是数字类型 作用 ：求两个数字的差

* 都是转换成数字类型在进行求两个数字的差

例：

	var d = 20 - 8;
	console.log(d);          // 12

**三、 x号**

* x号两侧都是数字类型 作用 ：求两个数字的积

* 都是转换成数字类型在进行求两个数字的积

例：

	var e = 3 * 5;
	console.log(e);           // 15

**四、 /号**

* /号两侧都是数字类型 作用 ：求两个数字的商

* 都是转换成数字类型在进行求两个数字的积

例：

	var f = 10 / 2;
	console.log(f);           // 5

**五、 逗号运算符 , 结果取逗号后面的**

例1：

	var g = (1,2);
	console.log(g);          // 2

例2：

	var h = (false,true);
	var i = (true,false);
	console.log(h);       // true
	console.log(i);      // false

**六、 除了 "+" 运算符，其余的运算符（- * / %）运算时，如果符号两端是字符串，会先将字符串转为 Number 类型，再做数学运算**

**七、 NaN 跟任意数据类型运算 结果都是NaN**

* 如果一个字符串中含有除数字外的英文字母，做运算转化为 Number 类型时，字母无法转为数字，最终会得到 NaN


* NaN和 “+” 做运算，是字符串的拼接, NaN 和其余的算术运算符（- * / %）做运算，得到的都是 NaN

例1：

	var j = 'sdfg' * 3;
	console.log(j);         // NaN

例2：

	var str;
	var k = str + 3;
	console.log(k);         // NaN

例3：

	var m = 100 / NaN;
	console.log(m);         // NaN

例4：

	NaN+"11"     // "NaN11"

	NaN-11      // NaN

* NaN 和任何数据做关系运算，得到的都是 false

例：

	NaN > 0     // false






