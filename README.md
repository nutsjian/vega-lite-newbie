# vega-lite-newbie
vega-lite

入门小白，有理解错误的地方请纠正，谢谢！

### view

### transform

### encoding
demo 在 `03encoding` 目录中，其中：

`demo_encoding_axis_01.html` 演示 `encoding` 下的 `axis` 配置效果，以及一些可配置的属性
#### encoding.axis 配置
```javascript
"encoding": {
    "x": {
        "field": ...,
        "type": ...,
        "axis": {   // Axis
        "orient": "...",  // 坐标轴的位置 top bottom left right，x 轴默认是 bottom ，下方
        "offset": ...,    // Number，坐标轴具体图表内容的留白空间（偏移大小）
        "position": ...,  // Number，当 x 轴是 top/bottom 时有用，是相对左边的偏移量
        "zindex": 0,      // Number，0 或者 1，若为 1 则在 marks 前面，若为 0 ，则在 marks 后面
        "labels": true,   // Boolean， true 或者 false，是否显示 x 轴的标签
        "format": "...",  // String，格式化，待补充
        "labelAngle": ...,// Number，标签的旋转角度
        "labelOverlap":..., // Boolean|String|String
        "labelPadding":..., // Number 标签文字和轴之间的距离
        "ticks": true,      // Boolean 是否显示刻度
        "ticksCount": ...,  // Number 刻度的数量
        "tickSize": ...,    // 刻度的大小，你所看到的是刻度的长度
        "values": ...,      // Number[] | DateTime[] 显示的设置刻度的值
        "title": ...,       // String | Null 轴的标题
        "titleMaxLength": ...,  // Number 轴的标题的最大长度，只有在自动生成，没有指定 title 时才有用
        "titlePadding": ...,    // Number 轴的标题和轴之间的间隔
        }
    },
    "y": ...,
    ...
}
```

`demo_encoding_axis_02.html` 演示在 `encoding` 下无法配置的一些属性，并且通过 `config` 下的全局配置，可以把通用的一些坐标轴的配置全局设定。
#### 全局 `config.axis` 配置
```javascript
bandPosition:
domain:
domainColor:
domainWidth:
maxExtent:
minExtent:

grid: Boolean，是否显示网格线
gridColor: String，网格线的颜色
gridDash: Number[]，
gridOpacity: Number，透明度，默认是 1
gridWidth: Number，网格线的宽度

labels: Boolean，是否显示坐标轴的刻度标签
labelAngle: Number，标签的角度
labelColor: String，颜色
labelFont: String，字体
labelFontSize: Number，字体大小
labelLimit: Number，标签的最大像素允许
labelOverlap: Boolean | String，encoding 中有说明
labelPadding: Number，encoding 中有说明

shortTimeLabels: Boolean，

ticks: Boolean
tickColor:
tickRound:
tickSize:
tickWidth:

titleAlign: String，
titleAngle: Number
titleBaseline: String
titleColor: String
titleFont: String
titleFontWeight: String
titleFontSize: Number
titleLimit: Number
titleMaxLength: Number
titlePadding: Number
titleX: Number
titleY: Number

// 这里 titleX titleY titleAlign 可以一起配合起来调整坐标轴标题的位置，比如 titleX: 0, titleAlign: "left" 此时 x 坐标轴的标题就在图表坐标系的左下角，并与 x 轴的 0 刻度对齐，自由发挥
```


#### encoding.type 配置
encoding 中的 type 可以选择如下几种类型：`quantitative`、`temporal`、`ordinal`、`nominal`、`genjson`。

quantitative：表示某种数量，通常是数字，比如：7.3 42.0 12.1
temporal：表示时间数据，支持日期时间和时间，比如：2015-03-07 12:32:17 17:01 2015-03-16 等
ordinal：