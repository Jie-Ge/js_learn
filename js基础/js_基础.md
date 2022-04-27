[TOC]



### 一、类型转换

1、转为字符串：toString()、String()、+ ""

```js
var a = 123;
var b = a.toString();
var c = String(a);
var d = a + ""
```

2、转为数字：Number()、parseInt()、parseFloat()

```js
//// Number()
var a = '123';
var b = Number(a);

var c = '123ad'
var d = Number(c); // NaN。有非数字内容，转为NaN

var e = '  '
var f = Number(e); // 0。字符串全是空格，则转为0

var g = true;
var h = Number(g); // 1
var i = false;
var j = Number(i); // 0

//// parseInt(参数，进制) 转换为几进制
var a = '123';
var b = parseInt(a); // 123

var c = '123ad234'
var d = parseInt(c); // 123

var e = '  '
var f = parseInt(e); // NaN

var e = true
var f = parseInt(e); // NaN

//// parseFloat()
var a = '123.213';
var b = parseFloat(a); // 123.213

var c = '123ad123'
var d = parseFloat(c); // 123
```

### 二、相等运算符

```js
console.log('1' == 1) // true。若值的类型不同，则会自动转换为相同的类型
console.log('1' === 1) // false

console.log('1' != 1) // false。若值的类型不同，则会自动转换为相同的类型
console.log('1' !== 1) // true
```

### 三、数组

#### 1、数组添加、删除元素

```js
// push()、pop()
var arr = ['a', 'v', 'q']
var result = arr.push('w', 'b')  // 会返回数组的长度
console.log(arr) // ['a', 'v', 'q', 'w', 'b']
console.log(result) // 5 

var result = arr.pop()  // 返回pop出的元素
console.log(arr) // ['a', 'v', 'q', 'w']
console.log(result) // 'b'

// unshift()、shift() 在数组开头操作
var arr1 = ['a', 'v', 'q']
var result1 = arr1.unshift('w', 'b')  // 会返回数组的长度
console.log(arr1) // ['w', 'b', 'a', 'v', 'q']
console.log(result1) // 5

var result1 = arr1.shift()  // 返回删除的元素
console.log(arr1) // ['b', 'a', 'v', 'q']
console.log(result1) // 'w'
```

#### 2、forEach遍历

```js
var arr = ['q', 'w', 'e']
// forEach()需要一个函数作为参数，遍历到的元素会传递给形参（值，索引，数组）
arr.forEach(function (v, index, array1) {
    /*
    q 0 ['q', 'w', 'e']
    w 1 ['q', 'w', 'e']
    e 2 ['q', 'w', 'e']
    */
    console.log(v, index, array1) 
})
```

#### 3、slice() 与 splice()

1）slice(start[, end])

​	数组切片

​	**注意：** slice() 方法不会改变原始数组。

```js
var arr = ['q', 'w', 'e', 'r']
var dd = arr.slice(1, 2)
console.log(arr) // ['q', 'w', 'e', 'r']
console.log(dd) // ['w']
```

2）splice(index[, howmany, item1, ....., itemX])

​	splice() 方法用于添加或删除数组中的元素。返回指定切片位置的数组

​	howmany：如果未规定此参数，则删除从 index 开始到原数组结尾的所有元素

​	 item1, ....., itemX：要添加到数组的新元素（从切片的位置开始添加）

​	**注意：**这种方法会改变原始数组。

```js
var arr = ['q', 'w', 'e', 'r']
var dd = arr.splice(1, 2)
console.log(arr) // ['q', 'r']
console.log(dd) // ['w', 'e']

var arr1 = ['q', 'w', 'e', 'r']
var cc = arr1.splice(1, 2, 'm', 'n', 'y')
console.log(arr1) // ['q', 'm', 'n', 'y', 'r']
console.log(cc) // ['w', 'e']
```

### 四、字符串的方法

1、charAt、charCodeAt、fromCharCode

```js
str = 'Hello'
var s = str.charAt(0)  //第几个位置的字符
console.log(s) // 'H'

// 获取指定位置字符的Unicode编码
var s1 = str.charCodeAt(0)
console.log(s1) // 72

// 根据字符的Unicode编码去获取字符
var r = String.fromCharCode(72)  // 'H'
```

