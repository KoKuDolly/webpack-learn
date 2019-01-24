--config 指定特定文件

Windows vs. POSIX
windows文件路径格式
```js
const pathStr = 'C:\\temp\\myfile.html'
path.win32.join(pathStr);
```
POSIX文件路径格式
```js
const pathStr = '/temp/myfile.html'
path.posix.join(pathStr);
```

```js
const path = require('path');
module.exports = {
  mode: 'production', // "production"|"development"|"none", production 开启优化功能；development 开启开发的有用工具；
  entry: {
    a: "",
    f: ["", ""],
    b: {
      c: "",
      d: ["", ""],
      e: {}
    }
  }, // string | object | array
  output: {
    path: path.resolve(__dirname, "dist"), // string, 必须是绝对路径，所有输出文件的目标路径，
    filename: "bundle.js", // string  "[name].js" -- 用于多个入口点（出口点）  "[chunkhash].js" -- 长效缓存
    // 入口分块的文件名模板
    publicPath: "/assets/", // string "" "/assets/" "https://cdn.example.com/"
    // 输出解析文件的目录，url 相对于 HTML 页面
    library: "", // string 导出库的名称
    libraryTarget: "umd", // 通用模块定义
    // 导出库的类型    umd2 -- 通用模块定义; commonjs2 -- exported with module.exports; commonjs -- 作为exports的属性导出; amd -- 使用AMD定义方法来定义; this -- 在this上设置属性; var -- 变量定义于根作用域下; assign -- 盲分配(blind assignment); window -- 在window对象上设置属性; global -- property set to global object; jsonp-- jsonp wrapper;
    /* 高级输出配置 */
    pathinfo: true, // 在生成代码时，引入相关的模块、导出、请求等有帮助的路径信息
    chunkFilename: "[id].js", // 附加分块（additional chunk）的文件名模板
    jsonpFunction: "", // 用于加载分块的 JSONP 函数名
    sourceMapFilename: "", // source map 位置 的文件名模板
    devtoolModuleFilenameTemplate: "", // devtool 中模块 的文件名模板
    devtoolFallbackModuleFilenameTemplate: "", // devtool 中模块 的文件名模板（用于冲突）
    umdNamedDefine: true, // 在 UMD 库中使用命名的 AMD 模块
    crossOriginLoading: "", // 指定运行时如何发出跨域请求问题 "use-credentials"(枚举)/"anonymous"/false
  },
  module: {
    rules: [
      {
        test: /\.jsx?$/,
        include: [path.resolve(__dirname, 'app')],
        exclude: [path.resolve(__dirname, "app/demo-files")],
        // 这里是匹配条件，每个选项都接收一个正则表达式或字符串
        // test 和 include 具有相同作用，都是必须匹配选项
        // exclude 是必不匹配选项（优先于 test 和 include ）
        // 最佳实践：
        // - 只在 test 和 文件名匹配 中使用正则表达式
        // - 在 include 和 exclude 中使用绝对路径数组
        // - 尽量避免 exclude，更倾向于使用 include
        issuer: { // issuer 条件（导入源）
          test, include, exclude
        },
        enforce: 'pre', // pre, post, 标识应用这些规则，即使规则覆盖
        loader: 'babel-loader',
        options: { // loader 的可选项
          presets: ['env']
        }
      },
      {
        test: /\.html$/,
        use: [ // 应用多个loader
          'xxx-loader',
          {
            loader: 'xxx-loader',
            options: {}
          }
        ]
      },
      {
        oneOf: []
      },
      // 只能使用这些嵌套规则之一
      {
        rules: []
      },
      // 使用所有这些嵌套规则（合并可用条件）
      {
        resource: []
      },
      {
        resource: {
          and: []
        }
      },
      {
        resource: {
          or: []
        }
      },
      {
        resource: {
          not: []
        }
      }
      /* 高级模块配置 */
    ]
  },
  resolve: {
    // 解析模块请求的选项
    // 不适用于对 loader 解析
    modules: [
      "node_modules",
      path.resolve(__dirname, "app")
    ],
    // 用于查找模块的目录
    extensions: [".js", ".json", ".jsx", ".css"],
    alias: {
      // 模块别名列表
      "module": "new-module",
      // 起别名： 
    }

  },
  performance: {

  },
  devtool: "",
  context: "",
  target: "",
  externals: [],
  serve: {
    port: 1223,
    content: './dist'
  },
  stats: "",
  devServer: {
    proxy: {
      '/api': 'http://localhost:3000'
    },
    contentBase: "",
    compress: true,
    historyApiFallback: true,
    hot: true,
    https: false,
    noInfo: true,
  },
  plugins: [

  ],
  /* 高级配置 */
  resolveLoader: {/* 等同于 resolve */}, // 独立解析选项的loader
}
```