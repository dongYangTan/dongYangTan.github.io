<!--
 * @Date: 2024-01-25 14:48:21
 * @LastEditors: tandongyang =
 * @LastEditTime: 2024-01-31 15:15:40
 * @FilePath: /markdown/dongYangTan.github.io/docs/web/webpack5/README.md
-->
# Webpack是一个现代化的静态模块打包工具，它主要用于构建复杂的前端项目。Webpack可以将多个模块（包括JavaScript、CSS、图片等）打包成一个或多个静态资源文件，以供浏览器加载和使用

## Webpack的主要功能包括：
1) 模块打包：Webpack将项目中的各个模块视为一个整体，通过分析模块之间的依赖关系，将它们打包成一个或多个输出文件。这样可以极大地简化前端项目的资源管理和加载过程。
2) 模块转换：Webpack支持使用各种加载器（Loader）来处理不同类型的文件。加载器可以将文件转换为可被Webpack处理的模块，例如将ES6代码转换为ES5、将Sass文件转换为CSS等。
3) 插件扩展：Webpack拥有丰富的插件系统，可以通过插件来扩展和定制打包过程。插件可以用于优化资源、压缩代码、处理静态文件等，以提供更好的开发体验和性能优化。
4) 开发服务器：Webpack提供了一个开发服务器，可以在开发过程中自动编译和刷新页面。它支持热模块替换（Hot Module Replacement），可以在不刷新整个页面的情况下，只更新变化的模块，提高开发效率。
5) 代码分割：Webpack支持将代码拆分成多个块，实现按需加载，减少初始加载时间。这可以通过动态导入、异步加载等方式实现。
Webpack的配置文件是一个重要的部分，通过配置文件可以定义入口文件、输出路径、加载器、插件等。使用Webpack的配置文件，可以灵活地定制打包过程，并满足项目的需求。  
综上所述，Webpack是一个功能强大的前端构建工具，它可以帮助开发者高效地处理模块化的资源，提供优化、扩展和开发便利性等功能，是现代前端开发中不可或缺的工具之一。  


## Webpack有以下五个核心概念：
1. 入口（Entry）：入口是Webpack构建过程的起点。它指定了Webpack应该从哪个模块开始构建内部的依赖图。可以有一个或多个入口，每个入口都会生成一个最终的构建文件。（相对路径 相对于运行代码的路径 而不是webpack.config.js）  
2. 输出（Output）：输出指定了Webpack构建后生成的文件的位置和文件名。你可以定义输出文件的名称、路径和格式等。通常情况下，Webpack会根据入口文件和模块之间的依赖关系自动确定输出文件的名称。(相对路径)  
3. 加载器（Loaders）：加载器允许Webpack处理非JavaScript文件（如CSS、Sass、图片等）。加载器是在构建过程中用于转换和处理这些文件的插件。通过加载器，你可以将这些文件转换为Webpack可以理解的模块，从而将它们包含在最终的构建文件中。
4. 插件（Plugins）：插件用于执行更广泛的构建任务和自定义Webpack的构建过程。插件可以执行各种任务，如优化资源、压缩代码、生成HTML文件、提取公共模块等。Webpack提供了许多内置插件，同时也支持第三方插件。
5. 模式（Mode）：模式指定了Webpack的构建模式，可以是开发模式（development）、生产模式（production）或其他自定义模式。不同的模式会触发不同的内置优化策略，例如在生产模式下会进行代码压缩和优化，而在开发模式下会启用更有用的开发工具和错误提示。  
这些核心概念共同组成了Webpack的基本工作原理和功能，通过配置它们，你可以定义和定制你的项目的构建过程，使其更高效、灵活和符合项目的需求。

## Webpack进行打包的一般操作
```
- npm init -y     生成一个package.json文
- npm i webpack webpack-cli -D    把Webpack及其命令行工具作为开发依赖项安装到项目中
- 在webpack.config.js文件中 配置 输入输出，以及加载器 插件(UglifyJsPlugin插件来压缩和混淆你的代码) 模式
- npx webpack
使用加载器处理 CSS
- npm install css-loader style-loader --save-dev
- 在[loader 文档](https://webpack.js.org/loaders/css-loader/) 中找到css-loader 配置module: rules
    > "style-loader",//将js中的css通过创建style标签添加到html文件中生效
    > "css-loader" // 将css资源编译成commonjs加载到js中
使用加载器处理 less
- npm install less less-loader --save-dev
- 在[loader 文档]找到配置
处理s[ac]ss  stylus 同上
处理图片资源 webpack4是通过file-loader 和 url-loader进行处理。webpack5已经内置，只要配置即可
{   test: /\.(png|jpe?g|gif|svg)$/i,
    type: "asset"}
[配置图片base64]（https://www.webpackjs.com/guides/asset-modules#inlining-assets ） 对于较小的图标或背景图片等，转换为Base64编码可以提高页面加载性能。而对于较大的图片，通常建议将其作为独立的文件进行加载  

```


## webpack内插件 eslint babel使用

## [HtmlWebpackPlugin](https://www.webpackjs.com/plugins/html-webpack-plugin/)

## [webpack-dev-server](https://www.webpackjs.com/configuration/dev-server/#devserver)
如果你使用 npx webpack serve 命令启动 Webpack Dev Server，它会在内存中构建和存储你的项目，而不会生成实际的输出文件到磁盘上的 dist 目录。  
Webpack Dev Server 是一个开发服务器，它将编译后的文件存储在内存中，并通过 HTTP 服务器提供这些文件。这种方式可以实现快速的重新编译和实时刷新，以提高开发效率。  

