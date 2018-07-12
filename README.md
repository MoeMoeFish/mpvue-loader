# mpvue-loade

>Webpack loader for mpvue components

本仓库是 fork 自 [mpvue-loader](https://github.com/mpvue/mpvue-loader) 修改而来，主要支持小程序分包功能。

实现原理请参考 [mpvue 如何对小程序进行分包？](https://github.com/Meituan-Dianping/mpvue/issues/590)

更多详细文档请查阅 [mpvue-loader](http://mpvue.com/build/mpvue-loader)。

本仓库是内部使用的，以后升级不会保证兼容

请修改以下文件：build/webpack.base.conf.js 中添加 webpack 配置
```javascript
resolveLoader: {
  alias: {
      'mpvue-loader': '@moemoefish/mpvue-loader'
  }
},
```

在文件 build/webpack.dev.conf.js 中修改
```javascript
output: {
  path: config.build.assetsRoot,
  filename: path.posix.join('[name]/js/main.js'),
  chunkFilename: path.posix.join('[id]/js/main.js')
},
```
```javascript
new ExtractTextPlugin({
  filename: path.posix.join('[name]/css/main.wxss')
}),
```

在文件 build/webpack.prod.conf.js 中修改
```javascript
output: {
  path: config.build.assetsRoot,
  filename: path.posix.join('[name]/js/main.js'),
  chunkFilename: path.posix.join('[id]/js/main.js')
},
```
```javascript
new ExtractTextPlugin({
  filename: path.posix.join('[name]/css/main.wxss')
}),
```
