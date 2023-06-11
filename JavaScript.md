[toc]

## Outline of the JS

![标题](./img/Snipaste_2023-05-24_17-47-07.png)

## 函数 !!!

### 实参 (actual parameter)

### 形参 (formal parameter)---> 可以看作个 变量，默认值为 undef，也可以选择给 形参默认值 （undef + undef = NaN）

![标题](./img/Snipaste_2023-05-24_22-02-37.png)

### 函数的返回值

根据需求来确定要不要 返回值
`return`

- 函数内部结果 给 外部 其他程序 使用
- 到 return 后面代码不会被执行
- 没 return 的函数 默认返回值 undefined

```js
function fn() {
  return 20;
}
console.log(fn());
// 实际上 fn() = 20
```

_break ？ return ？_

- break --> 循环＋ switch
- return --> 函数

### 匿名函数 与 具名函数

```js
function () {

}
```

```js
let btn = document.querySelector("#btn");
btn.onclick = function () {
  alert("I am  匿名函数");
};
```

- 具名函数可以随便用
- 匿名函数只能 先声明 再使用
- 立即执行函数 (当年学 java 写过,第一个小括号里面可以加形参；第二个小括号是调用的作用,里面可以加实参)😊 本质是个匿名函数, 目的：防止变量污染,广泛运用在第三方包，这样可以确保 不会困扰使用者
  tip:必须要加分号; 结束，不然会报错

```js
(function () {})();
or((function () {})());
```

## 逻辑中断

```js
// 本质上，一个看到false就停止执行，一个看到true就停止执行

&&
console.log(false && age++)
// 一假则假，看到false以后，就不会再执行下面的age++

||
console/log(11 || age++)
// 一真则真，看到11 确定为true，后面的age++ 就不执行了
```

```js
function fn(x, y) {
  x = x || 0;
  y = y || 0;
  console.log(x + y);
}
// 本质上就是
function fn(x = 0, y = 0) {
  console.log(x + y);
}
```

## 对象 = 属性＋方法

无序的数据结合 object --> 所以不能用 for 循环来遍历对象
有序的数据结合 array
() --> 优先级
[] --> 数组
{} --> 对象

- 属性：增删改查 --> 查 有两种方法，另一种是当，属性值为字符串时，`obj['属性']`

- 方法： 对象里面的函数
  e.g.

```js
document.write();
```

### 遍历对象

```js
// for in 遍历数组，但不推荐
let arr = ["pink", "red", "blue"];
for (let k in arr) {
  console.log(k);
  // 得到 字符串类型的 0 / 1 / 2
  console.log(arr[k]);
}

// for in 遍历对象
let obj = {
  uname: "pink",
  age: 18,
  gender: "male",
};
for (let k in obj) {
  console.log(k);
  // 得到 属性名---> 'uname' / 'age'
  console.log(obj[k]);
  // 得到 属性值
}
```

### 内置对象 Math

```js
parseInt() & Math.floor()
parseInt()还可以放字符串

null 类似  let obj = {}
typeof(null) ---> object
```

```js
Math.random() 随机数函数，返回 0-1 之间
```

## 数据类型

简单数据类型(值类型)

- 存的值
- 栈

复杂数据类型(引用数据类型)

- 存的**地址**
- 堆
- 对象 数组 函数等等都是 复杂数据类型

图示：![标题](./img/Snipaste_2023-05-25_21-08-33.png)

```js
let obj1 = {
    age: 18
}
let obj2 = obj1
obj2.age = 20
console.log(obj1.age)
---> 20
```

图示：![标题](./img/Snipaste_2023-05-25_21-15-29.png)

## Web APIs

### const ? let ?

---> “变” / 建议数组，对象用 const 来声明

```js
const num1 = +prompt("first number:");
const num2 = +prompt("second number:");
alert(`${num1 + num2}`);
```

