## part5_02 字符串出现最多的字符

下面来做一个 统计字符串中出现最多的字符

例：'aaaaaaaasddddddddfssssaaaaassdsdsfsdgdsasdssssssddddaaaa'

```javascript

function getManyChar(star) {
		var obj = {}; //遍历出的字符 存到一个空的变量里
		for ( var i = 0, l = star.length; i < l; i++ ){  //遍历出字符串中的所有字符
		var perChar = star.charAt(i); //返回在指定位置的字符
		if (obj[perChar] == undefined) { //判断对象中有没有当前字符
			obj[perChar] = 1; //没有时 赋1
		} else {
			obj[perChar] = obj[perChar] + 1; //有  次数+1
			}
		}
		var maxKey = '' , max = 0 ;
		var maxkey1 = '';
		// maxKey 存出现最多的那个字符 空
		// max 存次数最多的值
		// maxKey2 存相同次数的数
	for (var attr in obj){
		if(obj[attr] > max){ //如果次数大于 max
			max = obj[attr]; //将次数这个数 赋给 max
			maxKey = attr; //存最多的那个字符 就等于这个字符
		}
		else if(obj[attr] == max){ //判断如果出现相同的数时
			max = obj [attr]; //相同数 最大值 还是 max
			maxKey1 = attr； //另一个次数相同的字符 存到 maxKey1 中 
		}
	}
	return {
		key :  maxKey + ',' + maxKey1,
		nums : max
	}
}
var star = 'aaaaaaaasddddddddfssssaaaaassdsdsfsdgdsasdssssssddddaaaa';
var res = getManyChar(star);
console.log(res);

```