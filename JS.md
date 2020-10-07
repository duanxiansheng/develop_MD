#### 页面优化的方式：

- 减少类名的使用
- 减少代码padding、margin
- 字体图标；修改颜色方便
- 尽量减少http请求，背景图片
- 图片精灵技术：css sprite技术 往右往下为负
- link标签写在head标签里，style标签写在head标签下面，script标签写在body的结束位置
- 事件委派
- 压缩图片

# Javascript

> 客户端脚本语言，用于用户交互

### 特点：

- 弱类型
- 解释型
- 基于对象
- 事件驱动
- 单线程/异步(callback)

### 作用：

- 动态创建元素
- 动画效果
- 操作元素的属性，样式与内容
- 表单验证
- ajax...100%

### 组成：

- ECMA基础语法

  > 变量、数据类型、运算符、流程控制、数组、函数、对象（属性和方法）、作用域、作用域链、原型、原型链，es6

- BOM浏览器对象模型

  > 地址对象、历史记录对象、window对象

- DOM文档对象模型

  > 获取元素，操作属性，事件，节点，事件对象

### 概念：

> 基于`对象`与`事件驱动`的`松散型` `解释型`语言。

### 引入方式：

- 外部引入方式：

  优化：body标签结束位置

  <script src="index.js"></script>

- 嵌入式：

  > 在html内部写script标签对

  ```
  <script>
  
  </script>
  ```

- 以上两种方式引入的js存在关联，相互访问，相互修改。

### 调试工具：

- 弹框 `alert(1);` 不识别变量，中文；代码从上到下执行，遇到错误的语句停止并报错；
- 输出到控制台 `console.log("输出到控制台");`
- 输出到页面 `document.write("输出到页面中");`
- ***提示用户输入\*** `prompt("提示用户输入")；` `console.log(prompt("提示用户输入",20));`
- 提示确定与取消 `confirm("提示文本");` `confirm("是否关闭");` `consloe.log(confirm("是否关闭")); true false`

### 注释：

- //
- /**/

# 一、变量

> 用来存储数的容器，var

### 命名规范：

- 命名由数字、字母、下划线、$组成，不能以数字开头
- 区分大小写
- 命名要有意义
- 不能用关键字（js中已经用到的）定义变量名
  - 不能用保留字（js将来会用到的）定义变量名
- 首字母大写法 Object
- 驼峰命名法 getElementById

### 赋值方式：

- 先声明一个变量，再赋值
- 声明一个变量的同时赋值
- 先声明多个变量，再赋值 `,`
- 声明多个变量的同时赋值 `,`

### 注意事项：

- 变量的默认值为undefined
- 变量可以赋新值
- 变量可以重复声明
- 一般都需要先声明后访问，如果你先访问后声明，变量值为`undefined` 。浏览器的预解析
- 预解析 var function 只解析到关键字
- 解析 执行
- 当不用var关键字声明变量，变量赋值，不会报错，变量为全局变量
- 当不用var关键字声明变量，变量没有赋值，会报错。

### let:es6

- 声明变量
- 不能够重复声明
- 不存在变量提升（先访问后声明）
- 识别块级作用域

### const：es6

- 声明常量，值不能变化
- 不能重复声明
- 不存在变量提升
- 不能先声明后赋值
- 识别块级作用域

# 二、数据类型

栈区 堆区（引入数据类型） 代码块区

> 根据数据在内存中的存储位置不同进行划分。

### 基本数据类型:(栈)

- number数字型

- string字符串

- boolean布尔型

- undefined

  1. 变量声明未赋值
  2. 函数没有返回值
  3. 形参不传值
  4. 对象没有属性
  5. 数组的越界访问

- null

- symbol(es6)

  - 值是独一无二的，一般用作对象的属性名

    ```
    let mysymbol=Symbol("fun");
    let mysymbol1=Symbol("fun");
     mysymbol 与 mysymbol1 即使有相同的值也认为是不相等的
    ```

  - 对象的属性名

    ```
    let mysymbol=Symbol("fun");
    let mysymbol1=Symbol("fun");
    let obj={
      [mysymbol]:"hello",
      [mysymbol1]:"hello",
    }
    不能用点运算符
    ```

    > 以symbol作为属性名的话，不能用for in 遍历，Object.getOwnPropertySymbols(obj)以数组的形式返回对象Symbol 的键名

### 引用数据类型:(堆)

- object

  > 数组，函数，对象；conslone.log(typeof num);检测数据类型,只看二进制的前三位，null和object前三位一样

| 数据类型  | 值                                                    | typeof的结果     |
| --------- | ----------------------------------------------------- | ---------------- |
| number    | 整数，小数，正数，负数，科学计数法，NaN(not a number) | number           |
| string    | 单双引号                                              | string           |
| boolean   | true、false                                           | boolean          |
| undefined | 变量只声明未赋值，值为undefined                       | undefined        |
| **null**  | null                                                  | **object**       |
| symbol    |                                                       |                  |
| object    | 数组，对象；函数                                      | object；function |

# 三、运算符

### 算术运算符：

> ```
> +` `-` `*` `/` `%` `var++` `++var` `var--` `--var
> ```

隐式数据类型转换

数字字符串console.log(Numder("abc"));

console.log(Numder("123"));

console.log(Numder(true));

console.log(Numder(false));

console.log(Numder(undefined));

console.log(Numder(null));

- `-` `*` `/` `%`:四则运算 /求商

> 如果操作数的数据类型不是number,会隐式调用Number()函数
>
> true：1，false:0,undefined:NaN,null:0,"123":123

- `+`

  - 加法运算

    > 两个操作数都为number型

  - 拼接运算

    > 只要有一个操作数是字符串就做拼接

- `var++` `++var` `var--` `--var`
  - 在前，先算
  - 在后，先算其他，再算
  - ++自增，--自减
  - ++只能作用于变量

### 关系运算符:

> ```
> >` `<` `<=` `>=` `==` `===严格相等` `!=` `!==非严格相等
> ```

> 关系运算符的返回值是布尔值

- 两个操作数都是数字，按照数字大小比较
- 两个操作数都是字符串，按照ASCII值比较
- 如果一个是数字，一个是字符串，先试图将字符串转换为数字，如果转换成功进行比较，转换不成功，输出false
- ===值和数据类型都相等 ==值相等
- `NaN!=NaN` `null===ull` `undefined==null`

### 赋值运算符：

> ```
> =` `+=` `-=` `*=` `/=` `%=
> ```

```
var num=10;
num+=20;//num=num+20
```

### 逻辑运算符：

> ```
> &&` `||` `！
> ```

> 布尔：flase,0,undefined,null,NaN,""都为假（6种）