```js
const arr = ['red','black'] !!
arr.push('blue')
console.log(arr)
// 本质上 栈的地址没变， 说明还是原数组，那么const是可以用  （针对于复杂数据类型）

const arr = ['red','black']
arr = ['red','black', 'blue']
// 会出错！！
```

图示:
![标题](./img/Snipaste_2023-05-25_21-28-15.png)

### DOM / BOM

![标题](./img/Snipaste_2023-05-25_21-34-17.png)
DOM：操作网页标签 内容
DOM 树：
![标题](./img/Snipaste_2023-05-25_21-37-41.png)
DOM 对象:

```js
const div = document.querySelector("div");
// 注意 qs选的是第一个哦😪
const li = document.querySelector("ul li:first-child");
```

DOM 核心：把内容当作对象来处理

### CSS 选择器

```js
const li = document.querySelectorAll("ul");
// 伪数组 [li,li,li], 只有一个也是伪数组呦
// 有长度有索引号，但是没有 pop() / push() 等数组方法
for (let i = 0; i < li.length; i++) {
  console.log(li[i]);
}

// innerText / innerHTML
// 区别后者还可以识别标签，要是要改标签用后者
```

## BOM (browser object model)

![标题](./img/Snipaste_2023-05-25_23-01-50.png)
"window"

```js
window.document.querySelectorAll();
window.alert();
var num = 10;
console.log(window.num);
// var声明的变量/函数 最后都是window 的属性和方法
```

### 定时器-延时函数

```js
setInterval();
// 每隔一段时间就执行一次
setTimeout(function () {
  img.style.display = "none";
}, 2000);
// 只执行一次， 用在 开屏广告
```

### JS 执行机制

```js
console.log("1111");
setTimeout(function () {
  console.log("3333");
}, 0);
console.log("2222");
```

**单线程 多线程**

同步 与 异步

- 同步任务
- 异步任务
  ![标题](./img/Snipaste_2023-05-25_23-20-28.png)
  执行栈 的任务读取完以后，再开始任务队列

- event loop：
  由于 主线程 不断 重复获得任务，然后执行任务，再获取任务，再执行.....

### window.location

```js
location.href = 'http://www.google.com'
// 注册 成功之后，5秒钟跳转首页
// 用到的函数是  setInterval() 因为每秒要变

location.search() 拿到问好？ 后面的内容
location.hash()  拿到 # 后面的
单页面运用，页面没有变，可以更好的利用资源
location.reload()
```

```js
<script>
    const a = document.querySelector('a')
    let num = 5
    let timerId = setInterval(function(){
        num--
        a.innerHTML = `${num} 秒后回到百度`
        if (num === 0) {
            clearInterval(timerId)
            location.href = 'https://www.baidu.com'
        }
    },1000)
    // 1 秒以后才会开始setInterval()
</script>
```

### window.navigator

获取游览器自身的信息
运用：网站版页面 还是？ 移动端页面?

### window.history

游览器 后退前进按钮
history.back()
history.forward()
history.go()

## 本地存储

刷新以后，数据不会被扔掉 😪 本质上是在游览器里面存储了信息。大概 5M

```js
localStorage.setItem(key, value);
sessionStorage.setItem(key, value);
// 区别，关闭游览器以后就消失了
```

存储复杂数据类型，无法直接使用
复杂数据类型 ---> "json 字符串" (typeof --> string)，存储本地
JSON 对象，他的 key value 都是有引号，且是双引号
JSON.parse(JSON 字符串) ---> 变 对象类型

## 数组总结

![标题](./img/Snipaste_2023-05-24_18-36-29.png)

## 遍历数组 总结

map 方法 遍历数组,处理数据，返回 **“新的数组”**
和 for 遍历最大的区别，是 这个 map 有返回值

```js
const arr = ["pink", "yellow", "orange"];
const newarr = arr.map(function (ele, index) {
  return ele + " color";
});
console.log(newarr);
console.log(newarr.join("$"));
```

也可以通过 foreach 来创建新的数组

