# Something about ES6.

> ### Promise
- 是ES6 中异步编程的一种解决方案，相比于传统的回调可以解决回调地狱的问题，有三种状态：pending、fullfilled、rejected
- Promise api 有resolve、reject、all、race、done、finally

> ### Iterator

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
