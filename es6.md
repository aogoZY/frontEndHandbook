# Something about ES6.

> ### Promise
- 是ES6 中异步编程的一种解决方案，相比于传统的回调可以解决回调地狱的问题
- Promise 是一个对象，可以获取异步操作的消息，有三种状态：pending、fulfilled、rejected，变成fulfilled 或者rejected 的状态都称为resolved
- Promise api 有then、catch、resolve、reject、all、race

> ### Iterator
##### (1) 是什么？
- 是一种遍历器接口，部署了Iterator 接口的数据结构可以使用ES6 的for...of 进行遍历
##### (2) 在哪里
- ES6 规定，默认的Iterator 接口部署在数据结构的Symbol.iterator 属性，或者说，一个数据结构只要具有Symbol.iterator 属性就认为是可遍历的
- ES6 中原生具备遍历器接口的数据结构包含：Array、Map、Set、String、TypedArray、函数的arguments 对象、NodeList 对象
##### (3) 对象为什么不具备遍历器接口？
- 因为对象属性的遍历顺序是不确定的，需要开发者手动指定。遍历器本质上是一种线性结构，对于非线性的数据结构，部署遍历器结构就等于部署一种线性转换
##### (4) 默认调用Iterator 接口的场合
- 解构赋值
- 扩展运算符
- yield*
- 任何接受数组作为参数的场合，比如
    - for...of
    - Array.from()
    - Promise.all()、Promise.race()
    - Map()、Set()、WeakMap()、WeakSet()

> ### Generator
- 是ES6 中异步编程的一种解决方案，函数名前带星号，函数中可以使用yield 进行暂停操作
- Generator 函数中遇到yield 关键字的时候会暂停执行后面的内容，并将紧跟在yield 后面的返回值作为对象的value 值
- 调用该函数会返回一个内部指针（遍历器），执行它不会返回结果，而是返回指针对象，可以通过next 方法移动内部指针
- 利用该函数可以在任意对象上部署Iterator 接口，之后我们可以通过for of 进行访问
- Generator 函数是协程在ES6 中的实现，最大特点就是可以交出函数的执行权（即暂停执行）
```js
function *asyncJob() {
    // ...
    // 此时函数的执行权交到readFile 函数手中
    var f = yield readFile(fileA);
    // ...
}
```
> ### async & await
- 是generator 函数的语法糖
- async 函数的返回值是Promise 对象
- await 命令后面是一个Promise 对象，如果不是，会被转成一个立即resolve 的Promise 对象
- async 的实现原理就是将generator 函数和自动执行器包装在一个函数里
- async & await 相对于generator 的改进
    - 内置执行器
    - 更好的语义
    - 更广的实用性
    - 返回值是Promise，await 相当于函数内部then 命令的语法糖