- && 与

  > 同真为真，返回第一个假值（短路原则），最后一个真值

- || 或

  > 同假为假，返回第一个真值·

- ！ 非

  > 取反

| A     | B     | A&&B  | A\|\|B | !A    |
| ----- | ----- | ----- | ------ | ----- |
| true  | true  | true  | true   | false |
| true  | false | false | true   | false |
| false | true  | false | true   | true  |
| false | false | false | false  | true  |

### 三元运算符：

```
表达式？值1：值2；
```

> 表达式的值是否为真，为真执行结果1，为假执行结果2

### 一元运算符：

- typeof 检测数据类型

- new 实例化对象

- delete 删除对象的属性（es6)

- instanceof：检测对象与构造函数或者类的关系 true false

  ```
  arr instanceof Array
  ```

  

### 特殊运算符：

- `,` 同时声明多个变量
- `（）`提升优先级，函数调用

### 运算符的优先级：

# 四、流程控制

> 按照相应的条件执行相应的代码。

- 顺序结构：按照代码的顺序，从上到下执行
- 分支结构：满足一定的条件，执行相应的代码
- 循环结构：满足一定的条件，重复执行相应的代码

### 分支结构

#### 单分支：

```
if(条件){
  满足条件时执行的语句；
}
```

#### 双分支：

```
if(条件){
  满足条件时执行的语句；
}else{
  不满足条件时执行的语句；
}
```

#### 多分支：

```
if(条件1){
  满足条件1时执行的语句；
}else if(条件2){
  满足条件2时执行的语句；
}else if(条件3){
  满足条件3时执行的语句；
}else{
  以上条件都不满足执行的语句；
}
```

#### 嵌套分支：

```
if(条件1){
  if(条件1-1){
     满足条件1并且满足条件1-1时执行的语句；
  }else if（）{
    
  }else if{}
  else{}
 }else{}
```

#### switch：

```
switch(变量){
  case 值1:语句1;break;//break终止
  case 值2:语句2;break;
  case 值3:语句3;break;
  case 值4:语句4;break;
  default:以上情况都不满足时执行；
}
```

- 值必须为变量能够取到的值，数据类型必须相等
- prompt接收的是字符串
- 如果条件是一个范围，用if else；条件是具体的值，用switch。

### 循环结构：

#### for：

```
for(初始条件;终止条件;步进值)
{
  循环体；
}
```

#### while:

```
while(条件){
     循环体; 
}
```

#### do while:

```
do{
  循环体;
}while(条件)
```

> 区别：当初始条件不满足终止条件时，dowhile会执行一次，while不会执行。

#### 跳出循环的语句：

- break;终止整个循环
- continue; 终止满足条件的本次循环，后面的循环满足条件仍然执行。

# 五、函数

> 对能实现特定功能的代码的封装，能够重复使用。

#### 声明函数的方式：

- function关键字

  ```
  function 函数名(){
    函数体；
  }
  fn1();
  ```

- 匿名函数，以自变量、自面量的方式声明函数

  ```
  var 函数名=function(){
    函数体；
  }
  fn1();
  ```

- 实例化构造函数function,new

  ```
  var 函数名=new Function{
    ' 函数体；'
  }
  fn1();
  ```

> 函数名相同，函数体不同，下面的覆盖上面的

> 以function的方式定义函数可以先访问后声明，但是匿名方式必须先声明后访问。

#### 函数的调用：

- `()` 调用：函数名（）

- 在事件中调用

  ```
  <div onclick="fn()"></div>
  ```

- 函数的自调用

  > 只能调用一次

  ```
  (function fn(){
    //函数体;
  })()
  ```

#### 函数的参数：

> 目的是使函数更加灵活

> 参数可以是任意数据类型，形参只在函数内部起作用。

```
function 函数名(num1,num2){//形参
  函数体；
}
fn1(num1,num2);//实参
```

> 形参只能在函数内部访问

##### 分类：

形参=实参：从左到右，一一对应

形参>实参：多余的形参为undefined,形参的默认值为undefined

形参<实参：

- 利用arguments接收:接收全部参数；是一个object对象

- 剩余参数:接收剩余参数；是一个Array数组 （es6）

  ```
  function fn(a,b,...rest){
  	函数体;
  }
  fn(1,2,3,4,5,6,7);
  ```

> object 类似于数组

##### 参数的默认值：

- 分支结构
- 三元运算符
- 逻辑或 `flag=flag||"<"`
- es6 `function fn(flag="<")`

### 函数的属性与方法:

- name:fn.name 返回函数的名称
- length：fn.length 返回函数形参的个数
- toString():fn.toString 将函数的原码转换为字符串

### 函数的返回值：

> 用return表达式：给函数一个返回值

- 函数没有返回值为undefined
- return可以终止整个函数的执行。continue、break
- 函数中可以有多个return分支，但最终只执行一个return分支
- 返回值也可以是任意的数据类型

### 箭头函数：es6

```
var fn=function(){
  return v;
}
var fn=v=>v;
var fn=(v)=>{return v};//要是有{}，必须加return；没有{}默认有return
```

- 如果函数没有参数，可用（）代替
- 如果函数体中代码多余一条，要用{}包起来
- 如果返回值是对象，json格式，要在对象外面添加（）
- 构造函数不能用箭头函数定义
- 箭头函数内部没有arguments对象
- 箭头函数多用于简化回调函数

### 回调函数：

> 把一个函数当做参数，传递给另一个函数。当做参数的这个函数叫做回调函数。

> 自己记的：使函数更加灵活。

### 递归函数：

> 在函数体内调用本函数，注意要有终止条件。阶乘。

### 闭包：

- 为什么出现：解决在函数外部访问函数内部变量的需求

- 概念：定义在函数内部的函数，使用目标变量，使用的变量不会被回收

- 缺点：变量常驻内存

  ```
  function fn(){
    var num=100;
    function aa(){
      return num;
    }
    return aa;
  }
  let num1=fn()();//aa num
  console.log(num1);
  ```

# 六、作用域

> 变量或函数起作用的范围。 8

- 全局作用域：在整个js代码中都能被访问到的变量
  - 在函数外部用var或let 声明的变量拥有全局作用域
  - 不用var声明但是赋值的变量，拥有全局作用域
- 局部作用域：在函数内部会被访问到的变量
  - 在函数内部用var或let声明的变量，拥有局部作用域
  - 形参拥有局部作用域
- 块级作用域（es6）`{ }`
  - `let const` 识别块级作用域

### 作用域链：

> 当访问变量时，js会为变量创建一个作用域链，规定了变量的访问顺序。

- 访问顺序：从内向外访问
- 局部作用域优于全局作用域

# 七、预解析

