# webpack 环境变量的设置方式

```sh
"alpha": "npm config set products:env alphaBeta && npm run build"
```

```sh
--define process.env.NODE_ENV="'production'"
```

在配置文件中设置 mode

```js
plugins: [
  new webpack.DefinePlugin({
    'process.env': env
  })
]

```