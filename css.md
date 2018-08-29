# Knowledge of css
> ### 天生inline-block 元素
- \<input>、\<img>、\<button>、\<textarea>、\<label>
> ### 常见的行内及块级元素
- 块级元素：div、p、h1、form、ul、li
- 行内元素：span、a、label、input、img、strong、em
> ### rgba()和opacity的透明效果的区别
- opacity 默认继承
- rgba() 默认不继承
- IE9 以下都不支持

> ### px、em、rem 的区别
- px 为固定长度单位
- em 为父元素的font-size 大小
- rem 为根元素的font-size 大小

> ### reset css 和normalize.css
- reset css 是指我们为了消除浏览器默认样式而在项目中引入的全局css
- normalize.css 是reset css 的一种，它提供了一套合理的默认样式值

> ### Css 盒模型
- Css 盒模型分为两种：IE 盒模型和W3C 盒模型，两者的区别在于IE 盒模型的content 包含了padding 和border，而W3C 的content 不包含padding 和border
- 使用doctype 声明可以让浏览器以标准模式（W3C）解释盒模型
- Css3 新增box-sizing 属性，开发者可以通过这个来控制盒模型的表现

> ### Css3 新特性
- 阴影、圆角边框、边框图片、backgound 新属性、渐变、transform、过渡、动画、多列布局、媒体查询等，下面这个链接总结的很详细
- https://segmentfault.com/a/1190000010780991#articleHeader41

> ### Css 引入方式link 和@import 的区别
- link 是html 的标签 ，而@import 是css 的标签，link除了调用css外还可以有其他作用譬如声明页面链接属性，声明目录，rss等
- link支持使用Javascript控制DOM去改变样式；而@import不支持
- link是XHTML标签，无兼容问题；@import是在CSS2.1提出的，低版本的浏览器不支持
- 当一个页面被加载的时候（就是被浏览者浏览的时候），link引用的CSS会同时被加载，而@import引用的CSS会等到页面全部被下载完再被加载。

> ### Css hack
- Css 定义p 标签，字体在IE6 下为黑色，IE7 下为红色，其他为绿色
```css
p {
    color:green;
    *color:blue;
    _color:black;
}
```