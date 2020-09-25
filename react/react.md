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

JSX表达式：

1. 由HTML元素构成
2. 中间如果需要插入变量用{}
3. {}中介可以使用表达式
4. {}中间表达式中可以使用jsx对象
5. 树形和html内容都是一样都是用{}来插入内容

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

## 组件

函数时和类组件的区别，**定义组件首字母大写**

函数式比较简单，一般用于静态没有交互事件的内容的组件页面。

类组件，一般称为动态组件，动态修改事件的或者交互。

**函数式组件：**

react 定义函数式组件的时候

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

**类组件：**

```
// 在render中，只能定义一个组件。在组件中可以定义很多组件，称为符合组件
// 类组件传值，输出this，在this中可以看到prors，里面有传的值
class 组件名 extends React.Component {
    render() {
        return (
            <div>
                <h1>类组件</h1>
            </div>
        );
    }
}
 ReactDOM.render(<组件名 data={'123'} />, root);
```

## 储存数据(vue的data)

定义在类组件中。<u>每次reactDOM.render的时候，constructor只执行一次，render渲染每次都执行。</u>

```
class 组件名 extends React.Component {
	constructor(props){
	super(props)
	// 状态（数据）
	this.state = {
		time:123
	}
	}
	
	render(){
	return(
		<div>
		<h1>当前时间{this.state.time}</h1>
		</div>
	)
	}
}
```

## 改变储存的值

因为数据constructor只渲染一次，所以要让他改变后渲染，就要使用this.setState.   切勿直接修改state数据	通过this.setState修改完数据后，并不会立即修改dom里面的内容。react这个函数内容所有设置状态变化后，统一对比虚拟dom对象，然后在统一修改，提升性能	

```
定义生命周期组件加载完，在类组件里使用。	
class 组件名 extends React.Component {
	constructor(props){
	super(props)
	// 状态（数据）
	this.state = {
		time:123
	}
	}
	render(){
	return(
		<div>
		<h1>当前时间{this.state.time}</h1>
		</div>
	)
	}
	
	componentDidMount(){
	this.setState({
	time:123
	})
	}
}

```



## 生命周期

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



## 样式

外联式使用样式className ={'定义的class名'} // 加引号定义的class名

```
// demo定义，下面使用。属性第二个首字母大写，也可以用引号括起来
consot demo = {borderBottom;'4PX SOLID #000'}
<div style={demo}>123</div>
```

### 条件渲染

直接通过条件运算返回要渲染的JSX对象。通过条件运算得出jsx对象，再将jsx对象渲染到模板中

```
在类组件中，render()中做判断。因为都是return所以可以直接做一下判断
 render() {
        if (this.state.isAnst) {
            return <Test />;
        } else {
            return <Test2 />;
        }
    }

拓展上面.这样可以更加灵活 推荐使用
   render() {
        var ele = null;
        if (this.state.isAnst) {
            ele= <Test />;
        } else {
            ele= <Test2 />;
        }
        return (
            <div>
                <span>123321</span>
                {ele}
            </div>
        )
    }
    
 也可以使用三元运算符 {this.state.isAnst? <Test />:<Test2 />}
```

### 列表渲染

从后端拿到数据后渲染

```
render() {
        var arrHtml = [];
        for (var i = 0; i < this.state.list.length; i++) {
            let demo = (
                <li>
                    id是：{this.state.list[i].id}
                    姓名是：{this.state.list[i].name}
                </li>
            );
            arrHtml.push(demo);
        }

        return (
            <div>
                <h1>列表渲染</h1>
                <ul>{arrHtml}</ul>
            </div>
        );
    }
    
拓展。可以用map代替for循环
```



## 事件

驼峰命名



原生：阻止跳转return false

点击事件onClick={this.clickevent}



## 组件传值

props

​	父传递给子组件数据，单项流动，不能子传给父，可以是任意类型。

Props可以设置默认值

helloMessage.defaultProps = {name:"张三",msg:"123"}

注意props可以专递函数，props可以传递父元素的函数，就可以去修改父元素的 state，从而达到传递数据给父元素

### 父传子

```
// 父组件,按钮绑定一个事件btnebent，setState修改数据里的值，bind修改事件的指向。chin定义的子组件，isanst传值给子组件。

class Demo1 extends React.Component {
    constructor(porst) {
        super(porst);
        this.state = {
            isAnst: true,
        };
        this.btnevent = this.btnevent.bind(this);
    }

    render() {
        return (
            <div>
                <button onClick={this.btnevent}>显示隐藏</button>
                <Chin isAnst={this.state.isAnst} />
            </div>
        );
    }
    btnevent() {
        this.setState({
            isAnst: !this.state.isAnst,
        });
    }
}

//子组件,接收值是用props来接受的。打印this.props就是接收值

class Chin extends React.Component {
    constructor(porst) {
        super(porst);
    }
    render() {
        let classTest = "";
        classTest = this.props.isAnst ? " block" : "";
        return (
            <div>
                <span className={"bgred" + classTest}>显示</span>
            </div>
        );
    }
}

ReactDOM.render(<Demo1 />, document.getElementById("root"));

```

### 子传父

调用父元素的函数从而操作父元素的数据 ，从而实现数据从子元素传递至父元素 

```
// 父组件。定义好isAnst值。定义好btnevent的方法，data形参是子组件传递过来的值，此方法是修改isAnst的值。在调用子组件传递btnevent方法
class Demo1 extends React.Component {
    constructor(porst) {
        super(porst);
        this.state = {
            isAnst: "1",
        };
    }

    render() {
        return (
            <div>
                <span>{this.state.isAnst}</span>
                <Chin btnevent={this.btnevent} />
            </div>
        );
    }
    btnevent = (data) => {
        this.setState({
            isAnst: data,
        });
    };
}

// 子组件。定义msg要传递的数据。在子组件按钮中创建事件。在事件中使用父组件传递过来的方法，this.props.定义的方法，在传递参数
class Chin extends React.Component {
    constructor(porst) {
        super(porst);
        this.state = {
            msg: "子组件的数据",
        };
    }
    render() {
        return (
            <div>
                <button onClick={this.emit}>显示</button>
            </div>
        );
    }
    emit = () => {
        this.props.btnevent(this.state.msg)
    };
}
ReactDOM.render(<Demo1 />, document.getElementById("root"));
```



# 补充

babel：一般babel.js是ES6转ES5的。

# 问题

+ 不使用ES6箭头函数传递、改变this的指向。
  + 点击事件要修改this的指向。在constructor中 this.事件名= this.事件名.bind(this)