### 环境

- 宿主：浏览器
- 执行环境：全局环境、局部环境

### 预解析：

- 按照`script`代码块的顺序解析
- var,function关键字会被提前解析到内存中
- 一个变量名既是全局又是局部变量，局部变量的优先级高于全局变量
- 预解析：函数名与变量名相同，函数名的优先级高
- 定义函数与变量时，名字不能相同。（执行时）

# 九、内置顶层函数：

> 内置：自带；顶层：window的方法

- `Number()` 将任意数据类型转换为数字型

  > true:1;false:0;null:0;undefined:NaN;数字：数字；空字符串：0；数字型字符串：数字；其他字符串：NaN;

- `Boolean()` 将任意数据类型转换为布尔型

  > undefined,null,NaN,false,0,空字符串 false

- `String()` 将任意数据类型转换为字符串型

- `parseInt()` 将字符串转换为整型

  - 数字型字符串，转换为十进制数
  - 忽略空格，从第一个数字到最后一个数字进行转换
  - 不是以数字、空格、-数字开头，其他情况转换为NaN

- `parseFloat()` 将字符串转换为浮点型

  - 如果为整数，不会转换为浮点型，会转换为整型
  - 转换的字符串是一个规范的浮点型，只能是一个小数点。

- `isNaN()` 判断一个数是否能转换为数值型，可以返回的是fslae,不能返回的是true。

- `eval()` 将传入的字符串当做js代码进行执行

#### 作用：数据类型转换

- 强制数据类型转换
- 隐式数据类型转换

# 十、数组

array()数组的构造函数

### 声明数组

- `var arr=[];`

- 实例化对象

  ```
  var arr=new Array();
  var arr=new Array(4);//1个值，代表数组的长度
  var arr=new Array(4,"shr",true);//大于1个值，代表数组的值
  ```

### 数组的赋值

- 声明的同时赋值

  ```
  var arr=[1,2,3];
  ```

- 先声明后赋值

  ```
  var arr=[];
  arr[0]=12;arr[1]=2;arr[2]=22;arr[3]="abc";
  ```

### 数组的访问：

- 下标访问arr[i]，下标的范围：0~arr.length-1;
- 数组中的元素可以是任意数据类型
- 数组可以越界访问，值为undefined

### 数组的遍历：

- for

  ```
  for（var i=0;i<arr.length;i++）{
    arr[i];
  }
  ```

- for in

  ```
  for(var i in arr){
  	i;//下标
    	arr[i];//值
  }
  ```

- for of

  ```
  for(var i of arr){
  	i;//数组中的值
  }
  ```

### 二维数组：

> 数组中的每一个元素都是数组。数组嵌套数组。

#### 访问：

```
arr[i][j]
```

#### 遍历：

```
for(let i=0;i<arr.length;i++){
  for(let j=;j<arr[i].length;j++){
    arr[i][j];
  }
}
```

#### 数组的拷贝

- 浅拷贝 ：地址

  ```
  let arr2=arr1;
  ```

- 深拷贝 ：值

  ```
  let arr1=[1,2,3]
  arr1.forEach(ele=>{
    arr2.push(ele);
  })
  ```

# 十一、对象

> 对属性和方法的集合。

> 属性：描述对象的特征。

> 方法：描述对象的功能

### 声明对象的方式

- 字面量方式声明：json格式 格式转换

  ```
    "属性名":"属性值",
    方法名:function(){
      	
    }//最后一个不写逗号
  var asus={//asus对象
    color:"blank",
    size:14,//size:'14px',
    play:function(){
      	console.log("play");
  	},
   study:function(){
      	return "study";
  	}
  };//分号
  //访问属性与方法
  //1.对象.属性名2.对象['属性名']
  //1.对象.方法名()2.对象['方法名']()
  console.log(asus);
  console.log(asus.color);
  asus.play();
  //增加 对象.属性名=属性值  对象.方法名=函数
  asus.price=30000;//新增一个属性;后访问
  console.log(asus);
  asus.video=function(){
    //函数体;
  }
  //删除属性
                             //删除对象 asus=null;
  delete 对象.属性名
  delete asus.color
  //修改
  对象.属性名=新属性值
  ```

- 实例化构造函数

  ```
  function Computer(){
    this.color="black";
    this.play=function(name){
      return name+"play"
    };//这个分号可有可无
    this.play=function(name){
      return name+"play"
    }
  }
  var apple=new Computer();
  //增加
  apple.price=16000;
  ```

  this： 函数内部存在this ，谁调用函数this指向谁，

  window，实例化构造函数的对象

- 实例化Object

  ```
  var obj=new Object();
  ```

- class (es6) 定义类 类要大写

  ```
  class Computer{
    //构造方法 es5
  	constructor(size){
        this.size=size；
      }
    //相当于原型
    play(){
      
    }
    study(){
      
    }
  }
  var apple=new Computer(12);
  ```

### 对象的遍历：

for in

```
for(let i in obj){
  i;//对象属性名字
  obj[i];//值
}
```

### constructor ：

> 原型对象的属性，用来指向原型所对应的构造函数

### instanceof:

> 判断对象与构造函数的关系。true false

### new运算符做了什么？

- 创建空对象obj
- 将obj的`__proto__`指向构造函数的原型
- 将构造函数内部的`this`指向`obj`

### this

### 原型 原型对象：prototype

> 构造函数的属性，存放公共的属性和方法，节省空间。

```
构造函数.prototype={
	属性名：属性值,//json格式
    方法名：方法,
}；//这个分号也是可有可无
```

### 原型链：

> 在访问对象的属性与方法时，遵循的一条规则。从对象，到对象的原型，再原型的原型。如果属性不存在返回`undefined` ；方法不存在，报错。
>
> 如果对象自身和它的原型上都定义了同一属性名，优先读取对象自身的属性。
>
> 原型链通过`__proto__` 实现。
>
> 通过原型链实现继承。

> 自己记的：每一个函数都有一个prototype属性，指向一个对象。原型对象的属性不是实例对象自身的属性。

### 对象的特性：

#### 封装：

> 将对象的组成组合起来。构造函数与prototype

- 工厂函数
- 构造函数
- prototype
- 混合函数：构造函数与prototype

#### 继承：

- 原型继承：prototype

- call:`fun.call(obj,参数1,...)` 将fun的this指向改变为obj

- apply：`fun.apply(obj,[参数1,参数2,...])` 将fun的this指向改变为obj

- bind：`fun.bind(obj,参数1,...)()` 将fun的this指向改变为obj。返回对应的函数，需要以后调用。call与apply是立即执行函数。

