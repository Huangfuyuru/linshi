# Webpack  

### 概念

webpack 是一个现代 JavaScript 应用程序的**静态模块打包器**，当 webpack 处理应用程序时，它会递归地构建一个依赖关系图，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个bundle

##### 四个核心

##### 入口 entry

##### 输出 output

##### loader 

* 作用

  **loader 让 webpack 能够去处理那些非 JavaScript 文件** (webpack 自身只理解 JavaScript)。loader可以将所有类型的文件转换为 webpack 能够处理的有效模块，然后使用 webpack 的打包能力，进行处理。本质上,webpack loader将所有类型的文件，转换为应用程序的依赖图可以直接引用的模块。

* webpack 模块种类

  * ES2015 import 语句

  * CommonJS require() 语句

  * AMD define 和 require 语句

  * 样式 (url(...)) 或HTML文件(`<img src=...>`)中的图片链接

  * css /sass /less 文件中的 @import 语句 

    (突然想到，为什么每次都要配置css的loader一些，是因为css文件本身不是一个模块，但要是让他呈现样式一般会@import index.css这样，其实loader就是让css文件变成一个webpack 模块，这样才能使用@import进行引用)

* 使用

  必须配置 test , use 属性

  ```javascript
  const path = require('path')
  
  const config = {
      output: {
          filename: 'my.js'
      },
      module: {
          rules: [
              {test:/\.txt$/,use:'raw-loader'}
          ]
      }
  }
  module.exports = config;
  ```

  

##### 插件 plugins

* 作用

  插件🐂 🐂  可以进行打包优化、压缩、定义环境中的变量。。。也可以自己编写插件

* 使用

  想要 使用一个插件，需要require()它，然后把他添加到 plugins 数组中。多数插件可以通过选项(option)自定义。也可以在一个配置文件中因为不同目的而多次使用同一个插件，这是需要通过使用 new 操作符来创建它的一个实例。

  ```javascript
  const HtmlWebpackPlugin = require('html-webpack-plugin');
  const webpack = require('webpack');
  
  const config = {
      module: {
          rules: [
              {test: /\.txt$/,use: 'raw-loader'}
          ]
      },
      plugins: [
          new HtmlWebpackPlugin({template:'./src/index.html'})
      ]
  }
  
  module.exports = config;
  ```

  

#### 模式