2、indexof()、lastIndexOf()

indexof(string[, position])  返回最开始匹配到的位置

​	position：从第几个位置开始查找

lastIndexOf()用法和indexof()一样，不同的是前者是从后往前找

```js
str = 'Hello world'
var s2 = str.indexOf('ell') // 返回最开始匹配到的位置
console.log(s2) // 1

var s3 = str.indexOf('eaa') // 匹配失败返回 -1
console.log(s3) // -1

var s3 = str.indexOf('l', 4) // 从第1个位置开始查找
console.log(s3) // 9
```

### 五、DOM

DOM（Document Object Model）文档对象模型。

作用：方便JS去操作网页（文档）（dom树、dom结点node）

### 六、BOM

BOM（Browser Object Model）浏览器对象模型。

作用：BOM可以使我们通过JS来操作浏览器

在BOM中为我们提供了一组对象，用来完成对浏览器的操作

- BOM对象：

  - window
    - 代表的是整个浏览器的窗口，同时也是网页中的全局对象
  - navigator
    - 代表的是当前浏览器的信息，通过该对象可以识别不同的浏览器
    - 不过现在不行了，一般都用userAgent来识别浏览器
  - location
    - 代表当前浏览器的地址栏信息，可以获取地址栏信息，或者操作浏览器跳转页面
      - location.href 返回当前页面的 href (URL)
      - location.hostname 返回 web 主机的域名
      - location.pathname 返回当前页面的路径或文件名
      - location.protocol 返回使用的 web 协议（http: 或 https:）
      - location.search 返回URL中从问号开始的部分（参数部分）
      - location.assign() 加载新文档（url）
      - location.reload() 重新加载当前文档
      - location.replace() 用新文档替换当前文档
  - history
    - 代表浏览器的历史记录，可以通过该对象来操作浏览器的历史记录
    - 由于隐私原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或向后翻页
    - 而且该操作只在当次访问时有效
      - history.back()
      - history.forward()
      - history.go()
  - screen
    - 代表用户的屏幕信息

  这些对象都是全局的，所以可以直接使用，也可以使用`window.`来调用

### 	七、定时器

setInterval()：定时调用

- 将一个函数每隔一段时间执行一次
- 返回值：返回一个number，作为定时器的唯一标识（可能有多个定时器）

```js
var num = 1;
// timer是一个number，作为定时器的唯一标识
var timer = setInterval(function () {
	console.log(num++);
    if(num === 10){
        clearInterval(timer); // 关闭定时器
    }
}, 1000) // 单位：毫秒
console.log(timer)
```

setTimeout()：延时调用，只会执行一次

```js
setTimeout(function () {
    console.log('延时了！！！')
}, 3000)

//clearTimeout() // 关闭定时器
```

### 八、JSON

JSON.parse() ：用于将一个 JSON 字符串转换为 JavaScript 对象。

JSON.stringify()：用于将 JavaScript 值转换为 JSON 字符串。

```js
var aa = {"name":"Runoob", "url":"www.runoob.com"}  // 对象
var bb = JSON.stringify(aa)
console.log(bb) // '{"name":"Runoob","url":"www.runoob.com"}'
console.log(typeof bb)  // 'string'

var cc = JSON.parse(bb)
console.log(cc) // 对象
console.log(typeof cc) // object
```

### 九、值传递与引用传递

我的总结：对于基本数据类型（String、Number等）传递的是值；对于对象（Object、Array等）传递的是地址，对参数进行增删改会同时修改原变量，而重新赋值就不会

```js
var rotate = function(nums, k) {
   var len = nums.length;
   var newArr = nums.splice(0, len-k)
   console.log(newArr, nums) // [1,2,3,4] [5,6,7]
   var temp = nums.concat(newArr)
   console.log(temp) //[5,6,7,1,2,3,4]
   nums = temp //[5,6,7,1,2,3,4]  对nums重新赋值，不会修改a
};

var a = [1,2,3,4,5,6,7]

rotate(a, 3)
console.log(a)  // [5, 6, 7]
```