- extends:(es6)

  ```
  class Point{
    constructor(x,y){
       this.x=x;
       this.y=y;
    }
    say(){
      return "say";
    }
  }
  class Points1 extends Point{
    constructor(x,y,color){
      super(x,y);
      this.color=color;
    }
    circle(){
      return "123";
    }
  }
  ```

  - 用 extends实现子类继承父类
  - 在子类构造方法中添加super()
  - 在子类中访问父类的属性用`this.父类属性名`
  - 在子类中访问父类的方法用`super.父类方法名`

# 数组对象

### 属性：

- length：数组的长度
- constructor:返回对象的构造函数

### 方法：

参数三个

1. `arr.push()` 向数组添加一个或多个元素，添加到数组的末尾，改变原数组，返回新数组长度。
2. `arr.unshift()` 向数组的开头添加一个或多个元素，改变原数组，返回新数组长度。
3. `arr.shift()` 删除数组中第一个元素，并返回第一个元素的值，会改变原数组
4. `arr.pop()` 删除数组中最后一个元素，并返回最后一个元素的值，会改变原数组
5. `arr.concat(arr1,arr2)` 实现一个或多个数组的拼接，返回拼接后的数组，不会对原数组产生影响。
6. `arr.every(function(ele,index){ return ele>0})` 当所有元素都满足条件时返回true，否则返回false
7. `arr.some(function(ele,index){ return ele>0})` 只要有一个元素满足条件时返回true，否则返回false
8. `arr.includes()` 判断数组中是否包含指定的值，包含返回true，否则返回false。
9. `arr.indexOf()` 返回指定值在数组中首次出现的下标，不包含返回-1；
10. `arr.lastIndexOf()` 返回指定值在数组中首次出现的下标，从后向前访问
11. `arr.join("-")` 将数组转换为字符串，默认用逗号`,`拼接
12. `arr.toString()` 将数组转换为字符串,不会改变原数组
13. `arr.toLocalString()` 将数组转换为本地字符串，使用地区特定的分隔符把生成的字符串连接起来，形成一个字符串
14. `arr.filter(function(ele,index){return ele>3;})` 一个集合到一个更小的集合
15. `arr.map((ele)=>{return ele*2;})` 映射，会产生一个新数组，不改变原来数组的值。必须有返回值，如果没有return，那么新数组的每一项都为undefined
16. `arr.forEach(function(ele,index){})` 数组遍历
17. `arr.slice(start,end)` 截取 从开始的下标到结束的下标，但不包含结束的下标，结束下标-1。如果结束没有值，截取剩余所有的元素。
18. `arr.splice(start,length)` 删除 从开始的下标删除指定的长度，改变原数组，当length为0时，做添加功能，当length不为0时，先删除指定的长度个元素，在添加
19. `arr.sort(function(a,b){return a-b(从小到大) / b-a (从大到小);})` 排序
20. `arr.reverse()` 颠倒顺序，反转，会改变原数组
21. `arr.reduce(function(tot,ele){ return tot+ele})` 数组从左向右累计求和
22. `arr.reduceRight(function(tot,ele){ return tot+ele})` 数组从右向左累计求和
23. `arr.flat()` 数组平坦
24. `arr.flatMap()` 对数组的每个成员执行一个函数
25. `arr.find(function(ele,index){return ele>1;})` 返回数组中满足条件的第一个元素，如果不存在返回undefined
26. `arr.findIndex(function(ele,index){return ele>1;})` 返回数组中满足条件的第一个元素的下标，如果不存在返回-1

# Math对象

### 属性

- `Math.PI`

### 方法:

- `Math.floor()` 向下取整
- `Math.ceil()` 向上取整
- `Math.random()` 取0-1的随机数。`Math.random()*(b-a)+a`
- `Math.abs()` 取绝对值
- `Math.max()` 取最大值
- `Math.min()` 取最小值
- `Math.pow(x,y)` 返回x的y次幂
- `Math.round()` 四舍五入

# 日期对象

- `var date=new Date(2019,9,1)` 实例化日期对象

### 方法：

- 当前时间 date.toLocaleTimeString（）// 上午12：12：12
- 当前时间 toLocaleString
- 年 `date.getFullYear()`
- 月 0-11 `date.getMonth()`
- 日 1-31 `date.getDate()`
- 周中的某一天 0-6 ；0表示周日 `date.getDay()`
- 时 `date.getHours()`
- 分 `date.getMinutes()`
- 秒 `date.getSeconds()`
- 获取到1970年1 月1 日的毫秒数 `date.getTime()`

### 属性：

- constructor
- prototype

自己记的：

 console.log(console);

 console.clear();清除控制台

# 字符串对象

### 属性：

- length 字符串长度

### 方法：

- `str.charAt (index)` 返回指定下标的字符串
- `str.charCodeAt (index)` 返回指定下标的字符的ASCII码值
- `String.fromCharCode(ASCII)` 返回指定的ASCII对应的字符
- `str.indexOf()` 返回指定字符串首次出现的下标
- `str.lastIndexOf()` 倒序返回指定字符串首次出现的下标
- `str.replace("被替换的内容", "替换后的内容")` 替换，替换首次出现的
- `str.slice(start,end)` 截取，从开始的下标到结束的下标，但是不包含结束的下标
- `str.substring(start,end)` 截取，不识别负数
- `str.substr(start,length)` 截取，从开始的下标截取指定的长度
- `str.split('')` 将字符串按照特定标识转换为数组 ，用逗号隔开
- `str.toUpperCase()` 将字符串全部转换为大写
- `str.toLowerCase()` 将字符串全部转换为小写
- `str.trim()` 去掉字符串的左右空格
- `str.trimRight()` 去掉字符串的右空格
- `str.trimLeft()` 去掉字符串的左空格
- `str.concat()` 连接两个或多个字符串
- `str.join('')` 转换为字符串
- `str.reverse()` 反转

# Javascript对象的分类：

- 内置对象：ECMAScript内置的对象，直接拿来用就可以，不需要实例化

  - 内置顶层对象(global): Math;

- 本地对象:需要实例化才能用

  - String;
  - Boolean;
  - Number;
  - Function;
  - Array;

- 宿主对象: BOM DOM

  > 宿主：js的执行环境

# Object对象：

### 方法：

- `Object.assign(obj1,obj2,obj3)` 对象的拼接，将obj2,obj3拼接到obj1中，会改变原对象
- `Object.is(a,b)` 比较两个值是否相等；基本数据类型比的是值，引用数据类型比的是地址
- `Object.keys(obj)` 以数组的形式返回对象的键名
- `Object.values(obj)` 以数组的形式返回对象的键值
- `Object.getOwnPropertyNames(obj);` 以数组的形式返回对象的键名
- `Object.getOwnPropertySymbol(obj);` 以数组的形式返回对象中Symbol的键名