```js
const arr = ["pink", "yellow", "orange"];
const NewColors = [];
arr.forEach(function (color) {
  const NewColor = color + " color";
  NewColors.push(NewColor);
});
console.log(NewColors);
```

join 方法

```js
// 数组里面的元素 进行 拼接 成一个字符串
```

## 元字符

e.g.
`abcdef... ---> [a-z]`

正则表达式 修饰符，是否区分大小写/ 多行匹配
i 匹配不区分大小写

```js
console.log(/^java$/i.test("JAVA")); // true
```

g 全局查找,匹配所有

```js

```

## 事件

### 事件流 = 事件捕获 + 事件冒泡

事件捕获： Document ---> Element html ----> Element body ----> Element div/p/li... addEventListener 最后要加 true
事件冒泡： Document <--- Element html <--- Element body <--- Element div/p/li... 冒泡多

```js
const father = document.querySelector(".father");
const son = document.querySelector(".son");
document.addEventListener("click", function () {
  alert("i am grandpa");
});
father.addEventListener("click", function () {
  alert("i am father");
});
son.addEventListener(
  "click",
  function () {
    alert("i am son");
    // 阻止冒泡
    e.stopPropagation();
  },
  false
);
// 当一个元素触发事件后，会 依次向上调用 所有父级元素的 (同名事件 -- "例子中 只会去找 click")
// 所以会先 弹出 son -- > father -- > grandpa
e.stopPropagation(); // 阻止事件捕获 / 事件冒泡
```

### 事件解绑

匿名函数不可以结拜哦

```js
function fn() {
  alert("xxxx");
}
// L2 事件移除 解绑
btn.addEventListener("click", fn);
btn.removeaddEventListener("click", fn);
```

### 事件委托（Event Delegation）

好处： 减少注册次数，提高程序性能

**事件对象 e (event)**

```js
// XXXXevent   运用在 ul 和 form... 中，委托给父元素，e.target可以帮助我们确定点击的小例li
// e.target.style.color = 'red'
// e.target里面有个属性 tagName, 可以确定只对ul里面的小li有用

// e.type = 'click'
// e.key = 'Enter'
if (e.targer.tagName === "LI") {
  e.target.style.color = "red";
}
```

### 鼠标经过事件

mouseover / mouseout
mouseenter / mouseleave (recommand,没有冒泡)

区别:mouseenter(进出时会触发函数) 和 mousemove（只要鼠标一移动就会触发函数）

### 两种注册事件的区别

L0

L2

### 环境对象 this

- 每个函数里面都有 环境对象 this，

```js
// 普通函数的this指的是window
function fn() {
  console.log(this);
}
fn();
// 实际上 是 window.fn(), this指的就是window
// 谁调用函数，this指向的就是谁
// 箭头函数 没有this
```

## 回调函数

```js
function fn() {
  console.log("I am Callback function");
}
setInterval(fn, 1000);
// fn(函数A) 作为 参数 传给 setInterval(函数B)

box.addEventListener("click", function () {
  console.log("i am also Callback function");
});
```

## 例子：短信验证码 + 用户名验证...

```js
// flag  ---> 校验能否点击 / 节流阀
let flag = true
code.addEventListener('click', function() {
    flag = false
    if (flag) {
        .....
    }
})

```

```js
// 用blur比较少，大多情况下用 change，因为不必要一直校验很多次
<script>
    const input = document.querySelector('.input')
    input.addEventListener('blur', function(){
        console.log(111);
    })
</script>
```

```js
// 正则规则 ， 一般用于用户名
const reg = /^[a-zA-Z0-9_]{6,10}$/;
```

```js
// 最后确认
classList.contains(); // 检测 是否有某个特定的类
```

## 作用域

局部作用域 ： _ 函数作用域
_ 块作用域： 代码块 for / if .....

```js
for (let i = 0; i < 3; i++) {
  // 这里面是代码块
}
// let 声明的i 外部拿不到
// 但是 var 声明的i 外部能拿到！，var没有块作用域
```

