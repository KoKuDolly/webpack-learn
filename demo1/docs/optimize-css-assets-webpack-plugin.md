optimize-css-assets-webpack-plugin
优化css资源webpack插件
虽然webpack5可能会将css优化嵌入，但是webpack4还是得需要自己手动添加插件。
在webpack的配置对象中，设置**optimization.minimizer**来覆盖webpack提供的默认值
```js
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const OptimizeCssAssetsPlugin = require('optimize-css-assets-webpack-plugin');
module.exports = {
  optimization: {
    minimizer: [
      new OptimizeCssAssetsPlugin({})
    ]
  },
  plugins: [
    new MiniCssExtractPlugin({
      filename: '[name].css',
      chunkFilename: '[id].css'
    })
  ],
  module: {
    rules: [
      {
        test: /\.css$/,
        use: [
          {
            loader: MiniCssExtractPlugin.loader
          }
          {
            loader: 'css-loader'
          }
        ]
      }
    ]
  }
}
```