# 正则对象

> 正则表达式用来匹配或检索符合某一种规则的字符，常见于表单验证当中，判断用户名是否满足要求或者判断手机号码是否符合规则、验证身份证号码是否符合规则

### 创建正则对象的方式：

- ```
  let reg = /正则表达式/
  
  let reg1 = new RegExp();
  ```

- 模式修正符

  | 符号 | 描述                         |
  | ---- | ---------------------------- |
  | i    | 执行对大小写不敏感的匹配     |
  | g    | 执行全局匹配（查看所有匹配） |
  | m    | 执行多行匹配                 |

  

### 组成正则对象的最小单元——原子

| 原子 | 描述                                           |
| ---- | ---------------------------------------------- |
| \d   | 匹配0-9之间的一个字符                          |
| \D   | 匹配除了0-9之间的一个字符                      |
| \w   | 匹配数字、字母、下划线字符                     |
| \W   | 匹配除了数字、字母、下划线的字符               |
| \n   | 用于匹配换行字符或者当成换行字符写入到字符串中 |
|      |                                                |

|  原子表  | 含义                                |
| :------: | :---------------------------------- |
|    []    | 只匹配其中的一个字符                |
|  [0-9]   | 匹配0-9之间的一个字符，与\d相同     |
|  [^0-9]  | 匹配除了0-9之间的一个字符，与\D相同 |
|          |                                     |
|          |                                     |
| **量词** | **含义**                            |
|   {n}    | 表示前面的原子被重复n次             |
|  {0,n}   | 前面的原子重复0-n次                 |
|  {1,n}   | 前面的原子重复1-n次                 |
|    +     | 前面的原子重复1-n次                 |
|    *     | 前面的原子重复0-n次                 |
|   {n,}   | 规定前面的一个原子重复n次及n次以上  |
|   ?=n    | 匹配字符后面紧跟n的字符             |
|   ?!n    | 匹配字符后不跟n的字符               |

| 边界        | 描述                   |
| ----------- | ---------------------- |
| ^           | 从字符串的开头进行匹配 |
| $           | 匹配到字符串的结尾     |
| \b          | 匹配单词边界           |
| \B          | 匹配非单词边界         |
| ¦（管道符） | 表示或者的意思，       |

# DOM对象：

> 操作html页面

### 一、DOM对象的属性：

| 属性            | 描述                                 | 读写 |
| --------------- | ------------------------------------ | ---- |
| URL             | 网站的url                            | 只读 |
| title           | 网站的标题                           | 读写 |
| charset         | 字符编码                             | 只读 |
| forms           | 页面中的所有form标签                 | 只读 |
| images          | 页面中的所有img标签                  | 只读 |
| body            | body标签                             | 只读 |
| head            | head标签                             | 只读 |
| documentElement | html标签                             | 只读 |
| cookie          | cookie信息(登录信息，爱好等存储信息) | 读写 |

### 二、获取元素的方法：

- 标签名：html集合 类数组

  ```
  document.getElementsByTagName("标签名")
  ```

- 类名：html集合 类数组 小标访问

  ```
  document.getElementsByClassName("类名")
  ```

- id：一个dom对象

  ```
  document.getElementById("id名")
  ```

- name:节点列表 类数组 小标访问

  ```
  document.getElementByName("name名")
  ```

- 获取第一个元素： DOM对象

  ```
  document.querySelector("css选择器")
  ```

- 获取所有元素：节点列表 for

  ```
  document.querySelectorAll("css选择器")
  ```

### 三、操作内容：

- 普通标签
  - innerHTML:识别标签对 `dom对象.innerHTML`
  - innerText：不识别标签对 `dom对象.innerText`
- value 表单

### 四、操作属性 html

#### 标准属性：

- 获取：obj.attr 对象.属性名
- 设置：obj.attr=value 对象.属性名=属性值

#### 非标准属性：

- 获取：`obj.getAttribute(name);`
- 设置：`obj.setAttribute(name,value);`
- 是否包含：`obj.hasAttribute(name)` true false

### 五、操作样式 css行内样式：

```
obj.style.css属性名=属性值;
//属性中有-，第二个单词的首字母大写
//移入事件
obj.onmouseenter=function(){

}
//移出事件
obj.onmouseleave=function(){

}
```

自己加的：

```
//单击事件
obj.onclick=function(){

}
//双击事件
obj.ondbclick=function(){
  
}
```

#### 批量操作：

- 类名：
  - 添加：`obj.classList.add("类名")`
  - 删除：`obj.classList.remove("类名")`
  - 切换：`obj.classList.toggle("类名")`
  - 是否包含：`obj.classList.contains("类名")`
  - 替换
- id:
  - 添加：`obj.id="id名"`
  - 删除：`obj.id=""`

#### 获取样式：

- `getComputedStyle(obj,null).attr` 获取内联css,外部引入css中的样式
- 将字符串转换为整型 `parseInt()`

### 六、节点：

> 在html中，所有的事物都被视为节点，节点之间是相互联系。整个html文件被视为节点树。

#### 节点的分类:

- 元素节点：标签
- 属性节点：html属性
- 文本节点：文字，空格，换行
- 注释节点
- 文档节点

#### 节点详细信息：

#### 节点的属性:

- 对象.parentNode 获取父节点
- 对象.childNodes 获取子节点
- 对象.firstChild 获取第一个子节点
- 对象.lastChild 获取最后一个子节点
- 对象.nextSibling 获取下一个兄弟节点
- 对象.previousSibling 获取上一个兄弟节点

#### 元素节点的属性:

- 对象.parentElement 获取父元素节点
- 对象.children 获取子元素节点
- 对象.childElementCount 获取子元素节点的个数
- 对象.firstElementChild 获取第一个子元素节点
- 对象.lastElementChild 获取最后一个子元素节点
- 对象.nextElementSibling 获取下一个兄弟元素节点
- 对象.previousElementSibling 获取上一个兄弟元素节点

#### 节点的方法:

- 创建：document.createElement(标签名)
- 操作内容、操作属性、操作样式
- 插入节点：parent.appendChild（子节点）
- 插入节点到指定位置：parent.insertBefore(新节点，位置)
- 删除节点：parent.removeChild(子节点)
- 替换节点：parent.replaceChild(新节点,旧节点)
- 克隆节点：node.cloneNode(boolean) false 克隆节点本身 true 克隆子节点以及本身

### 七、事件：

> 事件源.事件=事件处理函数

#### 添加事件的方式：

- 行内事件： ``

