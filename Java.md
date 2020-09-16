# markdown使用说明

## 标题

ctrl 加 1~6   #6最小

## 斜体 粗体

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

# JAVA

## 计算机基础

> 系统软件：DOS简称CMD ，windows，linux，Unix，mac，ios，android
>
> 应用软件：QQ 浏览器 等
>
> $\color{rgb(0,0,0)}{有了系统软件的支撑，在能使用应用软件}$

## DOS系统简单的命令

> ipconfig查询ip 、 cls 清屏、 exit退出、 c:/d: 切换盘服

## Java跨平台

> #### 什么是跨平台性？
>
>  通过java语言编写的应用程序在不同的系统平台上都可以运行
>
> **java是跨平台的，jvm不是跨平台的**
>
>  jvm有不同版本的，比如安卓苹果windows、linux等，JVM(相当于一个桥梁)对Java语言进行编译和运行
>
> #### 原理是什么？
>
>  只要在需要安装java应用程序的操作系统上，先安装一个java虚拟机(JVM)即可,由JVM来负责JAVA程序在该系统中的运行
>
> ###### 总结：因为有了JVM，所以同一个java程序在三个不同的操作系统中都可以执行。这样就实现了java程序的跨平台性。也称为java具有良好的可移植性

## JRK与JDK

> **JVM保证java语言跨平台**
>
> ###### JRE（java Runtime Environment JAVA运行环境）
>
> 包括java虚拟机jvm和java程序所需的核心类库等，如果想运行一个开发好的java程序，计算机中只需要安装JRE即可
>
> ##### JDK(java Development Kit java 开发工具包)
>
> JDK是提供开发人员使用，包含java开发工具、也包括JRE，所以安装了JDK，就不用在单独安装JRE了

## JAVA下载与安装

> 针对不同操作系统，下载不同版本的JDK，安装路径写英文
>
> https://www.oracle.com/cn/downloads/ 下载网站

## Hollew Worled

> 1. 新建一个java为后缀名的文件
>
>    ```
>    class 名称 {
>      public static void main(String[] args){
>        System.out.println("content");
>      }
>    }
>    java程序的最基本单位是类，所以我们要定义一个类。
>    	格式 class 类名 举例 class helloworld
>    在类中写内容，要用大括号括起来
>    java程序要想执行，必须有main方法
>    	格式：public static void main(string[] args)
>    严格区分大小写
>    	
>    ```
>
> 2. 使用dos系统输入 javac +空格 + 文件名为java后缀的文件 生成class后缀文件
>
> 3. 如果没报错，使用 java 文件名.不需要加后缀class

## JAVA环境变量配置

1. 创建新的变量名称 JAVA_HOME 值为JDK安装目录(有bin文件夹的目录) D:\install\java
2. 在path中新建编辑 %JAVA_HOME%\bin %java_home%是选中变量的意思
3. classpath环境变量
   1. 名为 classpath。值为classpath文件的目录，多个目录间用分号(;)分割。class文件
   2. 作用：使classpath目录中的，class文件可以在任意目录运行
   3. 技巧：通常将配置的目录最前面添加，配置，即便当前目录，使class文件

> path是以exe为结尾的环境配置，
>
> classpath环境变量里记录的是java类的运行文件所在目录

## 标识符概述

1. 就是给类，接口，方法，变量等起名时使用的字符序列
2. 组成规则
   1. 英文字母大小写
   2. 数字和字符
   3. $和_
3. 注意事项：
   1. 不能以数字开头
   2. 不能是java关键字
   3. java严格区分大小写
4. 包：其实就是文件夹，用于吧相同的类名进行区分 
   + 全部小写 
     + 单级 :liuyi 多级: cn.itcast 
   + 类或者接口: 
     + 一个单词：单词的首字母必须大写 
       + 举例:student,Dog 多
     + 个单词：每个单词的首字母必须大写 
       + 举例：HelloWorld，StudentName 
   + 方法或者变量 
     + 一个单词:单词的首字母小写 
       + 举例:main,age 
     + 多个单词：
       + 从第二个单词开始，每个单词的首字母大写 
       + 举例：HelloWord,StudentName
5. 常量
   + 一个单词:全部大写
     + 举例:PI
   + 多个单词：每个字母都大写，用_隔开
     + 举例：STUDENT_MAX_AGE

## 注释概述

+ 注释

  + 单行注释 //

  + 多行注释 /* */ 

    + 多行注释不能嵌套，单行可以

  + 文档注释

    + ```
      /***注释***/
      ```

+ 作用：写文档，查找出错代码

## 常量

在程序执行过程中，其值不发生改变的量

+ 字面值常量 用上引号括起来的内容
  + 举例："hello","world","HelloWorld"
+ 整数常量  所有的整数
+ 小数常量 所有的小数
  + 10.22
+ 字符常量 用单引号括起来的内容
  + 'a','A'
+ 布尔常量 
  + true false
+ 空常量
  + null

## 进制

进位方式，X进制，表示逢X进1