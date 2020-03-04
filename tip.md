# tip

## 百度地图
vue-baidu-map

## 快速删除node_modules
> npm i rimraf -g
> rimraf node_modules

## geojson
获得geojson数据
> http://datav.aliyun.com/static/tools/atlas/#&lat=33.521903996156105&lng=104.29849999999999&zoom=4

绘制geojson
> http://geojson.io/#map=12/35.5724/110.6907

## vue-cli3.0 路由懒加载失效原因
在vue-cli3.0 内默认使用了prefetch
### prefetch

```html
<link rel="prefetch" ></link>
```

这段代码告诉浏览器，这段资源将会在未来某个导航或者功能要用到，但是本资源的下载顺序权重比较低。也就是说prefetch通常用于加速下一次导航，而不是本次的。
被标记为prefetch的资源，将会被浏览器在空闲时间加载。

在vue-cli3.0 内默认使用了prefetch，当我们动态请求路由进行懒加载渲染的时候，浏览器会误以为这时候可以进行加载，把所有页面都加载了，导致首屏渲染慢。

我们在打包后的index.html可以找到每个chunk都加上了 rel="prefetch"

我们可以在vue.config.js内对prefetch进行删除处理

vue-cli3.0还有一个bug

移除 prefetch 插件不能写成以下代码
```js
chainWebpack: config => {
  // 移除 prefetch 插件
  config.plugins.delete('prefetch')
}
```

而要根据xxx.html的名称去删除

```js
chainWebpack: config => {
  // 移除 prefetch 插件
  config.plugins.delete('prefetch-xxx')
  config.plugins.delete('prefetch-index')
  config.plugins.delete('prefetch-admin')
}
```

## vue.js 进行初始化遇到的关于core-js的错误@core-js/modules/es6.array.find-index]

core-js版本太高 

发生原因：cnpm不会根据package-lock.json安装依赖，故会导致直接根据package.json中的core-js: ^2.x.x安装了更高版本

> npm install core-js@2 / cnpm install core-js@2

## 移动端UI组件
Mint UI  饿了么组件
Nut UI 京东组件
vant-ui https://youzan.github.io/vant/#/zh-CN/intro
weex UI 阿里组件
weui 微信小程序组件

## 算法小技巧
### 如何将浮点数点左边的数每三位添加一个逗号，如12000000.11转化为『12,000,000.11』?
```js
function commafy(num){
  return num && num
    .toString()
    .replace(/(\d)(?=(\d{3})+\.)/g, function($1, $2){
      return $2 + ',';
    });
}
```

## 前端学习网站推荐
1. 极客标签：     http://www.gbtags.com/

2. 码农周刊：     http://weekly.manong.io/issues/

3. 前端周刊：     http://www.feweekly.com/issues

4. 慕课网：       http://www.imooc.com/

5. div.io：       http://div.io

6. Hacker News： https://news.ycombinator.com/news

7. InfoQ：       http://www.infoq.com/

8. w3cplus：     http://www.w3cplus.com/

9. Stack Overflow： http://stackoverflow.com/

10. w3school：    http://www.w3school.com.cn/

11. mozilla：     https://developer.mozilla.org/zh-CN/docs/Web/JavaScript

## 打包成桌面软件
nwjs

## v-waves
element 指令waves 水波纹效果

## 拒绝别人用F12看你代码
```js
(function noDebuger() {
    function testDebuger() {
        var d = new Date();
        // test();
        debugger;
        if (new Date() - d > 10) {
            document.body.innerHTML = "<h1>年轻人，不要太好奇</h1>";
            return true;
        }
        return false;
    }

    function start() {
        while (testDebuger()) {
            testDebuger();
        }
    }
    if (!testDebuger()) {
        window.onblur = function () {
            setTimeout(function () {
                start();
            }, 500);
        };
    } else {
        start();
    }
})();
```

## vue-grid-layout
vue-grid-layout是一个类似于Gridster的栅格布局系统, 适用于Vue.js。

https://github.com/jbaysolutions/vue-grid-layout/blob/master/README-zh_CN.md

### 特性
- 可拖拽
- 可调整大小
- 静态部件（不可拖拽、调整大小）
- 拖拽和调整大小时进行边界检查
- 增减部件时避免重建栅格
- 可序列化和还原的布局
- 自动化 RTL 支持
- 响应式


## 流程图工具
https://github.com/bpmn-io/bpmn-js

https://github.com/bpmn-io/vue-bpmn

vue-flowchart

## canvas
https://codepen.io/ 

## terser-webpack-plugin
清除console

## el-input 限制只能输入数字
```html
<el-input v-model.number="num" oninput="value=value.replace(/[^\d.]/g,'');"></el-input>
```

## vue 监控 element元素大小
element-resize-detector

## 预览excel跟word文档
Excel: SheetJS
Word: mammoth.js

当然，如果你的文档都是公网可以访问的，可以用微软提供的在线预览
```html
<iframe src='https://view.officeapps.live.com/op/embed.aspx?src=http://remote.url.tld/path/to/document.doc' width='1366px' height='623px' frameborder='0'>This is an embedded <a target='_blank' href='http://office.com'>Microsoft Office</a> document, powered by <a target='_blank' href='http://office.com/webapps'>Office Online</a>.</iframe>
```
