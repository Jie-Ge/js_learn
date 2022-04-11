【本教程视频】https://www.bilibili.com/video/BV14s411E7qf?p=2&spm_id_from=pageDriver

### 一、类型

基本类型：String、Number、boolean、undefined、null

对象类型：Object（任意对象）、Function（可以执行的对象）、Array

判断：typeof、instanceof（判断是否是对象的实例）、=== 、==

### 二、函数调用 call()/apply()

```js
function test(){
	console.log('text function!');
};
var obj = {};
// test.call(obj);
test.apply(obj); // 临时让test成为obj的方法进行调用
```

### 三、回调函数

定义：没有调用，但函数执行了

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <button id='btn'>点击</button>
    <script>
        // dom事件回调函数
        document.getElementById('btn').onclick = function(){
            alert('lalalallalala');
        };

        // 定时器回调函数
        setTimeout(function(){
            alert('heyheyhey');
        }, 2000); // 2秒后执行
    </script>
</body>
</html>
```

### 四、IIFE立即执行函数

【参考】https://blog.csdn.net/stpice/article/details/80586444

作用：不污染全局环境

```js
!(function(){}());

!(function(){})();

//传参
(function foo(arg1,arg2,...){...}(param1,param2,...));
```

### 五、this

`this` 同python中 `self`。

- 在全局作用域（没有指定调用者的）， `this` = `window`

  ```js
  function zz(){
     console.log(this);  // window对象
  }
  zz();  //这里是window调用的，window.zz()
  ```

- 在方法作用域，`this` = 调用者

- 类的方法里面，`this` = 类自己

```js
function Person(color) {
    console.log(this);
    this.color = color;
    this.getColor = function (){
        console.log(this);
    }
    this.setColor = function (color){
        console.log(this);
        this.color = color;
    }
}

Person('red'); //this是谁？ window

var p = new Person('yellow'); //this是谁？ p

p.getColor(); //this是谁？ p

var obj = {};
// 临时让setColor成为obj的方法进行调用
p.setColor.call(obj, 'black'); //this是谁？ obj

var test = p.setColor;
test(); //this是谁？ window
```

```js
function fun1(){
    function fun2() {
        console.log(this);
    }
    fun2();  //this是谁？ window
}
fun1();
```

