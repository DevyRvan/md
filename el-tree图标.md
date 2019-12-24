## element-ui tree 自定义图标

> 可以根据数据的不同去用不同的icon/svg，有需求的自行修改

```html
<template>
  <el-tree
    :data="treeData"
    :render-content="renderContent"
  >
</template>
```

```js
<script>
export default{
  methods: {
    renderContent(h, { node, data, store }) {
      if (data.children && data.children.length > 0) {
        return (
          <span class="custom-tree-node">
            <svg-icon icon-class="folder2"></svg-icon>
            <span style="margin-left:5px;">{ node.label }</span>
          </span>
          )
      }
      return (
          <span class="custom-tree-node">
            <svg-icon icon-class="file"></svg-icon>
            <span style="margin-left:5px;">{ node.label }</span>
          </span>
          )
    },
  }
}
<script>
```