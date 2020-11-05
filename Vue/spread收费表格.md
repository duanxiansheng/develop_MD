# **spread**

### spreadjs禁止重绘

+ spread.suspendPaint();//停止重绘
+ sheet.suspendCalcSercice();  //暂停计算，
+ sheet.resumeCalcService();  //恢复计算
+ spread.resumePaint(); //恢复重绘

### 获取单元格

+ sheet.getRange(2, 3, 31, 2) （第几行，第几列，几行，几列） //-1 为全行或全列
+ sheet.getCell(0，0); （第几行，第几列） 不可以出现-1
+ ​



### 设置样式

+ setValue可以设置单元格的值
  + sheet.getCell(11,0).text('四、工种分布情况').font("bold normal 15px normal");
+ setStyle 可以设置单元格的样式
+ setFormula可以设置单元格的公式
+ setFormatter可以设置单元格的格式

#### 设置默认高度与宽度

+ sheet.defaults.rowHeight = 30;   //设置高度
+ sheet.defaults.colWidth = 120; //设置宽度

#### 设置单行或单列的高度或宽度

+ sheet.setColumnWidth(8, 30);
+ sheet.setRowHeight(8, 75);

#### 设置背景颜色

+ sheet.getRange(0, 0, 31, 11).backColor("rgb(236,233,216)");
+ sheet.getRange(2, 3, 31, 2).backColor("White");

### 设置几行几列

+ sheet.setRowCount(20);
+ sheet.setColumnCount(5);

### 合并单元格

+ sheet.addSpan(0,1,1,2) （第几行，第几列，几行，几列）
+ ​

### 禁止用户缩放单元格

> spread.options.allowUserZoom = false;

### 设置滚动条

+ spread.options.scrollbarMaxAlign = true; //设置滚动条显示到最后一列即可
+ spread.options.scrollbarShowMax = true;

#### 隐藏滚动条

+ spread.options.showHorizontalScrollbar = false; //隐藏横向滚动条
+ spread.options.showVerticalScrollbar = false; //纵向滚动条

### 单元格禁止编辑

> 单元格编辑是把单元格中的 locked 和 protected 设置为true就可以把单元格禁止编辑，而单元格的locked默认为true

+ sheet.options.isProtected = true; //禁止所有单元格编辑
+ sheet.getRange(2, 3, 23, 1).locked(false); //将locked设置为false就可以进行编辑


### 绑定数据

1.  var source = new GC.Spread.Sheets.Bindings.CellBindingSource(this.spreadData); //设置要绑定的对象
2.  sheet.setBindingPath(23, 3, "obj.M1001_NAME");
3.  sheet.setDataSource(source); //将值设置上才可以显示

### 设置行头与列头

+ sheet.setRowVisible(0, false, GC.Spread.Sheets.SheetArea.colHeader); //隐藏行头
+ sheet.setColumnVisible(0, false, GC.Spread.Sheets.SheetArea.rowHeader); //隐藏列头


### 禁止单元格拖拽

+ spread.canUserDragDrop(false); //禁止拖动移动
+ spread.canUserDragFill(false); //禁止拖动填充

### 设置单元格边框

> sheet.getRange(0, 0, 31, 11).setBorder(new GC.Spread.Sheets.LineBorder("black",GC.Spread.Sheets.LineStyle.thin),{ all: true }, 1);

### 禁止单元格拖动

+ spread.options.allowUserDragDrop = false;

### 设置右击菜单为空

+ spread.contextMenu.menuData = [];

+ ```
  let Query = {
          text: "查询条件",
          name: "query",
          command: "markWithRedBg",
          workArea: "viewport"
        };
        let comments = {
          text: "批注",
          name: "comments",
          workArea: "viewport",
          subMenu: [
            {
              text: "新建批注",
              name: "comments.ins",
              workArea: "viewport"
            },
            {
              text: "修改批注",
              name: "comments.edit",
              workArea: "viewport"
            },
            {
              text: "删除批注",
              name: "comments.del",
              workArea: "viewport"
            },
            {
              text: "显示所有批注",
              name: "comments.sel",
              workArea: "viewport"
            }
          ]
        };
        spread.contextMenu.menuData.push(Query); 
        spread.contextMenu.menuData.push(comments);

  ```



