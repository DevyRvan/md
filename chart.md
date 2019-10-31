
## 各类charts
- echart: 正常柱状图，正常平面饼图，水滴球图等等
- hightchart: 3d饼图，3d柱状图
- amchart: 3d柱状饼图(其余的没有必要不用amchart，这个插件还未完善完毕，而且全英文档)

## echarts水滴球图 demo
> 先引入 echarts-liquidfill

```
npm install 'echarts-liquidfill' --save
```

```
import 'echarts-liquidfill'
```

```JavaScript
waterDrop() {
  let value = 0.48
  let data = [value] // 水滴高度
  let option = {
    backgroundColor: 'rgba(0,0,0,0)',
    graphic: [{
      type: 'group',
      left: 'center',
      bottom: 10,
      children: [{
        type: 'text',
        z: 100,
        left: '10',
        top: 'middle',
        style: {
          fill: '#fff',
          text: '磁盘剩余空间：',
          font: '16px Microsoft YaHei'
        }
      }, {
        type: 'text',
        z: 100,
        left: '120',
        top: 'middle',
        style: {
          fill: '#fff',
          text: '128G',
          font: '24px Microsoft YaHei'
        }
      }]
    }],
    series: [{
      type: 'liquidFill',
      radius: '70%',
      center: ['50%', '40%'],
      itemStyle: {
        opacity: 0.1, // 波浪的透明度
        shadowBlur: 2, // 波浪的阴影范围
        shadowColor: '#5cd9ff' // 阴影颜色
      },
      emphasis: {
        itemStyle: {
          opacity: 0.1 // 鼠标经过波浪颜色的透明度
        }
      },
      data: data,
      outline: {
        show: false,
        borderDistance: 22, // 外部轮廓与图表的距离 数字
        itemStyle: {
          borderColor: 'rgba(255,255,255,0.1)', // 边框的颜色
          borderWidth: 1, // 边框的宽度
          // shadowBlur: 5 , // 外部轮廓的阴影范围 一旦设置了内外都有阴影
          shadowColor: '#000' // 外部轮廓的阴影颜色
        }
      },
      backgroundStyle: {
        borderWidth: 5,
        borderColor: 'rgba(128, 225, 255, 0.7)',
        color: 'rgba(0,0,0,0)',
        shadowBlur: 30, // 外部轮廓的阴影范围 一旦设置了内外都有阴影
        shadowColor: 'rgba(128, 225, 255)'
      },
      label: {
        normal: {
          formatter: (value * 100).toFixed(2) + '%',
          textStyle: {
            fontSize: 24,
            color: '#5cd9ff', // 背景前的文字颜色
          },
          insideColor: 'rgba(112, 237, 255)' // 波浪前的文字颜色
        },
      }
    }]
  }
  this.myChart.setOption(option)
}
```

## 有关自适应时echart的resize
```JavaScript
export default {
  data() {
    return {
      myChart: ''
    }
  },
  methods: {
    resize() {
      this.myChart.resize()
    }
  },
  mounted() {
    this.myChart = this.$echarts.init(document.getElementById('echart'))
    window.addEventListener('resize', this.resize)
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.resize)
    this.myChart.dispose()
  }
}

```