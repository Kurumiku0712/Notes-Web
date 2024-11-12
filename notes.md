# Project

## MERN-store

### Introduction

Learn to build full-stack web applications using MongoDB, Express.js, React, and Node.js, AKA the MERN stack. This course will guide you through setting up your development environment and creating dynamic, responsive applications from scratch. You'll gain hands-on experience in building RESTful APIs, managing databases, and developing interactive front-end interfaces.

### README

Setup .env file

```
MONGO_URI=your_mongo_uri
PORT=5000
```

Run this app locally

```
npm run build
```

Start the app

```
npm run start
```



### Details

#### SetUp

in folder named Store, open vscode, open terminal

```
npm  init -y
```

do this in the root instead of in the backend: **deploy** this app easily. output: package.json



```
npm install express mongoose dotenv
```

install three libraries. Dotenv 是一个环境变量管理库，帮助我们将敏感信息（如 API 密钥、数据库密码等）保存在 `.env` 文件中

dotenv 好处: 避免硬编码敏感信息，提高 **安全性** 和 **代码可移植性**



create server.js as the entry of API

由于 `import` 是 ES6 模块的语法，要在 Node.js 环境中支持 ES6 模块语法，你需要在 `package.json` 文件中指定 `"type": "module"`，以告知 Node.js 该项目使用 ES 模块. 在哪加都行, 我选择加在scripts下面容易check

运行调试

在console输入node .\backend\server.js

等价于  在package.json里面改

 "scripts": {

  "dev": "node backend/server.js"

 },

然后在console输入 npm run dev

但是这样不会自动refresh, 为了更方便地调试引入nodemon库

```
npm i nodemon -D
```

```
  "scripts": {
    "dev": "nodemon backend/server.js"
  },
  "type": "module",
```

这样不用每次手动运行了, 保存更改的代码会自动刷新运行

```
npm run dev
```











# JS

## 基础

定义变量 let, const

打印 console.log(' '); 可以用 `+` 或 `,` 去打印; 打印空行 console.log(); 换行在中间加`\n`

`' '` 和 `" "` 都可以用来写字符串, 建议使用单引号简单方便

想要打印出单引号要用转义字符 `\`

常用 `===` 验证变量值和类型

用 `+` 即可拼接字符串

三元运算符

```js
let score = 50
let result = score >= 50 ? 'Pass':'Fail'
```



## 函数

**理解ES6箭头函数**

一般来说函数需要 function 和函数名称和参数, 可以不return只操作比如alert, 也可以return值

```js
function sum (a,b){
	return a+b
}
或
const sum = function(a, b){
    return a+b
}
```

等价于

```js
const sum = (a,b) => a+b
```

现在箭头函数很常见, 读的时候看括号就知道是参数, 箭头后面就代表函数内容和return, 如果一行就能搞定逻辑判断return也可以省略



**理解回调函数**  js里面常常会把一个函数作为参数传递给另一个函数, 回调就是回头再调用, 执行时才逻辑实现

**回调函数**（Callback Function）是指**一个函数作为参数传递给另一个函数**，并在某个时刻执行的函数。在JavaScript中，函数是一等公民，可以像变量一样传递和操作，因此回调函数的使用非常常见。回调函数的典型用途是**将逻辑的实现延迟到函数调用时再执行**，这种设计提高了代码的**灵活性**、**复用性**和**扩展性**。相比传统的硬编码逻辑，回调函数让代码更加模块化和可维护，是现代JavaScript开发中非常重要的编程技巧。

**灵活性**：回调函数让`getSumWithCondition`函数可以接受不同的条件，处理不同的逻辑。例如，这个函数不仅可以用于计算偶数之和，还可以用来计算奇数之和、质数之和等，只需改变传入的回调函数。

**代码复用**：你不需要为每个具体的条件（如偶数、奇数）都写一个新的函数。通过传递不同的回调函数，你可以使用同一个`getSumWithCondition`函数完成多种任务。

**异步处理**：回调函数在处理异步操作（如事件处理、定时器、网络请求等）时非常有用。例如，`setTimeout`、`Promise`等异步操作通常依赖回调函数，在异步任务完成时执行特定的代码。



例子

```js
console.log('使用回调函数: 输出1到100之间的所有整数之和, 偶数之和和奇数之和, 预期结果是5050, 2550和2500')
const sumWithCondition = (start, end, fn) => {
    let sum = 0
    for(let i = start; i <= end; i++){
        if(fn(i)){
            sum += i
        }
    }
    return sum
}

const sum = sumWithCondition(1, 100, () => true)
const sumOfEven = sumWithCondition(1, 100, (n) => n % 2 === 0)
const sumOfOdd = sumWithCondition(1, 100, (n) => n % 2 !== 0)

console.log('sum: ' + sum)
console.log('sumOfEven: ' + sumOfEven)
console.log('sumOfOdd: ' + sumOfOdd)
```



## **数组**

```js
console.log('array')
let arr = [2, 3, 4]
console.log('arr: ' + arr)
console.log('length of arr: ' + arr.length)
console.log('arr[0]: ' + arr[0])

arr.unshift(1)
arr.push(5)
console.log('arr after unshift and push: ' + arr)

arr.forEach((item, index) => {
    console.log('arr[' + index + ']: ' + item)
})
```

记住 unshift, push, forEach((item, index) => { })

特别是forEach乍一看有点懵, 其实就是它本身就设计为接收一个回调函数, 参数一对应数组值, 参数二对应索引

forEach可作用于普通数组, 也可以作用于对象数组 let objects = [{name: 'A'}, {name: 'B'}, {name: 'C'}]



## **对象**

```js
console.log('对象')
let obj = {
    name: 'Percy',
    age: 25
}
console.log('obj: ' + obj)
console.log('obj.name: ' + obj.name)
console.log('obj[\'name\']: ' + obj['name'])

for (let key in obj) {
    console.log(key + ': '+ obj[key])
    console.log(`${key}: ${obj[key]}`)
}
```

for..in 就是专门设计的用来遍历object的属性的



## **DOM**

DOM（Document Object Model, 文档对象模型）是**浏览器为HTML文档提供的编程接口**

**文档（HTML、CSS）**：定义了网页的静态结构和样式

**DOM**：把文档建模为一个可操作的对象模型 (元素转化为节点形成一个树状结构)

**JavaScript**：通过操作DOM来动态地修改网页内容和行为 (js控制交互, 如点击按钮、提交表单、发送消息等)

![DOM HTML tree](https://www.runoob.com/images/htmltree.gif)

![image-20241109122508135](D:\Web\assets\image-20241109122508135.png)



### 核心方法

#### querySelector

#### eventListener

#### style property





# MongoDB





















# Git





# Shortcut Key

## Typora

CTRL + SHIFT + K  代码块

CTRL + 1/2/3/4  变成标题

## VSCode

SHIFT + ALT + F  自动排版

console里面: cls  清空, CTRL + C 然后y退出运行