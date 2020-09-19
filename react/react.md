# markdown使用说明

大纲显示隐藏 ctrl + shift + 1

## 标题

ctrl 加 1~6   #6最小

## 斜体 粗体 下划线

斜体：ctrl+i 

粗体:   ctrl + b 

下划线： ctrl + u 

## 列表

```
 无序列表: + 加空格
 有序列表: 1.加空格
```

## 注释

大于号 加空格

> 注释

## 代码

```
三个```回车生产
```

## 表格

表格：ctrl + t

## 水平线

水平分割线：三个*号

# React

## 故事背景：

由facebook发布的。于2013年开源

## 特点：

**1.声明式**：

​		以前需要操作dom，手动刷新dom。jquery也是在操作dom。有了声明式，就不需要操作dom了

**2.高效**：

​	虚拟dom，不总是直接操作dom。dom diff算法，最小化页面重绘

**3.灵活**

​	与其他库灵活使用

**4.JSX**

​	js里写html，JavaScript的扩展语法

​	优点:

1. JSX执行更快，编译为JavaScript代码时进行优化
2. 类型更安全，编译过程如果出错就不能编译，及时发现错误
3. JSX编写模板更加简单快速。

注意：

1. JSX必须要又根节点
2. 正常普通HTML元素要小写。如果是大写，默认认为是组件

5.**组件化**

​	代码复用，模块化

6.**单项数据流**

​	数据-视图-事件-数据

## 相关JS库

react.js 是React的核心库

react-dom.js 提供操作DOM的react扩展库

babel.min.js解析jsx语法代码转为纯js语法代码的库

## 安装

### CND

```
  <script src="https://unpkg.com/react@16/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
```

### npm安装

​	cnpm install -g create-react-app       	create-react-app  -v 测试

​	create-react-app 创建项目名

## HTML使用

```
 CDN引入
    const msg = "I LIKE YOU!";
        const myId = "Atguigu";
        // 创建虚拟dom
        const vDome = React.createElement("h2",{ id: "abc" },msg.toUpperCase()+123);
        // h2是标签，id是属性，msg是值
        // 将虚拟dom导入标签里
        ReactDOM.render(vDome, document.getElementById("test"));
```

## 元素渲染

```
let h1 = <h1>helloworld</h1>
使用JSX的写法，可以创建JS元素对象，
注意：JSX元素对象，或者组件对象，必须只有1个根元素根节点。最外层h1就是根元素，其他标签只要写到里面。
```

## 函数式组件

react 定义函数式组件的时候，**首字母大写**

```
//函数式组件
function Demo(data) {
    return (
        <div>
            <h1>现在的时间是{data.data.toLocaleTimeString()}</h1>
        </div>
    );
}
function run() {
    var root = document.getElementById("root");
    ReactDOM.render(<Demo data={new Date()} />, root);
}
setInterval(() => {
    run();
}, 1000);
```



# 补充

babel：一般babel.js是ES6转ES5的。



componentWillMount(){
    console.log("组件将要渲染")
  }
  componentDidMount(){

    console.log('组件渲染完毕')
  }
  componentWillReceiveProps(){
    console.log('组件将要接受props数据')
  }
  shouldComponentUpdate(){
    console.log('在组件接收到新的state或者pros，判断是否更新')
    return true
  }
  componentWillUpdate(){
    console.log("组件将要更新")
  }
  componentDidUpdate(){
    console.log("组件已经更新")
  }
  componentWillUnmount(){
    console.log("组件将要卸载")
  }