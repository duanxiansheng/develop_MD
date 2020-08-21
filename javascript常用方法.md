# 获取当前时间

```
    getTime() {
      var myDate = new Date();
      var Y = myDate.getFullYear();
      var M = myDate.getMonth() + 1;
      M = M < 10 ? "0" + M : M;
      var D = myDate.getDate();
      D = D < 10 ? "0" + D : D;
      var h = myDate.getHours();
      h = h < 10 ? "0" + h : h;
      var m = myDate.getMinutes();
      m = m < 10 ? "0" + m : m;
      var s = myDate.getSeconds();
      s = s < 10 ? "0" + s : s;
      var time = Y + "-" + M + "-" + D + " " + h + ":" + m + ":" + s;
      return time;
    },
```

# 递归渲染数控

```
 // 树控渲染
	this.totree(res,0)
    toTree(data, PID) {
      let result = [];
      if (!Array.isArray(data)) {
        return result;
      }
      data.forEach((ele, index) => {
        if (ele.M0004_PID == PID) {
          if (
            data.findIndex(
              element =>
                element.M0004_PID == ele.M0004_ID 
            ) != -1
          ) {
            ele.children = this.toTree(data, ele.M0004_ID);
          }
          result.push(ele);
        }
      });
      return result;
    },
```