全局作用域

- 函数中 未用 let const 这些声明的变量会被认为是全局变量，但不推荐这种写法
- 尽量减少全局变量 防止变量污染

作用域链: 本质上是底层的变量查找机制，优先查找当前作用域，没有的话就 逐级查找 父级作用域 直到 ‘全局作用域’

## JS 垃圾回收机制： 内存的分配和回收 都是自动完成的，内存不使用的时候会被垃圾回收器自动回收

内存的**生命周期**：

- 分配内存： 当我们声明变量 对象 函数时，会自动给他们分配内存。
- 内存使用： 即 读写内存，使用变量 函数等。
- 内存回收： 使用完毕，由垃圾回收器自动回收 不再使用的内存。

- 一般 全局变量，只有在关闭页面的时候，才会被回收
- 局部变量则是 ， 不用就会立马被回收

内存泄漏： 程序中分配的内存，因为某种原因未释放或无法释放 叫做 “ 内存泄漏 ”

算法说明：
栈：基本数据类型 ---> 操作系统 自动分配释放 函数的参数值等
堆：复制数据类型 ---> 由程序员 分配释放，如果程序员不释放，那么就由垃圾回收机制 回收

引用计数法 / 标记清除法
（具体见 JS 黑马 153/08:00）

- 引用计数法，会出现 嵌套引用/循环引用（实际上是 在堆里面的两个对象相互指向 ） 会造成内存泄漏
- 现代游览器 是基于 标记清除法， 理念就是 从根部（即 js 中全局对象）出发定时去扫描内存中的对象，能找到就不回收，找不到就回收。

## 闭包 = 内层函数 + 外层函数变量

```js
function outer() {
  const a = 1;
  function f() {
    console.log(a);
  }
  // f()
  return fn;
}
const fun = outer(); // 最后的outer就成功拿到了 10
fun(); // 输出 10
// 里面的
const a = 1;
function f() {
  console.log(a);
}
// 是个闭包(closure)
```

- 目的： 为了 外部 也可去访问函数内部的变量， 就在大函数里面 装个小函数，通过 return 把变量搞出去
- 运用场景： 实现数据的私有， 比如 要统计 函数调用次数，在全局变量声明
  let count 很容易被修改，可以把 count 丢函数里面

## 变量提升

仅存在 var 的变量，是 js 的一个缺陷, 把所有 var 声明的变量 丢到 到当前作用域的最前面 ，但是只提升声明，不赋值

```js
console.log(num + "件");
var num = 10;

// in fact:
var num;
console.log(num + "件");
num = 10;
```

## 函数提升

函数在声明之前就可以被调用

```js
fn();
function fn() {
  alert("a");
}
```

## 函数的参数

**动态**参数（参数不定） arguments ---> 本质上是个 伪数组，有索引号 有下标，但是没有常用的数组方法

求和： 动态参数 arguments

```js
function getSum() {
    let sum = 0
    for (i = 0; i < argu)
}
```

**剩余**参数 ----> 是个 **真数组** 用的多，且箭头函数里面没有 arguments

```js
// function getSum(...arr) {
//     console.log(arr);
// }
// getSum(1,2,3,4,5)

function getSum(a, b, ...arr) {
  console.log(arr);
}
getSum(2, 3); // the result will be none
getSum(1, 2, 3, 4, 5, 6, 7, 8); // the result will be 3,4,5,6,7,8  that is the meaning of **剩余**参数
// 此时就要求 用户必须输入两个，但是剩余的实参也可以拿过来
```

## 展开运算符 ---> 展开数组

