## 介绍

canvas的三要素
	id作为唯一标识    
	width画布内容宽度的像素大小（与style的宽度和高度是有区别的）   
	height 画布内容高度的像素大小

```js
    <canvas id="canvas1" width="500" height="600"></canvas>

 	 <script>
        // 1.找到画布
        let canvas1 = document.getElementById("canvas1");
        // 2.画笔
        let ctx = canvas1.getContext("2d");
        console.log(ctx);
        // 3.绘制路径
        ctx.rect(50, 50, 300, 300);
        // 4.填充
        ctx.fillStyle = "#fff"; // 填充颜色
        ctx.fill(); // 执行填充
        // 5.描边和路径
        ctx.lineWidth = 20; // 描边值
        ctx.strokeStyle = "blue"; // 描边颜色
        ctx.stroke(); // 执行描边
    </script>

 	<script>
        let canvas1 = document.getElementById("canvas1");
        let ctx = canvas1.getContext("2d");
        // 设置绘制的起点
        ctx.moveTo(50, 50);
        // 设置经过的某个位置
        ctx.lineTo(50,300)
        // 设置经过的某个位置
        ctx.lineTo(350,300)
        ctx.lineWidth = 20
        ctx.stroke()
    </script>               
```

##  常用的样式

https://www.w3school.com.cn/tags/html_ref_canvas.asp W3C 参考手册

### 线条样式

lineCap 起始路径的线段边缘设置为圆角

lineJoin 线条拐角
	bevel 斜角
	round 圆角
	miter 尖角

## 绘制圆形

```
ctx.arc(x,y,r,起始角度,结束角度,顺时针或逆时针)
ctx.arc(200,200,100,0,2*Math.PI) // math.pi  是180°，2就是360°
默认为false 顺时针，true为逆时针
```

## 绘制文字

```
ctx.font="50px 微软雅黑"
ctx.fillText("helloworld",x,y) // 在画布上绘制“被填充的”文本   x是横轴  y是竖轴
ctx.strokeText()// 镂空文字

ctx.shadowBlur = 20; // 设置或返回用于阴影的模糊级别
ctx.shadowColor = "rgba(0,0,0,1)" // 颜色
ctx.shadowOffsetX=10 // X轴的位置
ctx.shadowOffsetY=10 // y轴的位置

ctx.clearRect(0,0,500,200) // 清除指定矩形内的像素

弹幕效果
	let x=600
   setInterval(() => {
   if(x <= -100){x = 600}
            ctx.clearRect(0,0,500,200)
            x -= 10;
            ctx.strokeText("你是猪", 100, 100);
        }, 100);
```

## 绘制图像

```
ctx.drawImage(图片对象，x位置，y位置)
ctx.drawImage(图片对象，x位置，y位置，宽度，高度)
ctx.drawImage(图片对象，图像裁剪的位置X，图像裁剪的位置y，裁剪的宽度，裁剪的高度，x位置，y位置，宽度，高度)
  var img = new Image
        img.src ="./1.png"
        img.onload = function(){
            ctx.drawImage(img,100,100,600,600)
        }
 PS：img.onload 是图片加载后，执行的方法。
```

## 转换

| 方法                                                         | 描述                                           |
| :----------------------------------------------------------- | :--------------------------------------------- |
| [scale()](https://www.w3school.com.cn/tags/canvas_scale.asp) | 缩放当前绘图至更大或更小                       |
| [rotate()](https://www.w3school.com.cn/tags/canvas_rotate.asp) | 旋转当前绘图                                   |
| [translate()](https://www.w3school.com.cn/tags/canvas_translate.asp) | 重新映射画布上的 (0,0) 位置                    |
| [transform()](https://www.w3school.com.cn/tags/canvas_transform.asp) | 替换绘图的当前转换矩阵                         |
| [setTransform()](https://www.w3school.com.cn/tags/canvas_settransform.asp) | 将当前转换重置为单位矩阵。然后运行 transform() |

```
rotate(Math.PI/4)// 旋转的时候，是根据坐标轴旋转的。
scale(宽,高)
```

## 其他

| 方法      | 描述                           |
| :-------- | :----------------------------- |
| save()    | 保存当前环境的状态             |
| restore() | 返回之前保存过的路径状态和属性 |

```js
save()// 没有参数，保留环境的状态。在中间做缩放和旋转。不管做什么操作都可以用restore()还原
restore() // 恢复，可以定义多个save()来保存状态，用restore()多个回复。

列:
ctx.fillStyle="blue"
ctx.save()
ctx.fillStyle="blue"
ctx.save()

ctx.restore() // 恢复上一个
ctx.restore() // 在恢复上一个的上一个
```



## 注意

+  在canvas中写入内容，正常画布是不显示的。你的浏览器不知道canvas

  