## [MiniCssExtractPlugin](https://www.webpackjs.com/plugins/mini-css-extract-plugin)
为每个包含 CSS 的 JS 文件创建一个 CSS 文件  

## [postcss-loader](https://www.webpackjs.com/loaders/postcss-loader/#root)
是一个用于在 Webpack 构建过程中处理 CSS 的加载器。它可以让你使用 PostCSS 插件来转换、优化和增强 CSS。 

## [CssMinimizerWebpackPlugin](https://www.webpackjs.com/plugins/css-minimizer-webpack-plugin/)
这个插件使用 cssnano 优化和压缩 CSS。html和js默认生产模式下自动压缩  

## sourcemap

Webpack 的 source map（源映射）是一种文件，它存储了压缩、转换后的代码与原始源代码之间的映射关系。它允许开发者在调试过程中将错误、警告或日志消息追踪到原始源代码的位置，而不是压缩后的代码。
```
开发环境一般cheap-module-source-map，生产环境一般配置source map 类型
module.exports = {
  // ...其他配置
  devtool: 'source-map',
}
```
生成的 source map 文件将与输出文件一起生成，并在浏览器的开发者工具中使用。当你在开发过程中遇到错误或警告时，开发者工具将通过 source map 将其追踪到 **原始源代码的位置** ，以便你能够更轻松地进行调试和修复。

## [HMR-HotModuleReplacementPlugin](https://www.webpackjs.com/plugins/hot-module-replacement-plugin/)
**HMR 绝对不能被用在生产环境**  
可以在不刷新整个页面的情况下，实时更新应用程序的某个模块，从而快速查看修改的结果。这对于大型应用程序和复杂的开发场景非常有用，因为它能够节省重新构建和刷新页面的时间。    
HMR 不仅仅支持 JavaScript 模块的热替换，还可以处理样式表、模板文件以及其他类型的文件。它能够自动处理模块间的依赖关系，并确保更新的模块以正确的顺序加载和替换。  
```
module.exports = {
  // ...其他配置项
  devServer: {
    hot: true, // 启用 HMR
  },
};
webpack-dev-server 默认启用 HMR hot: true  
在生产环境中，通常会禁用 HMR
```
css可支持热更新  
在 JavaScript 中，你可以使用一些代码来检测浏览器是否支持 HMR，并根据结果来决定是否针对性地刷新某个文件或模块。
```
if (module.hot) {
  //这样只要file.js修改 就只会更新这个文件
    module.hot.accept('./path/to/file.js')
}
实际开发中可借助react-hot-loader实现
```


## oneOf
在 webpack 的配置中，oneOf 通常与 rules 配置项一起使用，用于定义不同类型文件的处理规则。当 webpack 处理某个文件时，它会按照在 oneOf 中定义的顺序依次尝试匹配，一旦匹配成功，就会停止进一步的匹配。
## include 和 exclude
webpack 配置中，include 和 exclude 是 rules 配置项中常用的属性，用于指定需要包含或排除的文件或目录。
```
module.exports = {
  // ...其他配置项
  module: {
    rules: [
      {
        test: /\.js$/,
        include: /src/, // 只处理 src 目录下的 JavaScript 文件
        exclude: /node_modules/, // 排除 node_modules 目录下的 JavaScript 文件
        use: 'babel-loader',
      },
      // 其他规则...
    ],
  },
};
```

## Cache  
[cache](https://www.webpackjs.com/configuration/cache/#cache)  
一般对babel options下添加cacheDirectory:true 来开启缓存，提升**非第一次**打包速度,另外关闭缓存压缩也能减少时间cacheCompression:false。
eslint 配置cache:true cacheLocation:path.resolve(__dirname,"./node_modules/.cache/eslintcache") 使用绝对路径，后面的路径要看配置文件基于根目录的位置，若webpack.js在根目录同级则使用./ ,若自己创建一层文件 那么要../  

## 多进程打包
能开启最大的进程是电脑的核数  
npm i thread-loader -D    
const os = require("os")  
const threads = os.cpus().length

```

{
        test: /\.js$/,
        exclude: /(node_modules)/,
        use: [
        {
            loader: 'thread-loader',
            options: {
             works: threads,
            }
        }
        ,
        {
         loader: 'babel-loader',
        }

    ]

},
eslint也可配置
new ESLintPlugin({
  context: path.resolve(__dirname, '../src'),
  threads
}),
```

## TreeShaking
Tree shaking 是一种用于移除 JavaScript 中未使用代码的优化技术，它可以显著减小打包后的文件体积。  
在 webpack 中，Tree shaking 通常与 ES2015 模块语法（即使用 import 和 export）以及静态解析工具（如 Babel、TypeScript）一起使用。它依赖于静态分析，通过识别代码中未被使用的部分，将其从最终的打包文件中移除。  
确保项目使用的是 ES2015 模块语法（即使用 import 和 export）。  
在 webpack 配置中设置 mode 为 "production"，以启用 webpack 的生产模式。这将自动开启一些优化功能，包括 Tree shaking。

## @babel-plugin-transform-runtime
@babel-plugin-transform-runtime 是 Babel 的一个插件，用于避免在每个使用了新的 ES6+ 特性的文件中重复引入 Babel 的辅助函数和 polyfill，从而减小生成文件的体积。

## core-js 
core-js 是一个 JavaScript 库，它提供了对 ECMAScript 标准功能的兼容性支持和填充 
Babel 是一个通用的 JavaScript 编译器，用于将新版本的 ECMAScript 代码转换为向后兼容的旧版本代码。它的重点是语法转换，将新的 ECMAScript 语法转换为等效的旧语法，以便在现有的 JavaScript 环境中运行。