- on+type:如果给同一事件源添加相同的事件，后者的事件处理函数覆盖前者的。

  - 鼠标：click、mouseenter、mouseleave、dblclick
  - 键盘：keydown、keyup
  - 表单:focus、blur(失去焦点)、change(改变并且失去焦点)、input(表单的值实时改变)
  - window:load(页面加载)、scroll(页面的滚动)

- 事件监听 ：同一个事件源的同一个事件可以添加多个事件处理函数

  - 添加事件：

    ```
    obj.addEventListener(even(事件名称),callback（回调函数）,boolean);
    obj.addEventListener("click",fn,false);//false表示在冒泡阶段调用
    obj.addEventListener("click",function(){},true);//true表示在捕获阶段调用事件处理程序
    ```

  - 移除事件：不能使用匿名函数，要获取函数的引用

    ```
    obj.removeEventListener(even,callback,boolean);
    ```

#### 事件对象：

> 记录事件发生时的详细信息

> event：事件处理函数的第一个参数。

```
box.addEventListener("click",function(e){
  console.log(e);
},flase);
```

自己记的：

> 属性：
>
> 方法：
>
> 适用场景：时间点击需要得到它的详细信息， 阻止浏览器的默认行为

#### 鼠标事件对象：

- `offestX` 距事件源左上角水平方向的距离 补充：谁调用？事件对象
- `offesY` 距事件源左上角垂直方向的距离
- `clientX` 距浏览器左上角水平方向的距离
- `clientY` 距浏览器左上角垂直方向的距离
- `pageX` 距页面左上角水平方向的距离
- `pageY` 距页面左上角垂直方向的距离

#### 键盘事件对象

##### 属性

- key 当前所按键的名称
- keyCode 当前所按键的键盘码 打字游戏
- altKey
- ctrlKey
- shiftKey
- 左37 上 38 右39 下40
- `e.target` 获取事件源

##### 方法

- `preventDefault()` 阻止浏览器的默认行为
- 阻止冒泡型事件流的方法`e.stopPropagation()`

阻止a连接的默认行为：

- # 

- javascript:;

- javascript:void(0);

- js中preventDefault()

```
//html
<a href="" class="clearA">Google谷歌</a>
//js
let clearA=document.querySelector(".clearA");
    clearA.onclick=function (e) {
        e.preventDefault();
    }
```

#### 事件流：

> 事件发生时会在元素节点与根节点之间按照顺序传播的事件。

##### 两种类型：

不明确：根节点 明确：当前元素

- 冒泡型事件流:从明确的元素到不明确的元素。on+type；事件监听false
- 捕获型事件流:从不明确的元素到明确的元素。事件监听true

##### 三个阶段：

- 捕获阶段
- 目标阶段
- 冒泡阶段:阻止冒泡型事件流的方法`e.stopPropaga`

### 事件委派(事件代理)：

- 定义：将子元素的事件添加在父元素身上
- 原理：冒泡型事件流
- 获取目标元素：`e.target` (小程序上也会用到，a链接的打开方式)
- 判断目标元素：
  - 判断内容 ：e.target.innerHTML innerText
  - 标签名：e.target.nodeName(大写的标签名)
  - 是否包含属性：e.target.hasAttribute(“属性名”)
  - 是否包含类名：e.target.classList.contains("类名")
- 应用场景：
  - 需要给大量元素添加事件时，提升代码的运行效率，减少对dom元素的操作
  - 给动态创建的元素添加事件的时候也要用事件委派

### 八、元素的尺寸和位置：

- 元素的真实宽度 `obj.offsetWidth` 内容+内填充+边框

  - 元素的真实高度 `obj.offsetHeight` 内容+内填充+边框

- 距文档顶部的距离：`obj.offsetTop`

- 距文档左部的距离：`obj.offsetLeft`

- 有滚动条的元素滚动时距滚动条顶部的距离：`obj.scrollTop`

- 有滚动条的元素滚动时距滚动条左部的距离：`obj.scrollLeft`

  ```
  window.onscroll=function(){
    obj.scrollTop
  }
  ```

  

# BOM 浏览器对象模型：

> 管理窗口与窗口之间的通信
>
> window是核心对象

- window
- window.console 控制台
- window.history 历史记录对象
- window.location 地址对象
- window.navigator 导航器对象

### window对象：

#### 属性：

- innerWidth: 浏览器的宽度 ie9
- innerHeight: 浏览器的高度 ie9
- document.documentElement.clientWidth: 浏览器的宽度 ie8及以下
- document.documentElement.clientHeigth: 浏览器的高度 ie8及以下

#### 方法：

- alert() 警告框

- prompt() 提示用户输入的对话框

- confirm() 有确定与取消的对话框

- open() `window.open(url)` 在新的标签页打开新的窗口

- close() `window.close();` 关闭本窗口

- **时间函数**，定时器：js中的一个异步

  - 时间函数：间隔一定的时间，重复不断地执行代码

    ```
    setInterval(function(){
      
    },1000)
    ```

  - 清除时间函数：

    ```
    window.clearInterval(t);
    ```

  - 时间函数：间隔一定时间，执行一次代码

    ```
    let t=setTimeOut(function(){
     
    },1000)
    
     clearTimeOut(t);
    ```

    

### history对象：

#### 属性：

- length 记录历史记录对象长度

#### 方法：

- `history.forward()` `history.go(1)`前进
- `history.back()` `history.go(-1)`后退
- `history.go(0)` 刷新

### location对象：

#### 属性：

- `href` 获取或设置页面的url地址
- `origin` 协议 域名 端口号
- `host` 域名 端口号
- `hostname` 域名
- `port` 端口号
- `pathname` 路径
- `search` 查询字符串
- `hash` 哈希
- `protocol` 协议

#### 方法：

- `reload()` 重新加载本页面
- `replace(url)` 用指定的url替换本页面

### 总结：

#### js刷新本页面方法汇总：

- history.go(0)
- location.reload()

#### js跳转页面方法汇总：

- window.open(url)

- location.href=""

- location.assign(url)

  

自己加的：

轮播图：

- 初始化，选中一个点和一个图
- 声明一个全局变量num=0
- 时间函数
  - 获取元素
  - 增加1
  - 当前的添加样式，清除剩余的样式
  - 判断num3

双下标轮播图：

# Ajax

### 是什么：

> 异步的Javascript和XML。创建快速动态网页。

### 做什么：

> 发送和接收数据
>
>  在不重新加载页面的情况下发送请求给服务器。
>
>  接受并使用从服务器发来的数据。

> 为什么：局部刷新，如果不采用ajax，整个页面将会都刷新

- 同步：代码从上到下执行，到它就执行。
- 异步：代码不按照从上到下的顺序执行，触发时才执行。 ( 时间函数，事件，ajax )

### ajax的使用：

