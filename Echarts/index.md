# 安装



本地下载:https://echarts.apache.org/zh/download.html

```
npm安装 npm install echarts --save
```

## 绘制简单的表

```
  <!-- 为 ECharts 准备一个具备大小（宽高）的 DOM -->
    <div id="main" style="width: 600px;height:400px;"></div>
```

## 在script中获取div

```
 // 基于准备好的dom，初始化echarts实例       
 var myChart = echarts.init(document.getElementById('main'));
 // 指定图表的配置项和数据
        var option = {
            title: {
                text: 'ECharts 入门示例'
            },
            tooltip: {},
            legend: {
                data:['销量']
            },
            xAxis: {
                data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
            },
            yAxis: {},
            series: [{
                name: '销量',
                type: 'bar',
                data: [5, 20, 36, 10, 10, 20]
            }]
        };

        // 使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
```

# 配置项

#### grid  数组

```
 // 位置
 grid: [
 {
                  left: "10%",
                  bottom: "25%",
                  top: "15%",
                  right: "15%"
                }
              ],
```

