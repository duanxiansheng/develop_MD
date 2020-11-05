### 介绍

Vuex 是一个专为 Vue.js 应用程序开发的**状态管理模式**。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。

### 使用

**分为五个部分。**

##### state 定义数据-单一状态树

```
state:{
        userName:"张三"
},
// 页面中使用
{{$store.state.模块变量.数据名}} 
{{this.$store.state.模块变量.数据名 }}
```

##### mutations 创建函数-触发同步事件

```
mutations:{
	setUserName:(state,data)=>{
		console.log(state,data)
	}
},
// 使用
this.$store.commit('方法名'，值)
this.$store.commit('setUsername'，123)
```

##### actions定义页面刷新后执行函数-提交mutation，可以包含异步操作

```
actions:{
        setUsername:({commit},data)=>{
            commit('setUserName',data)
        }
    }
//使用
this.$store.dispatch('异步定义的方法', 传参)
this.$store.dispatch("setUsername",1234)
```

##### getters计算属性-状态获取

```
const getters ={
    test:(data)=>{
      var a=  data.user.userName+"哎呦啊123"
        return a
    }
}
//使用
this.$store.getters.test
```

##### modules模块化，让每个模块都有自己的方法，方便管理

```
import Vue from 'vue'
import Vuex from 'vuex'
import getters from './getters'
import user from  "./modules/user"
Vue.use(Vuex)

export default new Vuex.Store({
  modules: {
    user
  },
  getters
})
```

### 补充

1. vuex 异步同步
   action:用于提交mutation改变数据.会默认自身封装一个paromise.包含异步。mutations:提交commit改变数据.只是一个单纯的函数。尽量不要使用异步，异步导致变量不能被追踪，也就是说action中的函数调用mutations中的函数，进行异步操作state中的数据

2. 

   

1. 