```js
const arr = [1, 2, 3];
console.log(...arr);
Math.max(...arr);
// Math.max(arr) 是不可以的， 后面只能直接接(1,2,3)这种数组
// 用的比较少
// 运用： 求数组最大值 / 合并数组

// 数组 ---》 拆开 成对象
const todos = [
  { id: 1, name: "eat", done: true },
  { id: 2, name: "sleep", done: true },
  { id: 3, name: "coding", done: false },
  { id: 4, name: "shopping", done: false },
];

const todoObj = { id: 5, name: "aa", done: false };

console.log(...todos);
newTodos = [todoObj, ...todos];

console.log(newTodos);
```

合并数组

```js
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6, 7, 8];

const arr999 = [arr1, arr2];
console.log(arr999); // [Array(3), Array(5)]

const arr888 = [...arr1, ...arr2];
console.log(arr888); // [1, 2, 3, 4, 5, 6, 7, 8]
```

## 箭头函数

- 箭头函数写法
  目的： 函数表达式 代码简洁
  **箭头函数** 来替代 **匿名函数**

基本语法：

```js
// 以前：函数表达式
const fn = function () {
  console.log(123);
};

// 现在：  function --->  =>
const fn = (x) => {
  console.log(x);
};
fn(1);

// 只有1个形参的时候，小括号可以省掉
const fn = (x) => {
  console.log(x);
};
fn(1);

// 只有1行代码 可以省略大括号
const fn = (x) => console.log(x);
fn(1);

// 只有1行代码 可以省略return
const fn = (x, y) => x + y;
fn(1, 2);

// 可以直接 返回一个对象
const fn = function (uname) {
  return { name: uname };
};
fn("Lqiang");
// 注意 是小括号 😪
const fn = (uname) => ({ name: uname });
console.log(fn("Lqiang")); // 得到的是一个对象 {name: 'Lqiang'}
```

- 没有 arguments，有...args/arr

```js
const getSum = (...args) => {
  let sum = 0;
  for (let i = 0; i < args.length; i++) {
    sum += args[i];
  }
  return sum;
};
getSum(2, 3, 4, 5);
```

- this 问题

```js
const fn = () => console.log(this); // 并不是因为window.fn(), 所以this才是window， 而是因为 箭头函数作用域链上一级，(在这里指的是script）
fn();
---------------------------------------------------------
const obj = {
  uname: "pink",
  sayHi: () => {
    console.log(this); // 打印出来会是 window
  },
};
obj.sayHi();
```

加事件的时候( 在 DOM 事件回调函数里面 )，不推荐使用箭头函数

## 数组 解构和赋值

- 数组解构 赋值： ---> 简单来说，就是在 **批量赋值**

```js
const arr = [100, 60, 80];
const [max, min, avg] = arr;
console.log(max);
console.log(min);

// 运用: 快速交换变量
let a = 1;
let b = 2; // 注意 要加分号 ;
[b, a] = [a, b];
console.log(a, b);
```

- 数组 - 变量少，单元值多的情况

```js
const [a,b,c,d ...liqiang] = [1,2,3,4,5,6,7,8]
console.log(liqiang)   // [5, 6, 7, 8] 真数组 😪
```

## 对象 解构

```js
const obj = {
  uname: "pink",
  age: 36,
};

// 要求 声明的变量名 要和属性名一致 ，否则会underfined
const { uname, age } = obj;

console.log(uname);
console.log(age);

// 改对象解构的变量名
const { uname: username, age } = obj;
console.log(username);
console.log(age);
```

## 数组对象 解构

```js
const pig = [
  {
    uname: 'pink',
    age: 6,
  }
]
const [{uname, age}] = pig
-------------------------------------------------------
const pig = {
  name: 'pink',
  family: {
    mother: 'a'
    father: 'b'
  },
  age: 6
}
const {name, family:{mother, father}, age} = pig
```

## forEach --> 不返回数组

```js
const arr = ["pink", "red", "blue"];
arr.forEach(function (item, index) {
  console.log(item);
  console.log(index);
});
```

- 优点: 在遍历 **数组对象** 的时候， 会简单些

```js

```

### tab 栏切换 --> CSS 就能写/js

## 筛选数组 filter

筛选完以后，return 新数组

