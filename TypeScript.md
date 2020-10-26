### 定义

布尔值-数字-字符-数组

```
let isDone:boolean =false

let num1:mumber =10

let str:string = "123321"

```

数组

```
数组 let arr:number[] = [1,2,3]
push时，也不可以穿字符串
另一种写法,泛型写法
	let arr1:array<number>=[1,2,3]
 接口定义数组
 	interface NumberArray{
 		[index:number]:number
 	}
```

空值void:定义函数不返回任何内容

```
function abc():void{}
```

定义undefined

```
	let u:undefined = undefined

	let n:null = null
```

任意类型的any

```
	let abc:any= “123”
```

> 定义好了变量类型，重新赋值只能赋值变量类型的

### 泛型T

### 类型推断

声明变量的时候如果没有赋值变量类型，那么该变量就会被 推断为一开始赋值的的类型。

### 联合类型

可以设置多个类型，既可以是字符也可以是数字

````
let star:string|number = "acc"

star = 123
````

### 类接口

​	接口定义的属性不能添加和减少

```

interface Dog{
	name:string;
	age:number;
	isreaister:boolean
}

let data:Dog{
	name:"张三",
	age:1,
	isreaister:true
}
	// 接口定义可选属性
interface Cat {
	name:string;
	color:string;
	[isreaister:string]:any
}
```

### 函数声明

```
function sum(x:number,y:number):number{
	return X+Y
}
// x值定义要定义数字，y值也定义数字，括号外面后面那个number是返回值类型
```

### 类别名

给类型取另一个名字

```
type isstring = string;
let nuserName:isstring = "avc"

type isstring = string|number
type isstring = "string"|"number"|"miucc"
使用的时候只能是这样。是上面定义的值
	let eventStr:isstring="string"

```

### 枚举

```
enum Days {sun,mon,tue,wed,thu,fri,sat}
使用
	let day:Days = Days.sun
	let days:Days[] =[Days.sun,Days.mon]
```

### 属性，私有和公有

```javascript
pulic 公有  
private 私有外部访问不了，子类也访问不了
protected 只允许子类访问。子类继承父类
readonly 只读
class Animal(
	public name
)
let a = new Animal("jack")
a.name 可以访问
```



## js面向对象三大特性

#### 封装

​	将数据细节隐藏起来，只暴露对外的接口，外界调用端不需要知道细节，就能通过对外提供的接口来访问该对象，同时也保证了外界无法任意更改对象内部的数据

> 让外部无法访问内部的内容。或者是自己暴露个外部的东西。

#### 多态

​	由继承产生了相关的不同的类，对同一个方法可以有不同的响应

> 如果定义了不同类型的方法或者属性，在你不知道执行那个方法的时候，会自动自动执行那个方法

#### 继承

​	子类继承父类，子类除了拥有父类的所有特性外，还有一些更具体的特性

> 子集去继承父级的方法



