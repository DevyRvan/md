# element-ui
总结记录element-ui的bug及解决方案

## 按需引入


## 开发环境中覆盖了一些样式生产环境没有起效
由于css的就近原则，后写的样式会覆盖前面的样式

在main.js中element-ui的样式文件引入要提前于APP.vue

正确引入方式

```js
import 'element-ui/lib/theme-chalk/index.css'
import App from './App'
```

## 在.vue文件中对element样式的覆盖没有起效
在scoped属性下的样式只会对当前的组件起效，而element的组件是包含子组件的，需要写在全局下才能起效（这里不建议使用深度选择器/deep/）
``` js
<style lang="scss">
// 建议用一个唯一性的外层给这个组件命名，已避免渲染到其他组件
.xxx-container {
    .el-xxx {
        xxxx: xxxx;
    }
}
</style>
```

## table出现滚动条的时候表头错位修复
```css
.el-table th.gutter{
	display: table-cell!important;
	width: 17px!important;
    // width根据滚动条的样式修改
}
```

## element-ui
记录element-ui组件