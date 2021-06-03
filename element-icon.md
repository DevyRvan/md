## 有关于element-icon的知识

> 由于vue-cli3.0自带对字体文件的处理，有关文件会被打包到public下，如果有其他需要的话要加以下代码

```js
// 字体处理
const fontsRule = config.module.rule('fonts')
fontsRule.uses.clear()
fontsRule
    .test(/\.(woff2?|eot|ttf|otf)(\?.*)?$/i)
    .use('file-loader')
    .loader('url-loader')
    .options({
      fallback: {
        loader: 'file-loader',
        options: {
          name: `/fonts/[name].[hash:8].[ext]`
        }
      }
    })
```
