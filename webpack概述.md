现代化的Js一般采用的是模块化的结构，模块和文件是一一对应的关系，即加载一个模块其实加载的就是一个对应的模块文件。webpack是一个JS代码模块化的打包工具，它能够通过代码模块之间的依赖关系来递归的构建一个模块依赖关系图，并将所有这些模块代码进行打包，最终生成一个或者多个bundle。

webpack的四个核心概念

入口(entry)
输出(output)
loader
插件(plugins)

1、入口(entry)

前面说过，webpack可以通过代码模块之间的依赖关系来递归的构建一个模块关系图，所以首先需要指定一个递归遍历的起始点，也就是入口文件。

可以通过在 webpack 配置中配置 entry 属性，来指定一个入口起点（或多个入口起点）。默认值为 ./src。

webpack.config.js

module.exports = {
  // 指定入口
  entry: './path/to/my/entry/file.js'
};


2、出口(output)

前面说过，当找到模块之间的依赖关系之后，就需要对所有这些模块进行打包，最终输入一个或者多个bundle。output 属性告诉 webpack 在哪里输出它所创建的 bundles，以及如何命名这些文件，默认值为 ./dist。

```
webpack.config.js

const path = require('path');

module.exports = {
  // 指定入口
  entry: './path/to/my/entry/file.js',
  // 指定出口
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js'
  }
};
```

3、loader

loader主要用于将不同的文件加载到js文件中，使用loader进行处理，将其他webpack无法识别的文件类型转换为webpack能够处理的有效模块，然后你就可以利用 webpack 的打包能力，对它们进行处理。


在 webpack 的配置中 loader 有两个目标：

test 属性，用于标识出应该被对应的 loader 进行转换的某个或某些文件。
use 属性，表示进行转换时，应该使用哪个 loader。

```
const path = require('path');

const config = {
  output: {
    filename: 'my-first-webpack.bundle.js'
  },
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  }
};

module.exports = config;
```

上面代码的作用就是告诉编译器：在打包之前，当遇到require()/import语句中被解析为'.txt'后缀的文件的时，需要先使用 raw-loader 转换处理一下。

4、插件(plugins)

loader 被用于转换某些类型的模块，而插件则可以用于执行范围更广的任务。插件的范围包括，从打包优化和压缩，一直到重新定义环境中的变量。插件接口功能极其强大，可以用来处理各种各样的任务。

```
webpack.config.js

const HtmlWebpackPlugin = require('html-webpack-plugin'); // 通过 npm 安装
const webpack = require('webpack'); // 用于访问内置插件

const config = {
  module: {
    rules: [
      { test: /\.txt$/, use: 'raw-loader' }
    ]
  },
  plugins: [
    new webpack.optimize.UglifyJsPlugin(),
    new HtmlWebpackPlugin({template: './src/index.html'})
  ]
};

module.exports = config;
```


参考文章：https://webpack.docschina.org/concepts/
