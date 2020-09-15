- cookie

- - 安装 npm install vue-cookies --save

  - - yarn add vue-cookies

  - 引入

  - - import Vue from 'vue' import VueCookies from 'vue-cookies' Vue.use(VueCookies)

  - 设置和获取

  - - this.$cookies.set("user_session","25j_7Sl6xDq2Kc3ym0fmrSSk2xV2XkUkX","6s") #6秒过期
    - this.$cookies.set("user_session","25j_7Sl6xDq2Kc3ym0fmrSSk2xV2XkUkX","1d")  #1d 为一天
    - this.$cookies.set("default_unit_second","input_value","0");//浏览器会话结束时过期
    - this.$cookies.set("default_unit_second","input_value",-1); //永不过期
    - this.$cookies.get("token")  #获取
    - this.$cookies.keys() 获取所有 cookie name
    - this.$cookies.remove(keyName [, path [, domain]]) 删除