```js
const arr [10,20,30]
const Newarr = arr.filter(function(item, index) {
  return item>= 20    // 只能写 > < =
})
console.log(Newarr)  //  [20 ,30]
```

## dataset

```js
// .dataset 得到的是一个 包含所有自定义id 的对象  ，像这样子 DOMStringMap {index: '1'}
e.target.dataset;
// 那么要取 index的值 就可以
e.target.dataset.index;
```

## 深入对象

- 创建对象有三种方式

```js
// 1.
const obj = new Object();
obj.uname = "pink";
// 2.
const obj = {};

// 3.
// 通过构造函数来创建对象   好处： 快速创建多个对象
// 公共属性 抽取出来封装到一个函数里面
function Pig(name, age) {
  this.name = name;
  // this 指的是 新的空的 obj

  this.age = age;
  // return 在构造函数里面无效
}

// 当new出现， 会自动生成个 空对象
const peppa = new Pig("peppa", 6);
const mom = new Pig("mom", 30);
```

- 实例化： 使用 new 关键字 调用函数的行为被称为 **实例化** -- 实实在在把对象 ---> by 构造函数 ---> 造出来

## 实例成员 & 静态成员

实例对象： e.g. 上面的 peppa 就是个实例对象
实例成员 = 实例对象的属性 + 实例对象的方法

静态成员： 构造函数 的属性和方法

## 内置构造函数

- 引用类型 : Object / Array
- 包装类型 : String / Number / Boolean

### 基本数据类型

6 种： 字符串 / 数值 / 布尔 / undefined / null

```js
const str = "pink";
// 实践上，是这样子
const str = new String("pink");
// 也就解释了 为什么str会有属性和方法
str.length;
```

### Object

```js
const o = { uname: "pink", age: 18 };
const copying = {};
// 如果要获取对象的 属性名 和 属性值
// 思路1： 循环
// 思路2： 静态方法
Object.keys(o); // ['uname', 'age']
Object.values(o);

Object.assign(copying, o);
// 运用： 给原本的对象 追加n个属性
```

### Array

![标题](./img/Snipaste_2023-06-01_16-31-50.png)

reduce: 返回 累积处理结果， 运用场景： 求和

```js
const arr = [1, 5, 8];

arr.reduce(function (prev, current) {
  return prev + current;
}, 10);

const total = arr.reduce((prev, cur) => prev + current, 10);
console.log(total);
```

- 方法
  ![标题](./img/Snipaste_2023-06-01_16-56-40.png)

```js
const arr = ["red", "green", "yellow"];
const re = arr.find(function (item) {
  return item === "green";
});

// 运用场景， 数组对象， 根据某个条件，把对象取出来
const arr = [
  {
    name: "apple",
    price: 1000,
  },
  {
    name: "huawei",
    price: 1000,
  },
];
// .find 只找 第一个满足的 就return
// 下面的 item 是 所有对象
const apple = arr.find((item) => item.name === "apple");
console.log(apple); // {name:'apple', price:1000}

// join
arr = ["40cm*40cm", "Black"];
console.log(arr.join(","));

// Array.from()
// 伪数组  ---> 真数组
// 伪数组 常见于 ： 💕 ul li 的获取   💕arguments
const lis = document.querySelectorAll("ul li");
const liss = arr.from(lis);
liss.pop();
```

## 必须要加分号 ； 总结

```js
// 1. 立即执行函数
(function () {})();
// 2. 数据解构
let a = 1;
let b = 2;
[b, a] = [a, b]; // 注意 这个步骤的上一步 必须要加分号 ;
// 原理： 游览器 会认为 [b,a]还是接着上一行内容继续在写，因此，数组开头一定要注意 在前面(上一行/ 这行开头)加 ;
console.log(a, b);
```

## 0.1+0.2 为什么不等于 0.3

