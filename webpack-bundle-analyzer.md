# webpack-bundle-analyzer
为优化vue项目性能,需要使用webpack-bundle-analyzer分析报文件，找出最占用空间的插件有哪些，对应做出优化

由于vue-cli3.0没有自带webpack-bundle-analyzer插件，故需要安装

> npm install webpack-bundle-analyzer –save-dev

在vue.config.js进行配置

```js
module.exports = {
    chainWebpack: config => {
        config
            .plugin('webpack-bundle-analyzer')
            .use(require('webpack-bundle-analyzer').BundleAnalyzerPlugin)
    }
}
```

当我们运行项目的时候，页面就会自动打开

> npm run serve

地址为127.0.0.1:8888
