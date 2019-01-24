### 为什么 vue-cli3 脚手架构建和打包速度比之前版本要快很多？
1. 所有的样式 loader 的 sourceMap 为 false
2. 所有的样式 解析匹配 使用了 oneOf
3. .vue, .js, .jsx, .ts, .tsx 文件都开启了缓存机制
4. 模块解析使用了 module.noParse 对 vue，vue-router，vuex，vuex-router-sync 不进行webpack解析，忽略大型的library可以提高构建性能。
5. resolve.modules: ['', ''] 里面指定了几个模块搜索目录， 告诉webpack解析模块时应该搜索的目录
6. 