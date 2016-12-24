# [ECharts](https://github.com/ecomfe/echarts) wordcloud extension based on [wordcloud2.js](https://github.com/timdream/wordcloud2.js)

<a href="http://echarts.baidu.com">
    <img style="vertical-align: top;" src="https://github.com/ecomfe/echarts/raw/master/asset/logo.png?raw=true" alt="logo" height="50px">
</a>

![](./example/word-cloud.png)


## Examples

[Google Trends](https://ecomfe.github.io/echarts-wordcloud/example/wordCloud.html)

[ECharts Option Keywords](https://ecomfe.github.io/echarts-wordcloud/example/optionKeywords.html)

## Install

```html
<script src="echarts.min.js"></script>
<script src="echarts-wordcloud.min.js"></script>
```

Or

```shell
npm install echarts-wordcloud
```

```js
var echarts = require('echarts');
require('echarts-wordcloud');
```

## Usage

```js
var chart = echarts.init(document.getElementById('main'));

chart.setOption({
    ...
    series: [{
        type: 'wordCloud',

        // The shape of the "cloud" to draw. Can be any polar equation represented as a
        // callback function, or a keyword present. Available presents are circle (default),
        // cardioid (apple or heart shape curve, the most known polar equation), diamond (
        // alias of square), triangle-forward, triangle, (alias of triangle-upright, pentagon, and star.
        // 字符云图形状的值，可以为任意极坐标方程表示的回调函数，或者是关键词，可选的关键词有圆形(默认情况)，心型曲线(
        //苹果或者心脏曲线),菱形，前向三角形，三角形(还可以用上三角形，五角形，星形作为代替)
        shape: 'circle',

        // A silhouette image which the white area will be excluded from drawing texts.
        // The shape option will continue to apply as the shape of the cloud to grow.
        //给空白的地方填上轮廓图
        maskImage: maskImage,

        // Folllowing left/top/width/height/right/bottom are used for positioning the word cloud
        // Default to be put in the center and has 75% x 80% size.
        // 词图的位置坐标以及大小，默认位置为center，大小为75% x 80%
        left: 'center',
        top: 'center',
        width: '70%',
        height: '80%',
        right: null,
        bottom: null,

        // Text size range which the value in data will be mapped to.
        // Default to have minimum 12px and maximum 60px size.
        // 映射在词图上的文本大小变化范围
        // 默认为[12px, 60px]
        sizeRange: [12, 60],

        // Text rotation range and step in degree. Text will be rotated randomly in range [-90, 90] by rotationStep 45
        // 文本旋转范围
        rotationRange: [-90, 90],
        rotationStep: 45,

        // size of the grid in pixels for marking the availability of the canvas
        // the larger the grid size, the bigger the gap between words.

        gridSize: 8,

        // Global text style
        // 全局文本风格
        textStyle: {
            normal: {
                fontFamily: 'sans-serif',
                fontWeight: 'bold',
                // Color can be a callback function or a color string
                color: function () {
                    // Random color
                    return 'rgb(' + [
                        Math.round(Math.random() * 160),
                        Math.round(Math.random() * 160),
                        Math.round(Math.random() * 160)
                    ].join(',') + ')';
                }
            },
            emphasis: {
                shadowBlur: 10,
                shadowColor: '#333'
            }
        },

        // Data is an array. Each array item must have name and value property.
        // Data 是一个数组，每个数组值中必须包括键值对属性
        data: [{
            name: 'Farrah Abraham',
            value: 366,
            // Style of single text
            textStyle: {
                normal: {},
                emphasis: {}
            }
        }]
    }]
});
```