#### 核心对象：XMLHttpRequest，

### 同源策略：

> 协议，域名，端口相同

### 跨域：Access-Control-Allow-Origin

#### 解决1：jsonp

原理：是在页面中动态的创建一个script标签对，因为在页面中src是没有跨域问题

> 与json没有什么关系

> script标签没有跨域限制的特点。
>
> 是动态的创建一个script标签对，

### 代理

在项目下创建一个vue.config.js

# json

> 是什么：轻量级的数据交互格式，JavaScript对象的表示法。

# 本地存储：

> 将一些数据存储在客户端

### localstorage

- 特点：永久性存储，5M-10M
- 应用场景：1.数据存储在本地，进行第二次访问2.多窗口访问数据（同一域名）
- 属性：
  - `localstorage.length` 获取长度
  - `localstorage.key=value` 添加数据
  - `localstorage.key` 查询数据
- 方法：
  - `localstorage.setItem(key,value)` 添加
  - `localstorage.getItem(key)` 查询
  - `localstorage.removeItem(key)` 移除
  - `localstorage.clear()` 清除整个 localstorage
- 数据格式转换：
  - `JSON.stringify()` 将对象转换为字符串
  - `JSON.parse()` 将字符串转换为对象

### Session Storage

- 特点：一次会话 5M-10M 短期存储
- 方法：
  - `sessionStorage.setItem(key,value)` 存
  - `sessionStorage.getItem(key)` 取
  - `sessionStorage.removeItem(key)` 删除
  - `sessionStorage.clear()` 清空
  - `sessionStorage.setItem.key=value` 存

### session:

- 

  

# 插件

Echarts

swiper

layui

forpage

# es6：

- let const 声明变量与常量

- 块级作用域

- 剩余参数

  > 接收实参，允许长度不确定的实参作为一个数组

- 箭头函数

- 给参数赋默认值

- 模板字符串

- class类

- symbol数据类型 即使一样了，也认为不一样

- Set数据结构

  - 成员唯一的数组，可以实现数组的去重
  - add() delete() has() clear() keys() values() enteries() forEach() size

- Map数据结构

  - 类似于对象，键值对的集合，键可以是任意数据类型
  - Map与数组，Map与对象的转换

- 解构赋值

  > 按模式匹配的方式，为变量进行赋值

  - 数组
  - 对象 :`let {obj1,obj2}={obj1:1,obj2,2}`
  - 字符串：`let [a,b,c]="efg";`

- 扩展运算符

  > 将一个数组转换为用逗号分隔的参数序列

  - `...[1,2,3]` 1 2 3
  - `{...obj,obj1}` 对象的连接

- Iterator遍历器：

  - 概念：提供了一个遍历接口，让不允许用`for...of` 进行遍历的数据类型添加Symbol.iterator属性，从而可以使用`for...of` 进行遍历
  - 普通对象：数字作为键名，添加`length`属性; `[Symbol.iterator]:Array.prototype.[Symbol.iterator]`
  - Array NodeList String Set Map

- 

# Ajax：

## 是什么

是异步的Javascript和XML；(Asynchronous JavaScript And XML)使用XML HttpRequest对象与服务器通信

## 做什么

发送和接受数据

## 怎么做

- 实例化XMLHttpRequest对象；

```
let ajax=new XMLHttpRequest();
```

- 用xml.open打开链接 ：ajax.open("get/post",url,asyns)
- 在所有的准备都做好了后，向服务器发送请求，使用send();
- 监听请求数据的状态，确定请求数据成功，onreadystatychange事件;
- 

## Ajax的使用：核心对象

## 同源策略：

## 跨域：Access-control-Allow_Origin

### 解决１：jsonp



## json

> 轻量级的数据交互格式，ｊｓ对象的表示法

JSON.Stringify

同步：

异步：只有事件、时间函数、ajax是异步

## 发送方式：

- GET方式：

- POST方式：application／ｘ－ｗｗｗ

  

## 本地存储：

> 讲一些数据存储在客户端

### localStorage

- 特点：保存的期限为永久性存储；大小5MB-10MB之间
- 应用场景：
  1. 将数据存在本地，进行第二次访问；
  2. 多窗口访问数据（同一域名下使用）；
- 属性：
  - 长度:`localStorage.length` 获取长度
  - `localStorage.key-value` 添加与查询 数据；
  - `localStorage.key` 查询数据
- 方法：
  - `localStorage.setItem(key,value)` 添加
  - `localStorage.getItem(key)` 查询;
  - `localStorage.removeItem(key)` 删除
  - `localStorage.clear()` 清楚整个local Storage
- 数据格式转换：
  - `JSON.stringify()` 将对象转换为字符串；
  - `JSON.parse()` 将字符串转换为对象；

异步编程：

> setTimeout、事件、Ajax；

Ajax：

> Ajax是指利用XMLHttpRequest对象，在客户端向服务器端；
>
> Ajax是用于创建快速动态网页的一门技术；

#### Ajax请求五部曲

- 实例化XMLHttpRequest()

  > let xml=new XMLHttpRequest();

- 使用open方法准备发送请求

  > xml.open(请求类型，请求地址，是否异步)
  >
  > xml.open("GET","[http://www.baidu.com](http://www.baidu.com/)",'true')

- 使用send方法发送请求

  > xml.send()

- 使用inreadystatechange事件监听当前的请求状态，确保成功以后进行数据的渲染

  > ```
  > xml.onreadystatechange=function(){
  >    //判断请求成功
  > 	if(xml.response===4){
  > 	//判断相应成功
  >        if(xml.status===200){
  >        	 //保存数据
  >          let data = xml.response
  >        }
  > 	}
  > }
  > ```
  >
  > 

- 在事件处理程序中判断条件，进行数据的渲染

#### 请求状态和相应状态

- 请求状态

  > 请求状态被保存在xml对象的ready State属性中，有5个值，分别对应如下：

  - 0：
  - 1：
  - 2：
  - 3：
  - 4：

- 响应状态

  > 响应状态保存在xml的status属性中，状态码分别如下：

### ajax封装

在Ajax请求中，请求的地址url，请求的方式type，极大的方便了页面的请求

因为需要的参数过多，所以不讲参数一一传递，将他们整体放置到一个对象中，将对象作为参数进行传递

```
obj={
  url="",   //请求地址
  data:"",  //请求参数
  dataType:"",  //请求数据格式
  type:"",  //请求方式
  async:"",  //是否支持异步
  success:callback,//请求成功以后要执行的回调函数
  error:callback,  //请求失败以后要执行的回调函数
}
function  ajax(obj){
  
}
```

post请求参数需要放在send中进行传递

数据获取成功执行success回调函数，需要判断是否存在success；

