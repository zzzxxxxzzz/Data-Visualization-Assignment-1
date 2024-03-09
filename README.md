#  数据可视化作业1 - Anscombe's quartet 数据集可视化

## 一 、 任务内容

1、用可视化软件或工具，对课程第1讲教学内容中所涉及的Anscombe's quartet数据集进行分析，将四组数据进行可视化，并说明这四组数据的分布特征。


Anscombe's quartet 数据集：是一个经典的统计学示例，由英国统计学家弗朗西斯·安斯库姆（Francis Anscombe）于1973年构造。这个数据集包括四组数据，每组数据包含11个点（x,y）。

![Anscombe’s quartet 数据集](https://github.com/zzzxxxxzzz/Data-Visualization-Assignment-1/blob/main/imgae/1.png)


2、用脚本语言或编程语言，计算四组数据的最小二乘法回归线方程。


## 二、任务一

1、每组数据单独用1个散点图，最后生成4个散点图。

![ ](https://github.com/zzzxxxxzzz/Data-Visualization-Assignment-1/blob/main/imgae/2.png)

2、使用1个散点图，对每组数据使用不同的颜色进行编码。

![ ](https://github.com/zzzxxxxzzz/Data-Visualization-Assignment-1/blob/main/imgae/3.png)

3、从均值、方差、相关系数的角度说明这四组数据的分布特征，并适当阐述数据可视化的意义和价值。

均值公式：

$$\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_i$$

方差公式：

$$s^2 = \frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2$$

相关系数公式：

$$r = \frac{\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^{n} (x_i - \bar{x})^2 \sum_{i=1}^{n} (y_i - \bar{y})^2}}$$

计算结果如下表：

|  | X均值 | Y均值 | X方差 | Y方差| 相关系数 |
|--|--|--|--|--|--|
| 1 | 9 | 7.5 | 11  | 4.127 | 0.816 |
| 2 | 9 | 7.5 | 11  | 4.127 | 0.816 |
| 3 | 9 | 7.5 | 11  | 4.127 | 0.816 |
| 4 | 9 | 7.5 | 11  | 4.127 | 0.816 |


尽管四组数据在许多统计度量上如均值、方差和相关系数等呈现出几乎相同的值，但这并**不足以揭示出数据集的真实结构**。只有通过**图形化展示**，我们才能清楚地看到每组数据的**独特分布和趋势**。

## 三、任务二

1、计算四组数据的最小二乘法回归线方程。


最小二乘法回归方程：它通过最小化误差的平方和来确定直线的参数，从而使得这条直线尽可能地接近数据点。最小二乘法回归线方程通常表示为 y=mx+b，其中：m为斜率，b为截距。

斜率 m 和截距 b 的计算公式如下：

$$ m = \frac{\sum xy - n\bar{x}\bar{y}}{\sum x^2 - n\bar{x}^2} $$

$$ b = \bar{y} - k\bar{x} $$

最后计算出四组数据的最小二乘法回归线方程均为：y=0.5*x+3

![ ](https://github.com/zzzxxxxzzz/Data-Visualization-Assignment-1/blob/main/imgae/4.png)

## 代码附录

散点图绘制：
``` javascript
<!DOCTYPE  html>
<html  lang="en">
<head>
<meta  charset="UTF-8">
<meta  name="viewport"  content="width=device-width, initial-scale=1.0">
<meta  http-equiv="X-UA-Compatible"  content="ie=edge">
<title>ECharts</title>
<script  src="js/echarts.min.js"></script>  <!-- 引入echarts.js -->
</head>
<body>
<div  id='div1'  style='width: 800px; height: 600px'></div>
<script>
var  chartDom = document.getElementById('div1');
var  myChart = echarts.init(chartDom);
const  dataAll = [
[

[10.0, 8.04],
[8.0, 6.95],
[13.0, 7.58],
[9.0, 8.81],
[11.0, 8.33],
[14.0, 9.96],
[6.0, 7.24],
[4.0, 4.26],
[12.0, 10.84],
[7.0, 4.82],
[5.0, 5.68]
],

[

[10.0, 9.14],
[8.0, 8.14],
[13.0, 8.74],
[9.0, 8.77],
[11.0, 9.26],
[14.0, 8.1],
[6.0, 6.13],
[4.0, 3.1],
[12.0, 9.13],
[7.0, 7.26],
[5.0, 4.74]

],

[

[10.0, 7.46],
[8.0, 6.77],
[13.0, 12.74],
[9.0, 7.11],
[11.0, 7.81],
[14.0, 8.84],
[6.0, 6.08],
[4.0, 5.39],
[12.0, 8.15],
[7.0, 6.42],
[5.0, 5.73]

],

[

[8.0, 6.58],
[8.0, 5.76],
[8.0, 7.71],
[8.0, 8.84],
[8.0, 8.47],
[8.0, 7.04],
[8.0, 5.25],
[19.0, 12.5],
[8.0, 5.56],
[8.0, 7.91],
[8.0, 6.89]

]

];

const  markLineOpt = {
animation:  false,
label: {
formatter:  'y = 0.5 * x + 3',
align:  'right'
},
lineStyle: {
type:  'solid'
},
tooltip: {
formatter:  'y = 0.5 * x + 3'
},

data: [
[
{

coord: [0, 3],
symbol:  'none'

},

{
coord: [20, 13],
symbol:  'none'

}
]

]

};

var  option = {
title: {
text:  "Anscombe's quartet 数据集可视化",
left:  'center',
top:  0

},

legend: {
data: ['I', 'II', 'III', 'IV'],
orient:  'vertical',
right:  '1%',
top:  '6%'

},

grid: [

{ left:  '7%', top:  '7%', width:  '38%', height:  '38%' },
{ right:  '7%', top:  '7%', width:  '38%', height:  '38%' },
{ left:  '7%', bottom:  '7%', width:  '38%', height:  '38%' },
{ right:  '7%', bottom:  '7%', width:  '38%', height:  '38%' }

],

tooltip: {

formatter:  'Group {a}: ({c})'

},

xAxis: [

{ gridIndex:  0, min:  0, max:  20 },
{ gridIndex:  1, min:  0, max:  20 },
{ gridIndex:  2, min:  0, max:  20 },
{ gridIndex:  3, min:  0, max:  20 },

],

yAxis: [

{ gridIndex:  0, min:  0, max:  15 },
{ gridIndex:  1, min:  0, max:  15 },
{ gridIndex:  2, min:  0, max:  15 },
{ gridIndex:  3, min:  0, max:  15 },

],

series: [

{

name:  'I',

type:  'scatter',
xAxisIndex:  0,
yAxisIndex:  0,
data:  dataAll[0],
markLine:  markLineOpt,

},

{

name:  'II',
type:  'scatter',
xAxisIndex:  1,
yAxisIndex:  1,
data:  dataAll[1],
markLine:  markLineOpt,

},

{

name:  'III',
type:  'scatter',
xAxisIndex:  2,
yAxisIndex:  2,
data:  dataAll[2],
markLine:  markLineOpt,

},

{

name:  'IV',
type:  'scatter',
xAxisIndex:  3,
yAxisIndex:  3,
data:  dataAll[3],
markLine:  markLineOpt,

},

]

};

option && myChart.setOption(option);

</script>
</body>
</html>
 ```


最小二乘法回归：
```python
<![endif]-->

import numpy as np  
import scipy.stats  
  
  
data = {  
'I': {  
'x': np.array([10, 8, 13, 9, 11, 14, 6, 4, 12, 7, 5]),  
'y': np.array([8.04, 6.95, 7.58, 8.81, 8.33, 9.96, 7.24, 4.26, 10.84, 4.82, 5.68])  
},  
'II': {  
'x': np.array([10, 8, 13, 9, 11, 14, 6, 4, 12, 7, 5]),  
'y': np.array([9.14, 8.14, 8.74, 8.77, 9.26, 8.10, 6.13, 3.10, 9.13, 7.26, 4.74])  
},  
'III': {  
'x': np.array([10, 8, 13, 9, 11, 14, 6, 4, 12, 7, 5]),  
'y': np.array([7.46, 6.77, 12.74, 7.11, 7.81, 8.84, 6.08, 5.39, 8.15, 6.42, 5.73])  
},  
'IV': {  
'x': np.array([8, 8, 8, 8, 8, 8, 8, 19, 8, 8, 8]),  
'y': np.array([6.58, 5.76, 7.71, 8.84, 8.47, 7.04, 5.25, 12.50, 5.56, 7.91, 6.89])  
}  
}  
  
  
results = {}  
  
for key, d in data.items():  
x_mean = np.mean(d['x'])  
y_mean = np.mean(d['y'])  
x_variance = np.var(d['x'], ddof=1) # Sample variance  
y_variance = np.var(d['y'], ddof=1) # Sample variance  
correlation = scipy.stats.pearsonr(d['x'], d['y'])[0]  
  
results[key] = {  
'x_mean': x_mean,  
'y_mean': y_mean,  
'x_variance': x_variance,  
'y_variance': y_variance,  
'correlation': correlation  
}  
  
print(results)  
  
  
# Calculate linear regression (least squares fit) for each dataset  
regression_results = {}  
  
for key, d in data.items():  
slope, intercept, r_value, p_value, std_err = scipy.stats.linregress(d['x'], d['y'])  
regression_results[key] = {  
'slope': slope,  
'intercept': intercept  
}  
  
print(regression_results)

```



