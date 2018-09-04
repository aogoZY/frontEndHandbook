# Knowledge of js
> ### 事件代理

> ### JS 模块化
##### (1) CommonJs
- 服务器端，同步加载。
- nodeJs 的模块化机制，使用exports 和require 导出和导入模块。
##### (2) AMD
- 浏览器端，异步加载。
- requireJs 为遵循AMD 的模块化工具。
- 使用define 和require 定义和加载模块。
##### (3) CMD
- 浏览器端，异步加载。
- seaJs 为遵循CMD 的模块化工具。
- AMD 与CMD 的区别在于
    - AMD 推崇依赖前置，在定义模块的时候就要声明其依赖的模块
    - CMD推崇就近依赖，只有在用到某个模块的时候再去require 
##### (3) ES6
- 使用export 和 import 导出和导入模块。
##### (4) 相关资料
- https://blog.csdn.net/crystal6918/article/details/74906757
- https://www.cnblogs.com/fayin/p/6831071.html
- https://www.cnblogs.com/goloving/p/7710951.html

> ### null 和undefined 的区别
- null 表示不存在的对象，undefined 表示存在的对象未赋值
```js
typeof null  // object
typeof undefined  // undefined
```

> ### 内置对象、原生对象、宿主对象
- 内置对象：是原生对象的一种，包含Global、Math 和JSON 等不需要new 可以直接使用的对象
- 原生对象：包含Object、Function、Array、String、Boolean、Number、Date、RegExp、Error、EvalError、RangeError、ReferenceError、SyntaxError、TypeError、URIError。简单来说，本地对象就是 ECMA-262 定义的引用类型，需要使用new 创建。（也就是说原生对象实际上包含引用类型和内置对象两种）
- 宿主对象：不是引擎的原生对象，而是由宿主框架通过某种机制注册到JavaScript 引擎中的对象，比如浏览器的window, document。

> ### apply、call、bind 的区别
- 三个方法的作用都是改变函数的执行上下文
- apply 和call 会立即执行，而bind 不会立即执行
- call() 在第一个参数之后的，后续所有参数就是传入该函数的值。apply() 只有两个参数，第一个是对象，第二个是数组，这个数组就是该函数的参数。
- bind 和call 的参数相同
- https://www.cnblogs.com/ly0612/p/6821124.html

> ### ajax 工作原理
- 通过XMLHttpRequest 对象向服务器发送异步请求，该对象包含的属性如下：
    - onreadystatechange 每次状态改变所触发事件的事件处理程序；
    - responseText 从服务器进程返回数据的字符串形式；
    - responseXML 从服务器进程返回的DOM兼容的文档数据对象；
    - status 从服务器返回的状态码（eg：200、404）
    - statusText 伴随状态码的字符串信息 （eg：200 OK）
- 通过监听readystatechange 事件来处理各个环节的响应

> ### attribute 和property
- attribute 是attributes 的子集，property 是properties 的子集；attributes 是properties 的子集
- property 是DOM中的属性，是JavaScript 里的对象；attribute 是HTML标签上的特性，它的值只能够是字符串
- 对于value 属性值来说，影响是单向的 attribute -> propery，但是两者的改动都会反映到html 中
- 对于其他属性来说，影响是双向的
- 对于新添加的非默认属性来说，互不影响