## ES6新增特性

### Symbol

> 在ES6之前，对象的属性名字必须是字符串，当我们引用一个对象的时候，添加属性时有可能会影响原先对象中的属性，造成属性名字的冲突，为了解决这个问题，ES6中新增了Symbol独一无二的值，用过Symbol生成的值可以保证不会重复。将这个值作为对象的键名字可以保证不冲突

每次调用一次Symbol（）都会生成一个独一无二的值

```
let sym = Symbol();
//Symbol中可以接受一个字符串作为参数，用来区分Symbol；


let a = Symbol('aaa');
let b = Symbol('aaa');

console.log(a===b); //false
```

#### 新增数据结构

> 在ES6之前，数据结构主要有数组和对象，ES6中戏赠了set和map数据结构

#### Set数据结构

> Set是一个构造函数，使用Set数据结构必须进行new实例化
>
> Set数据结构中的成员的值都是独一无二的；

set对象，map

set本身是一个构造函数，类似于数组，里面的每个成员都是唯一的，

##### Set属性：

- size：返回Set构造函数的成员个数

##### Set方法：

| 方法名       | 参数         | 返回值              | 描述                      |
| ------------ | ------------ | ------------------- | ------------------------- |
| set.add()    | 被添加的成员 | 添加成员后的Set对象 | 给set结构中添加传入的成员 |
| set.delete() | 被删除的成员 | Boolean             | 删除指定的set成员         |
| set.has()    | 被判断的成员 | Boolean             | 判断某个成员是否存在      |
| set.clear()  | 无           | undefined           | 清空所有的成员            |

- set.add(); 一次只能添加一个，添加多个如：rex.add(1).add(2)；链式调用中只有add可以

  > set.add() 这个方法输出后是一个对象所以可以链式调用

- set.delete();

- set.has();

- set.clear();

#### Map数据结构

> 也是一个构造函数

### Promise对象

> Promise对象是最早提出的解决异步问题的特性。
>
> 在Promise对象中其实封装了在未来某一个阶段会执行的代码，等到异步问题处理完成以后再去执行
>
> 在Promise对象中有then，catch等方法，用来处理成功或失败以后的代码

**其实Promise对象就是将回调的过程封装起来，让整个回调看起来更加的整洁**

#### Promise对象的实例化

> ```
> new Promise((resolve,reject)=>{
> 	//resolve接受异步处理成功时的回调函数，
> 	//reject接受异步处理失败时的回调函数
> })
> ```

- then();处理异步成功后需要执行的代码
- catch()；用来接受异步失败的信息
- Promise.resolve()；将其他的数据转为promise对象
- Promise.all()；将多个promise对象转为一个promise对象

## 本地存储

### cookie

| 标题     | 介绍                                                         |
| -------- | ------------------------------------------------------------ |
| 存储方式 | 键值对的方式存储                                             |
| 存储大小 | 存储内容不得超过4K，最多可存储20个cookie                     |
| 访问     | 不同域名不可以互相访问cookie                                 |
| 清理机制 | IE呵呵Opera定期将不常使用的进行清理，也可以设置存储期限，FireFox会随机清理cookie |
| 缺陷     | 每次http请求都会携带cookie，浪费带宽                         |
| 应用     | 购物车、登录状态                                             |

### localStorage

> 本地存储：存储数据量大，5~10M之间，对于H5应用而言，这个数据量已经足够了；并且访问速度很快，具有永久存储的机制。

| 标题     | 介绍                                                         |
| -------- | ------------------------------------------------------------ |
| 存储方式 | 键值对                                                       |
| 存储大小 | 5~10M                                                        |
| 存储机制 | 永久存储，除非人为删除                                       |
| 访问     | 不同域名无法访问                                             |
| 主要应用 | ajax请求数据，需要长期保存的数据                             |
| 缺陷     | 同样的数据不能跨域共享，所以不要存储业务关键信息以及安全性信息 |

#### 方法

- 添加 `localStorage.setItem(key键,value值)`
- 获取 `localStorage.geiItem(key键)`
- 移除 `localStorage.removeItem(key)`
- 清除 `localStorage.clear()` 清除所有的本地存储

### sessionStorage

> 短期存储，当本页面关闭后数据就会消失，除了存储机制与localStorage不同，其他相同；

### 三种存储方式的区别总结

#### 相同点

都保存在浏览器端，同源的

#### 不同点

1. 传递方式不同
   - cookie数据始终在同源的http请求中携带（即使不需要），即cookie在浏览器和服务器间来回传递。
   - sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。
2. 数据大小不同
   - cookie数据不能超过4k
   - sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
3. 数据有效期不同
   - cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭。
   - sessionStorage：仅在当前浏览器窗口关闭前有效。
   - localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；

# 日期对象

> 

在js中事件是从1970年00:00:00开始的

先实例化一个对象

```
let date = new Date();


data.getDate();  //
```

| 方法                   | 描述                                           |
| ---------------------- | ---------------------------------------------- |
| date.getDate()         | 获取月份中的某一天                             |
| date.getDay()          | 获取周中的某一天，0-6，0表示周日               |
| date.getFullYear()     | 获取四位数的年份                               |
| date.getHours()        | 获取当前的小时数                               |
| date.getMilliseconds() | 获取当前的毫秒数                               |
| date.getMinutes()      | 获取当前时间 的分钟数                          |
| date.getMonth()        | 获取当前的月份，0-11，获取的月份比实际月份小一 |
| date.getSeconds()      | 获取当前的秒数                                 |
| date.getTime()         | 获取到1970年1月1日00：00：00的毫秒数           |
|                        |                                                |

## 时间戳

> 保存的时间一般是不会时非常标准的时间格式，而是表示被保存时间的一串数字，这个数字就是时间戳。

- `Date.parse(new Date());` //会将毫秒级的数字都变成0，不准确
- `(new Date()).valueOf()` 通过这个方法，将对象转为最初始的状态；
- `new Date().getTime()`
- `Number(new Date())` 将当前的时间转为一个数值型，也就是时间戳
- `Date.now()` 返回当前时间的时间戳

# jQuery

find 用来找元素内部的子元素

on

> 封装好的函数库

### jQuery的特点

- 隐式循环

  > jQuery本质上是一个对象，在对象内部将获取到的DOM对象通过循环保存到jQuery对象身上，然后在jQuery方法调用DOM元素的时候使用的jQuery身上的属性

  **隐式循环：jQuery中为我们隐式进行了循环，将获取到的每一个DOM对象都设置了需要的样式或文本内容**

- 链式调用

  > jQuery对象中的方法，返回值为jQuery对象(this),所以可以继续去调用对象的方法，实现链式调用