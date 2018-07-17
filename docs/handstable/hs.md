# HandsonTable简介
  一款用JS编写的在线电子表格插件
## 核心
  主要由配置项(options)，方法(method)以及事件(hooks)和插件(plugins)组成
### 配置项
  基本语法
  
    const container = document.getElementById('example');
    const hot = new Handsontable(container, {
       data: myArray,
       width: 400,
       height: 300
     });
===================================================================
* activeHeaderClassNameString:String  
  配置选中左侧或上侧表头时css类名,默认为:<code>ht__active_highlight</code>
* allowEmpty:Boolean  
  配置列是否允许为空(null,undefined or '')

        allowEmpty: true,
         columns: [
           {
             data: 'date',
             dateFormat: 'DD/MM/YYYY',
             // allow empty values only for the 'date' column
             allowEmpty: true
           }
         ]
* allowHtml:Boolean  
  配置是否允许html文本 
  
         columns: [{
            type: 'autocomplete',
             allowHtml: true,
             source: ['<strong>foo</strong>', '<strong>bar</strong>']
         }]
* allowInsertColumn:Boolean  
  是否允许插入列
* allowInsertRow:Boolean  
  是否允许插入行
* allowInvalid:Boolean  
  是否允许不合法单元格
* allowRemoveColumn:Boolean  
  是否允许删除列
* allowRmoveRow:Boolean  
  是否允许删除行
* autoColumnSize:Boolean  
  列宽自动
* autoRowSize:Boolean  
  行宽自动
* autoWrapCol:Boolean  
  在最后一个单元格使用enter键是否跳到第一个单元格
* autoWrapRow:Boolean  
  在最后一个单元格使用enter键是否跳到第一个单元格
* cell:Array<array>  
  传入一个单元格数组
* cells:function(row,column,prop)  
  配置单元格属性

        cells: function(row, column, prop) {
            const cellProperties = {};
            const visualRowIndex = this.instance.toVisualRow(row);
            const visualColIndex = this.instance.toVisualColumn(column);
            if (visualRowIndex === 0 && visualColIndex === 0) {
              cellProperties.readOnly = true;
            }
            return cellProperties;
        }  
* className:String Array<String>  
  table的样式
  
      className: 'your__class--name',
      // or
      className: ['first-class-name', 'second-class-name'],
  
* colHeaders:Boolean Array.<String> function  
    表格列头设置
    
        // as a boolean
        colHeaders: true,
        
        // as an array
        colHeaders: ['A', 'B', 'C'],
        
        // as a function
        colHeaders: function(index) {
          return index + ': AB';
        }
* columnHeaderHeight:Number Array.<Number>  
   表格列头高度
   
       // set shared height for all headers
       columnHeaderHeight: 35,
       
       // or
       // set height for each header individually
       columnHeaderHeight: [35, 20, 55],
       
       // or
       // skipped headers will fallback to default value
       columnHeaderHeight: [35, undefined, 55]