精度缺失， 0.1+0.2 会先转换到 二进制 再进行运算，0.1 转换成 二进制就不是原来的 0.1 了
0.1 ---> 0.00011001100.......
0.2 ---> 0.00110011001.......
但 1 和 2 的二进制不是无限循环的
所以 解决办法： (0.1*10+0.2*10)/10

## ? 条件判断

```js
newGift = gift ? xxxxxxxxxxx : "";
// Boolean(gift) = true的话 就xxxxxxxx
```

## 深入 ‘面向对象’

- 面向过程 ： 性能更高，适合跟 硬件联系紧密的东西， 前端面向过程更多

- 面向对象 : 更适合大型项目
  特性：

### 封装性

- js 通过 构造函数 来实现函数的封装
- 缺点： 存在 浪费内存 的问题， 因为存了很多 一样的 function 等复杂数据类型
- 解决方法： **原型**

### **原型**

- 能够利用原型对象实现方法的共享

- 每个构造函数都有一个 prototype， 指向另一个对象， 所以也称为 原型对象

```js
function Star(name, age) {
  this.name = name;
  this.age = age;
  this.sing = function () {
    console.log("sing");
  };
}

const lq = new Star("pink", 29);
// 原型
Star.prototype; // 是个 object
Star.prototype.sing = function () {
  console.log("sing");
};
```

- 原型对象 Star.prototype 里面的公用函数里面的 this 还是指向这里的 lq

- 解决方法： 公共的方法 写到原型身上 就可以共享

### 对象原型 **proto**

- obj 都会有个 **proto** 的属性， 会指向 ---> 原型对象
- 另一种写法 [[prototype]]

```js
ldh.__proto__ === Object.prototype; // true
dh.__proto__.constructor === Star; // true
```

![](./img/Snipaste_2023-06-02_15-54-33.png)

### constructor - 构造函数

```js
function Star(name) {}

Star.prototype.sing = function () {
  console.log("sing");
};

// 以下方法不可取，应该追加，而不是等于
// 以下方法 会把 constructor 给搞没
Star.prototype = {
  sing: function () {
    console.log("sing");
  },
  // 重新指回
  constructor: Star,
};

Star.prototype.constructor === Star(每个Star.prototype都有个constructor属性);
```

![](./img/Snipaste_2023-06-02_15-42-55.png)

- 继承性

```js
// 公共部分放到原型上
const Person = {
  eyes: 2,
  head: 1,
};

function Man() {}
// 构造函数去  继承  某个有各种属性 方法的obj
Man.prototype = Person;
// 修正 constructor 被覆盖的问题
Man.prototype.constructor = Man;

function Woman() {}
Woman.prototype = Person;
Woman.prototype.constructor = Woman;
// add some specific feature of Woman
Woman.prototype.babygiving = function () {
  console.log("skill: have a baby");
};

const Lily = new Woman();
```

- 多态性





### 额外的点

* &--位运算符 
5 & 3 
5：101
3：011

&&-- 逻辑运算符


## AJAX
不刷新网页的前提下，进行网页更新
HTTP 协议
AJAX 发的就是 HTTP 请求

ajax / jquery / fetch / axios

nodejs / express 框架

Asynchronous JavaScript And XML
异步的 JS 和 XML

好处： 提高网页加载速度，利用率

XML： HTML？
HTML 都是 预定义标签，
XML 没有预定义标签，全都是自定义标签。

现在不用XML， 被JSON 给替代了 （数据交换）  


缺点：
* SEO  源代码，响应体，， 动态创建，爬虫爬不到结果
* 跨域问题


## HTTP 协议
HyperText Transport Protocol

请求报文    重点： 格式，参数
响应报文
格式图片:
![](./img/Snipaste_2023-06-07_23-32-39.png)


接口： url   请求方法   参数
```js
// 接口 , 由 后端提供的
axios({
  url:'',
  method: 'get',
  params: {
    pname: 'HN'
  }
})
```

status code: 
1xx 信息
2xx 成功
3xx 重定向消息
4xx 客户端错误
5xx 服务端失败










