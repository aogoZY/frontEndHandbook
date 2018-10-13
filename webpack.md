# Something about webpack.

> ### About loaders
- webpack 原生只认识js 文件，想要让webpack 像对待js 一样处理其他类型的文件就需要针对指定的文件使用指定的loader 辅助操作
- 常用的loader 包含css-loader、ts-loader、babel-loader、file-loader 等

> ### About Plugin
- Plugin 是用来扩展webpack 的功能的，通过在构建流程里注入钩子实现各种各样与构建相关的事情
- 常用的Plugin 包含commons-chunk-plugin、uglifyjs-webpack-plugin、happypack-plugin 等