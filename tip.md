# 百度地图
vue-baidu-map

# geojson
获得geojson数据
> http://datav.aliyun.com/static/tools/atlas/#&lat=33.521903996156105&lng=104.29849999999999&zoom=4

绘制geojson
> http://geojson.io/#map=12/35.5724/110.6907

# vue-cli3.0 路由懒加载失效原因

## prefetch

```html
<link rel="prefetch" ></link>
```

这段代码告诉浏览器，这段资源将会在未来某个导航或者功能要用到，但是本资源的下载顺序权重比较低。也就是说prefetch通常用于加速下一次导航，而不是本次的。
被标记为prefetch的资源，将会被浏览器在空闲时间加载。

在vue-cli3.0 内默认使用了prefetch，当我们动态请求路由进行懒加载渲染的时候，浏览器会误以为这时候可以进行加载，把所有页面都加载了，导致首屏渲染慢。

我们在打包后的index.html可以找到每个chunk都加上了 rel="prefetch"

我们可以在vue.config.js内对prefetch进行删除处理

```Javascipt
chainWebpack: config => {
    // 移除 prefetch 插件
    config.plugins.delete('prefetch')
    config.plugins.delete('prefetch-index')
    config.plugins.delete('prefetch-admin')
}
```