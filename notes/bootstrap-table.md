### 入门

```html
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Hello, Bootstrap Table!</title>

    <link rel="stylesheet" href="./table/bootstrap.min.css" integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS" crossorigin="anonymous">
    <!-- <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.6.3/css/all.css" integrity="sha384-UHRtZLI+pbxtHCWp1t77Bi1L4ZtiqrqD80Kn4Z8NTSRyMA2Fd33n5dQ8lWUE00s/" crossorigin="anonymous"> -->
    <link rel="stylesheet" href="./table/bootstrap-table.min.css">
  </head>
  <body>
    <table data-toggle="table">
      <thead>
        <tr>
          <th>Item ID</th>
          <th>Item Name</th>
          <th>Item Price</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>Item 1</td>
          <td>$1</td>
        </tr>
        <tr>
          <td>2</td>
          <td>Item 2</td>
          <td>$2</td>
        </tr>
      </tbody>
    </table>
	
	<table data-toggle="table" data-url="./data.json"
	  data-pagination="true"
	  data-search="true" >
		<!-- 缺少<thead> -->
		<thead>
			<th data-sortable="true" data-field="id">ID</th>
			<th data-field="name">姓名</th>
			<th data-field="price">余额</th>
		</thead>
	</table>
	
	<table id="table">
		<caption id="toolBar"></caption>
	</table>
	

    <script src="js/jquery-3.3.1.min.js" integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>
    <script src="./table/popper.min.js" integrity="sha384-wHAiFfRlMFy6i5SRaxvfOCifBUQy1xHdJ/yoi7FRNXMRBu5WHdZYu1hA6ZOblgut" crossorigin="anonymous"></script>
    <script src="./table/bootstrap.min.js" integrity="sha384-B0UglyR+jN6CkvvICOB2joaf5I4l3gm9GU6Hc1og6Ls7i6U/mkkaduKaBhlAXv9k" crossorigin="anonymous"></script>
    <script src="./table/bootstrap-table.min.js"></script>
  </body>
  
  
  <script>
	  $('#table').bootstrapTable({
	    columns: [{
	      field: 'id',
	      title: 'Item ID'
	    }, {
	      field: 'name',
	      title: 'Item Name'
	    }, {
	      field: 'price',
	      title: 'Item Price'
	    }],
	    data: [{
	      id: 1,
	      name: 'Item 1',
	      price: '$1'
	    }, {
	      id: 2,
	      name: 'Item 2',
	      price: '$2'
	    }],
		toolBar:'#toolBar'
		/* url: 'data.json', */
	  })
  </script>
</html>
```


```json
//data.json
[
{"id":1,"name":"zs","price":20.25},
{"id":2,"name":"dd","price":11.25},
{"id":3,"name":"rrd","price":24.25},
{"id":4,"name":"ewd","price":88.25}
]
```

### 

### 列表选项

## -

- **属性:**`data-toggle`

- **类型:**`String`

- **详情:**

  无需编写JavaScript即可激活引导表。

- **默认:**`'table'`

- **例子:**[From HTML](https://www.bootstrap-table.com.cn/examples/welcome/from-html/)

## height

- **属性:**`data-height`

- **类型:**`Number`

- **详情:**

  表的高度，启用表的固定标题。

- **默认:**`undefined`

- **例子:**[Table Height](https://www.bootstrap-table.com.cn/examples/options/table-height/)

## classes

- **属性:**`data-classes`

- **类型:**`String`

- **详情:**

  表的类名。`'table'`, `'table-bordered'`, `'table-hover'`, `'table-striped'`, `'table-dark'`, `'table-sm'` 和 `'table-borderless'` 可被使用。默认情况下，表格是有界的。

- **默认:**`'table table-bordered table-hover'`

- **例子:**[Table Classes](https://www.bootstrap-table.com.cn/examples/options/table-classes/)

## theadClasses

- **属性:**`data-thead-classes`

- **类型:**`String`

- **详情:**

  表thead的类名。Bootstrap v4，使用修饰符类`.thead-light` 或 `.thead-dark` 使用 `thead` 显示为浅灰色或深灰色。

- **默认:**`''`

- **例子:**[Thead Classes](https://www.bootstrap-table.com.cn/examples/options/thead-classes/)

## headerStyle

- **属性:**`data-header-style`

- **类型:**`Function`

- **详情:**

  标头样式格式化程序函数采用一个参数：

  - `column`: 列对象。

  支持 `classes` 或 `css`。用法示例：

```
  functionheaderStyle(column){
    return{
      css:{'font-weight':'normal'},
      classes:'my-class'
    }
  }
  
```

- **默认:**`{}`
- **例子:**[Header Style](https://www.bootstrap-table.com.cn/examples/options/header-style/)

## rowStyle

- **属性:**`data-row-style`

- **类型:**`Function`

- **详情:**

  行样式格式化程序函数具有两个参数：

  - `row`: 行记录数据。
  - `index`: 行索引。

  支持类或CSS。

- **默认:**`{}`

- **例子:**[Row Style](https://www.bootstrap-table.com.cn/examples/options/row-style/)

## rowAttributes

- **属性:**`data-row-attributes`

- **类型:**`Function`

- **详情:**

  行属性格式化程序函数具有两个参数：

  - `row`: 行记录数据。
  - `index`: 行索引。

  支持所有自定义属性。

- **默认:**`{}`

- **例子:**[Row Attributes](https://www.bootstrap-table.com.cn/examples/options/row-attributes/)

## undefinedText

- **属性:**`data-undefined-text`

- **类型:**`String`

- **详情:**

  定义默认`undefined` 文本。

- **默认:**`'-'`

- **例子:**[Undefined Text](https://www.bootstrap-table.com.cn/examples/options/undefined-text/)

## locale

- **属性:**`data-locale`

- **类型:**`String`

- **详情:**

  设置要使用的语言环境（即`'zh-CN'`）。区域设置文件必须预先加载。如果加载了后备语言环境，则按以下顺序进行：

  - 首先尝试指定的语言环境，
  - 然后尝试将'_'转换为'-'并将区域代码大写的语言环境，
  - 然后尝试使用简短的语言环境代码（即`'zh'` 代替 `'zh-CN'`),
  - 最后，将使用最后一个加载的语言环境文件（如果未加载语言环境，则使用默认语言环境）。

  如果为左`undefined`字符串或为空字符串，则使用上次加载的语言环境（或`'en-US'`如果未加载任何语言环境文件）。

- **默认:**`undefined`

- **例子:**[Table Locale](https://www.bootstrap-table.com.cn/examples/options/table-locale/)

## virtualScroll

- **属性:**`data-virtual-scroll`

- **类型:**`Boolean`

- **详情:**

  设置 `true` 为启用虚拟滚动以显示虚拟的 “infinite” 列表。

- **默认:**`false`

- **例子:**[Large Data](https://www.bootstrap-table.com.cn/examples/options/large-data/)

## virtualScrollItemHeight

- **属性:**`data-virtual-scroll-item-height`

- **类型:**`Number`

- **详情:**

  如果未定义此选项，则默认情况下我们将使用第一项的高度。

  如果虚拟商品的高度将明显大于默认高度，则提供此功能非常重要。此维度用于帮助确定初始化时应创建多少个单元格，并帮助计算可滚动区域的高度。此高度值只能使用`px`单位。

- **默认:**`undefined`

- **例子:**[Virtual Scroll Item Height](https://www.bootstrap-table.com.cn/examples/options/virtual-scroll-item-height/)

## sortable

- **属性:**`data-sortable`

- **类型:**`Boolean`

- **详情:**

  设置 `false`为禁用所有列的可排序。

- **默认:**`true`

- **例子:**[Table Sortable](https://www.bootstrap-table.com.cn/examples/options/table-sortable/)

## sortClass

- **属性:**`data-sort-class`

- **类型:**`String`

- **详情:**

  `td` 排序的元素的类名称。

- **默认:**`undefined`

- **例子:**[Sort Class](https://www.bootstrap-table.com.cn/examples/options/sort-class/)

## silentSort

- **属性:**`data-silent-sort`

- **类型:**`Boolean`

- **详情:**

  设置`false` 为使用加载消息对数据进行排序。当sidePagination选项设置为时，此选项有效 `'server'`.

- **默认:**`true`

- **例子:**[Silent Sort](https://www.bootstrap-table.com.cn/examples/options/silent-sort/)

## sortName

- **属性:**`data-sort-name`

- **类型:**`String`

- **详情:**

  定义要排序的列。

- **默认:**`undefined`

- **例子:**[Sort Name Order](https://www.bootstrap-table.com.cn/examples/options/sort-name-order/)

## sortOrder

- **属性:**`data-sort-order`

- **类型:**`String`

- **详情:**

  定义列的排序顺序，只能是`'asc'` 或 `'desc'`.

- **默认:**`'asc'`

- **例子:**[Sort Name Order](https://www.bootstrap-table.com.cn/examples/options/sort-name-order/)

## sortStable

- **属性:**`data-sort-stable`

- **类型:**`Boolean`

- **详情:**

  设置 `true`以获得稳定的排序。我们将`'_position'` 属性添加到该行。

- **默认:**`false`

- **例子:**[Sort Stable](https://www.bootstrap-table.com.cn/examples/options/sort-stable/)

## rememberOrder

- **属性:**`data-remember-order`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为记住每列的顺序。

- **默认:**`false`

- **例子:**[Remember Order](https://www.bootstrap-table.com.cn/examples/options/remember-order/)

## serverSort

- **属性:**`data-server-sort`

- **类型:**`Boolean`

- **详情:**

  设置`false`为在客户端对数据进行排序，仅在`sidePagination` 时为 `server`时有效

- **默认:**`true`

- **例子:**[Server Sort](https://www.bootstrap-table.com.cn/examples/options/server-sort/)

## customSort

- **属性:**`data-custom-sort`

- **类型:**`Function`

- **详情:**

  执行自定义排序功能而不是内置的排序功能，它需要三个参数：

  - `sortName`: 排序名称。
  - `sortOrder`: 排序顺序。
  - `data`: 行数据。

- **默认:**`undefined`

- **例子:**[Custom Order](https://www.bootstrap-table.com.cn/examples/options/custom-order/)

## columns

- **属性:**`-`

- **类型:**`Array`

- **详情:**

  表列配置对象，请参阅列属性以获取更多详细信息。

- **默认:**`[]`

- **例子:**[Table Columns](https://www.bootstrap-table.com.cn/examples/options/table-columns/)

## data

- **属性:**`data-data`

- **类型:**`Array | Object`

- **详情:**

  要加载的数据。

- **默认:**`[]`

- **例子:**[From Data](https://www.bootstrap-table.com.cn/examples/welcome/from-data/)

## url

- **属性:**`data-url`

- **类型:**`String`

- **详情:**

  一个从远程站点请求数据的URL。

  请注意，所需的服务器响应格式取决于是否`'sidePagination'` 指定了该选项。请参阅以下示例：

  - [Without server-side pagination](https://github.com/wenzhixin/bootstrap-table-examples/blob/master/json/data1.json)
  - [With server-side pagination](https://github.com/wenzhixin/bootstrap-table-examples/blob/master/json/data2.json)

- **默认:**`undefined`

- **例子:**[From URL](https://www.bootstrap-table.com.cn/examples/welcome/from-url/)

- **错误处理**

  要获取加载错误，请使用[onLoadError](https://www.bootstrap-table.com.cn/doc/api/events/#onloaderror)

## method

- **属性:**`data-method`

- **类型:**`String`

- **详情:**

  请求远程数据的方法类型。

- **默认:**`'get'`

- **例子:**[Table Method](https://www.bootstrap-table.com.cn/examples/options/table-method/)

## cache

- **属性:**`data-cache`

- **类型:**`Boolean`

- **详情:**

  设置`false`为禁用AJAX请求的缓存。

- **默认:**`true`

- **例子:**[Table Cache](https://www.bootstrap-table.com.cn/examples/options/table-cache/)

## contentType

- **属性:**`data-content-type`

- **类型:**`String`

- **详情:**

  请求远程数据的contentType，例如：`application/x-www-form-urlencoded`.

- **默认:**`'application/json'`

- **例子:**[Content Type](https://www.bootstrap-table.com.cn/examples/options/content-type/)

## dataType

- **属性:**`data-data-type`

- **类型:**`String`

- **详情:**

  您期望从服务器返回的数据类型。

- **默认:**`'json'`

- **例子:**[Data Type](https://www.bootstrap-table.com.cn/examples/options/data-type/)

## ajax

- **属性:**`data-ajax`

- **类型:**`Function`

- **详情:**

  一种替换ajax调用的方法。应该实现与jQuery ajax方法相同的API。

- **默认:**`undefined`

- **例子:**[Table AJAX](https://www.bootstrap-table.com.cn/examples/options/table-ajax/)

## ajaxOptions

- **属性:**`data-ajax-options`

- **类型:**`Object`

- **详情:**

  提交ajax请求的其他选项。值列表：[jQuery.ajax](http://api.jquery.com/jQuery.ajax).

- **默认:**`{}`

- **例子:**[AJAX Options](https://www.bootstrap-table.com.cn/examples/options/ajax-options/)

## queryParams

- **属性:**`data-query-params`

- **类型:**`Function`

- **详情:**

  请求远程数据时，可以通过修改queryParams发送其他参数。

  如果 `queryParamsType = 'limit'`，params对象包含：`limit`, `offset`, `search`, `sort`, `order`.

  否则，它包含：`pageSize`, `pageNumber`, `searchText`, `sortName`, `sortOrder`.

  返回 `false`停止请求。

- **默认:**`function(params) { return params }`

- **例子:**[Query Params](https://www.bootstrap-table.com.cn/examples/options/query-params/)

## queryParamsType

- **属性:**`data-query-params-type`

- **类型:**`String`

- **详情:**

  设置`'limit'`为发送具有RESTFul类型的查询参数。

- **默认:**`'limit'`

- **例子:**[Query Params Type](https://www.bootstrap-table.com.cn/examples/options/query-params-type/)

## responseHandler

- **属性:**`data-response-handler`

- **类型:**`Function`

- **详情:**

  在加载远程数据之前，处理响应数据格式，参数对象包含：

  - `res`: 响应数据。
  - `jqXHR`: jqXHR对象，它是XMLHTTPRequest对象的超集。有关更多信息，请参见 [jqXHR 类](http://api.jquery.com/Types/#jqXHR).

- **默认:**`function(res) { return res }`

- **例子:**[Response Handler](https://www.bootstrap-table.com.cn/examples/options/response-handler/)

## totalField

- **属性:**`data-total-field`

- **类型:**`String`

- **详情:**

  键入包含`'total'`数据的传入json 。

- **默认:**`'total'`

- **例子:**[Total/Data Field](https://www.bootstrap-table.com.cn/examples/options/total-data-field/)

## totalNotFilteredField

- **属性:**`data-total-not-filtered-field`

- **类型:**`string`

- **详情:**

  json响应中的字段，将用于 `showExtendedPagination`.

- **默认:**`totalNotFiltered`

- **例子:**[Total Not Filtered Field](https://www.bootstrap-table.com.cn/examples/options/total-not-filtered-field/)

## dataField

- **属性:**`data-data-field`

- **类型:**`String`

- **详情:**

  键入包含`'rows'`数据列表的传入json 。

- **默认:**`'rows'`

- **例子:**[Total/Data Field](https://www.bootstrap-table.com.cn/examples/options/total-data-field/)

## pagination

- **属性:**`data-pagination`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为在表格底部显示分页工具栏。

- **默认:**`false`

- **例子:**[Table Pagination](https://www.bootstrap-table.com.cn/examples/options/table-pagination/)

## onlyInfoPagination

- **属性:**`data-only-info-pagination`

- **类型:**`Boolean`

- **详情:**

  设置`true`为仅显示表中显示的数据量。它需要将分页表选项设置为true。

- **默认:**`false`

- **例子:**[Only Info Pagination](https://www.bootstrap-table.com.cn/examples/options/only-info-pagination/)

## showExtendedPagination

- **属性:**`data-show-extended-pagination`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为显示分页的扩展版本（包括不带过滤器的所有行的计数）。如果在服务器端使用分页，请使用`totalNotFilteredField`来定义计数。

- **默认:**`false`

- **例子:**[Show Extended Pagination](https://www.bootstrap-table.com.cn/examples/options/show-extended-pagination/)

## paginationLoop

- **属性:**`data-pagination-loop`

- **类型:**`Boolean`

- **详情:**

  设置`true`为启用分页连续循环模式。

- **默认:**`true`

- **例子:**[Pagination Loop](https://www.bootstrap-table.com.cn/examples/options/pagination-loop/)

## sidePagination

- **属性:**`data-side-pagination`

- **类型:**`String`

- **详情:**

  定义表格的侧面分页，只能是`'client'` 或 `'server'`。使用 `'server'`side需要设置`'url'` 或 `'ajax'` 选项。

  请注意，根据 `'sidePagination'` 选项设置为 `'client'` 还是，所需的服务器响应格式会有所不同 `'server'`。请参阅以下示例：

  - [没有服务器端分页](https://github.com/wenzhixin/bootstrap-table-examples/blob/master/json/data1.json)
  - [使用服务器端分页](https://github.com/wenzhixin/bootstrap-table-examples/blob/master/json/data2.json)

- **默认:**`'client'`

- **例子:**[Client Side Pagination](https://www.bootstrap-table.com.cn/examples/options/client-side-pagination/) and [Server Side Pagination](https://www.bootstrap-table.com.cn/examples/options/server-side-pagination/)

## totalRows

- **属性:**`data-total-rows`

- **类型:**`Number`

- **详情:**

  此属性主要由分页服务器传入，该服务器易于使用。

- **默认:**`0`

## totalNotFiltered

- **属性:**`data-total-not-filtered`

- **类型:**`Number`

- **详情:**

  此属性主要由分页服务器传入，该服务器易于使用。

- **默认:**`0`

## pageNumber

- **属性:**`data-page-number`

- **类型:**`Number`

- **详情:**

  设置分页属性时，请初始化页码。

- **默认:**`1`

- **例子:**[Page Number](https://www.bootstrap-table.com.cn/examples/options/page-number/)

## pageSize

- **属性:**`data-page-size`

- **类型:**`Number`

- **详情:**

  设置分页属性时，初始化页面大小。

- **默认:**`10`

- **例子:**[Page Size](https://www.bootstrap-table.com.cn/examples/options/page-size/)

## pageList

- **属性:**`data-page-list`

- **类型:**`Array`

- **详情:**

  设置分页属性时，初始化页面尺寸选择列表。如果包含`'all'` 或 `'unlimited'` 选项，则所有记录将显示在表中。

- **默认:**`[10, 25, 50, 100]`

- **例子:**[Page List](https://www.bootstrap-table.com.cn/examples/options/page-list/)

## paginationHAlign

- **属性:**`data-pagination-h-align`

- **类型:**`String`

- **详情:**

  指示如何对齐分页。`'left'`, `'right'` 可以使用。

- **默认:**`'right'`

- **例子:**[Pagination H Align](https://www.bootstrap-table.com.cn/examples/options/pagination-h-align/)

## paginationVAlign

- **属性:**`data-pagination-v-align`

- **类型:**`String`

- **详情:**

  指示如何垂直对齐分页。`'top'`, `'bottom'`, `'both'`（穿上顶部和底部的分页）都可以使用。

- **默认:**`'bottom'`

- **例子:**[Pagination V Align](https://www.bootstrap-table.com.cn/examples/options/pagination-v-align/)

## paginationDetailHAlign

- **属性:**`data-pagination-detail-h-align`

- **类型:**`String`

- **详情:**

  指示如何对齐分页细节 `'left'`, `'right'` 可以使用。

- **默认:**`'left'`

- **例子:**[Pagination H Align](https://www.bootstrap-table.com.cn/examples/options/pagination-h-align/)

## paginationPreText

- **属性:**`data-pagination-pre-text`

- **类型:**`String`

- **详情:**

  指示要在分页详细信息中显示的图标或文本，即上一个按钮。

- **默认:**`'‹'`

- **例子:**[Pagination Text](https://www.bootstrap-table.com.cn/examples/options/pagination-text/)

## paginationNextText

- **属性:**`data-pagination-next-text`

- **类型:**`String`

- **详情:**

  指示要在分页详细信息（下一步按钮）中显示的图标或文本。

- **默认:**`'›'`

- **例子:**[Pagination Text](https://www.bootstrap-table.com.cn/examples/options/pagination-text/)

## paginationSuccessivelySize

- **属性:**`data-pagination-successively-size`

- **类型:**`Number`

- **详情:**

  连续的最大连续页数。

- **默认:**`5`

- **例子:**[Pagination Index Number](https://www.bootstrap-table.com.cn/examples/options/pagination-index-number/)

## paginationPagesBySide

- **属性:**`data-pagination-pages-by-side`

- **类型:**`Number`

- **详情:**

  当前页面每侧（右侧，左侧）的页数。

- **默认:**`1`

- **例子:**[Pagination Index Number](https://www.bootstrap-table.com.cn/examples/options/pagination-index-number/)

## paginationUseIntermediate

- **属性:**`data-pagination-use-intermediate`

- **类型:**`Boolean`

- **详情:**

  计算并显示中间页面以便快速访问。

- **默认:**`false`

- **例子:**[Pagination Index Number](https://www.bootstrap-table.com.cn/examples/options/pagination-index-number/)

## search

- **属性:**`data-search`

- **类型:**`Boolean`

- **详情:**

  启用搜索输入。

  有3种搜索方式：

  - 该值包含搜索查询（默认）。示例：Github包含git。
  - 该值必须与搜索查询相同。示例：Github（值）和Github（搜索查询）。
  - 比较（<, >, <=, =<, >=, =>）。示例：4大于3。

- **默认:**`false`

- **例子:**[Table Search](https://www.bootstrap-table.com.cn/examples/options/table-search/)

## searchOnEnterKey

- **属性:**`data-search-on-enter-key`

- **类型:**`Boolean`

- **详情:**

  搜索方法将一直执行到按下Enter键。

- **默认:**`false`

- **例子:**[Search On Enter Key](https://www.bootstrap-table.com.cn/examples/options/search-on-enter-key/)

## strictSearch

- **属性:**`data-strict-search`

- **类型:**`Boolean`

- **详情:**

  启用严格搜索。禁用比较检查。

- **默认:**`false`

- **例子:**[Strict Search](https://www.bootstrap-table.com.cn/examples/options/strict-search/)

## visibleSearch

- **属性:**`visible-search`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为仅在可见列/数据中搜索，如果数据包含其他未显示的值，则在搜索时将忽略它们。

- **默认:**`false`

- **例子:**[visible search](https://www.bootstrap-table.com.cn/examples/options/visible-search/)

## showButtonIcons

- **属性:**`show-button-icons`

- **类型:**`Boolean`

- **详情:**

  所有按钮都将在其上显示图标

- **默认:**`true`

## showButtonText

- **属性:**`show-button-text`

- **类型:**`Boolean`

- **详情:**

  所有按钮都将在其上显示文本

- **默认:**`false`

## showSearchButton

- **属性:**`data-show-search-button`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为在搜索输入后面显示搜索按钮。仅在按下按钮时才会执行搜索（例如，以防止交通或加载时间）。

- **默认:**`false`

## showSearchClearButton

- **属性:**`data-show-search-clear-button`

- **类型:**`Boolean`

- **详情:**

  设置`true`为在搜索输入后面显示一个清除按钮，该按钮将清除搜索输入（还包括来自过滤器控件的所有过滤器（如果启用））。

- **默认:**`false`

## trimOnSearch

- **属性:**`data-trim-on-search`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为修剪搜索字段中的空格。

- **默认:**`true`

## searchAlign

- **属性:**`data-search-align`

- **类型:**`String`

- **详情:**

  指示如何对齐搜索输入。`'left'`, `'right'` 可以使用。

- **默认:**`'right'`

## searchTimeOut

- **属性:**`data-search-time-out`

- **类型:**`Number`

- **详情:**

  设置搜索触发超时。

- **默认:**`500`

## searchText

- **属性:**`data-search-text`

- **类型:**`String`

- **详情:**

  设置搜索属性后，初始化搜索文本。

- **默认:**`''`

## customSearch

- **属性:**`data-custom-search`

- **类型:**`Function`

- **详情:**

  执行自定义搜索功能而不是内置搜索功能，它采用三个参数：

  - `data`: 表格数据。
  - `text`: 搜索文字。
  - `filter`: `filterBy` 方法中的过滤器对象。

  用法示例：

```
  functioncustomSearch(data,text){
    returndata.filter(function(row){
      returnrow.field.indexOf(text)>-1
    })
  }
  
```

- **默认:**`undefined`

## showHeader

- **属性:**`data-show-header`

- **类型:**`Boolean`

- **详情:**

  设置`false` 为隐藏表格标题。

- **默认:**`true`



## showFooter

- **属性:**`data-show-footer`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为显示摘要页脚行。

- **默认:**`false`

## footerStyle

- **属性:**`data-footer-style`

- **类型:**`Function`

- **详情:**

  页脚样式格式化程序函数，采用一个参数：

  - `column`: 列对象。

  支持 `classes` 或 `css`.用法示例：

```
  functionfooterStyle(column){
    return{
      css:{'font-weight':'normal'},
      classes:'my-class'
    }
  }
  
```

- **默认:**`{}`

## showColumns

- **属性:**`data-show-columns`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为显示列下拉列表。我们可以将 [`switchable`](https://www.bootstrap-table.com.cn/doc/api/column-options/#switchable)选项设置`false`为隐藏下拉列表中项目。

- **默认:**`false`

## showColumnsToggleAll

- **属性:**`data-show-columns-toggle-all`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为在列选项/下拉列表中显示“全部切换”复选框。

- **默认:**`false`

## showColumnsSearch

- **属性:**`data-show-columns-search`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为显示对列过滤器的搜索。

- **默认:**`false`

## minimumCountColumns

- **属性:**`data-minimum-count-columns`

- **类型:**`Number`

- **详情:**

  从列下拉列表中隐藏的最小列数。

- **默认:**`1`

## showPaginationSwitch

- **属性:**`data-show-pagination-switch`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为显示分页开关按钮。

- **默认:**`false`

## showRefresh

- **属性:**`data-show-refresh`

- **类型:**`Boolean`

- **详情:**

  设置`true`为显示刷新按钮。

- **默认:**`false`

## showToggle

- **属性:**`data-show-toggle`

- **类型:**`Boolean`

- **详情:**

  设置`true`显示切换按钮以切换表格/卡片视图。

- **默认:**`false`

## showFullscreen

- **属性:**`data-show-fullscreen`

- **类型:**`Boolean`

- **详情:**

  设置`true`显示全屏按钮。

- **默认:**`false`

## smartDisplay

- **属性:**`data-smart-display`

- **类型:**`Boolean`

- **详情:**

  设置`true`为智能显示分页或名片视图。

- **默认:**`true`

## escape

- **属性:**`data-escape`

- **类型:**`Boolean`

- **详情:**

  转义用于插入HTML的字符串，并替换 &, <, >, “, `, and ‘ 字符。

- **默认:**`false`

## filterOptions

- **属性:**`data-filter-options`

- **类型:**`Boolean`

- **详情:**

  定义算法的默认过滤器选项， `filterAlgorithm: 'and'` 意味着所有给定的过滤器必须匹配， `filterAlgorithm: 'or'` 意味着给定的过滤器之一必须匹配。

- **默认:**`{ filterAlgorithm: 'and' }`

## idField

- **属性:**`data-id-field`

- **类型:**`String`

- **详情:**

  指明哪个字段将用作复选框/单选框值，与[selectItemName](https://www.bootstrap-table.com.cn/doc/api/table-options/#selectitemname)对应。

- **默认:**`undefined`

## selectItemName

- **属性:**`data-select-item-name`

- **类型:**`String`

- **详情:**

  单选或复选框输入的名称。

- **默认:**`'btSelectItem'`

## clickToSelect

- **属性:**`data-click-to-select`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为在单击行时选择复选框或单选框。

- **默认:**`false`

## ignoreClickToSelectOn

- **属性:**`data-ignore-click-to-select-on`

- **类型:**`Function`

- **详情:**

  设置忽略元素`clickToSelect`。接受一个参数：

  - `element`: 元素被点击。

  如果应忽略该单击，则返回true；如果应使该行被选择，则返回false。仅当`clickToSelect`为true时，此选项才相关。

- **默认:**`{ return ['A', 'BUTTON'].includes(tagName) }`

## singleSelect

- **属性:**`data-single-select`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为允许复选框仅选择一行。

- **默认:**`false`

## checkboxHeader

- **属性:**`data-checkbox-header`

- **类型:**`Boolean`

- **详情:**

  设置`false`为隐藏标题行中的所有复选框。

- **默认:**`true`

## maintainMetaData

- **属性:**`data-maintain-meta-data`

- **类型:**`Boolean`

- **详情:**

  设置`true`为在更改页面和搜索上维护以下元数据：

  - 选定的行
  - 隐藏的行

- **默认:**`false`

## multipleSelectRow

- **属性:**`data-multiple-select-row`

- **类型:**`Boolean`

- **详情:**

  设置`true`以启用多选行。可以使用ctrl键单击以选择一行，或使用shift键单击以选择一系列行。

- **默认:**`false`

## uniqueId

- **属性:**`data-unique-id`

- **类型:**`String`

- **详情:**

  为每一行指示唯一的标识符。

- **默认:**`undefined`

## cardView

- **属性:**`data-card-view`

- **类型:**`Boolean`

- **详情:**

  设置`true` 为显示名片视图表，例如移动视图。

- **默认:**`false`

## detailView

- **属性:**`data-detail-view`

- **类型:**`Boolean`

- **详情:**

  设置`true`为显示详细视图表。

- **默认:**`false`

## detailViewIcon

- **属性:**`data-detail-view-icon`

- **类型:**`Boolean`

- **详情:**

  设置`true`为显示详细信息视图列（加/减图标）。

- **默认:**`true`

## detailViewByClick

- **属性:**`data-detail-view-by-click`

- **类型:**`Boolean`

- **详情:**

  设置`true`单击以设置切换细节视图。

- **默认:**`false`

## detailFormatter

- **属性:**`data-detail-formatter`

- **类型:**`Function`

- **详情:**

  当格式化您的详细信息视图`detailView` 设置为 `true`。返回一个String，它将被附加到详细信息视图单元格中，可以选择使用第三个参数直接渲染该元素，该参数是目标单元格的jQuery元素。

- **默认:**`function(index, row, element) { return '' }`

## detailFilter

- **属性:**`data-detail-filter`

- **类型:**`Function`

- **详情:**

  当启用每行扩展`detailView` 设置到 `true`。返回true，将启用该行进行扩展，返回false，并且将禁用该行的扩展。默认函数返回true以启用所有行的扩展。

- **默认:**`function(index, row) { return true }`

## toolbar

- **属性:**`data-toolbar`

- **类型:**`String/Node`

- **详情:**

  jQuery选择指示工具栏，例如： `#toolbar`, `.toolbar`，或DOM节点。

- **默认:**`undefined`

## toolbarAlign

- **属性:**`data-toolbar-align`

- **类型:**`String`

- **详情:**

  指示如何对齐自定义工具栏。`'left'`, `'right'`可以使用。

- **默认:**`'left'`

## buttonsToolbar

- **属性:**`data-buttons-toolbar`

- **类型:**`String/Node`

- **详情:**

  jQuery选择，指示自定义按钮工具栏，例如：`#buttons-toolbar`, `.buttons-toolbar`，或DOM节点。

- **默认:**`undefined`

## buttonsAlign

- **属性:**`data-buttons-align`

- **类型:**`String`

- **详情:**

  指示如何对齐工具栏按钮。 `'left'`, `'right'`可以使用。

- **默认:**`'right'`

## buttonsOrder

- **属性:**`data-buttons-order`

- **类型:**`Array`

- **详情:**

  指示如何自定义工具栏按钮的顺序。

- **默认:**`['paginationSwitch', 'refresh', 'toggle', 'fullscreen', 'columns']`

## buttonsPrefix

- **属性:**`data-buttons-prefix`

- **类型:**`String`

- **详情:**

  定义表格按钮的前缀。

- **默认:**`'btn'`

## buttonsClass

- **属性:**`data-buttons-class`

- **类型:**`String`

- **详情:**

  定义`'btn-'`表格按钮的类（在后面添加）。

- **默认:**`'secondary'`

## icons

- **属性:**`data-icons`

- **类型:**`Object`

- **详情:**

  定义在工具栏，分页和详细信息视图中使用的图标。

- **默认:**

```
  {
    paginationSwitchDown: 'fa-caret-square-down',
    paginationSwitchUp: 'fa-caret-square-up',
    refresh: 'fa-sync',
    toggleOff: 'fa-toggle-off',
    toggleOn: 'fa-toggle-on',
    columns: 'fa-th-list',
    fullscreen: 'fa-arrows-alt',
    detailOpen: 'fa-plus',
    detailClose: 'fa-minus'
  }
  
```

- **例子:**[Table Icons](https://www.bootstrap-table.com.cn/examples/options/table-icons/)

## html

- **属性:**`data-html`

- **类型:**`Object`

- **详情:**

  定义表格的html。

- **默认:**

  代码太多，请签出`index.js`

## iconSize

- **属性:**`data-icon-size`

- **类型:**`String`

- **详情:**

  定义图标的大小， `undefined`, `'lg'`, `'sm'` 都可以使用。

- **默认:**`undefined`

## iconsPrefix

- **属性:**`data-icons-prefix`

- **类型:**`String`

- **详情:**

  定义图标集名称（`'glyphicon'` 或 `'fa'`）。默认情况下`'fa'`用于Bootstrap v4。

- **默认:**`'fa'`

### 列表选项

## field

- **属性:** `data-field`

- **类型:** `String`

- **详情:**

  列字段名称。

- **默认:** `undefined`

- **示例:** [列字段](https://www.bootstrap-table.com.cn/examples/column-options/field/)

## title

- **属性:** `data-title`

- **类型:** `String`

- **详情:**

  列标题文本。

- **默认:** `undefined`

- **示例:** [列标题](https://www.bootstrap-table.com.cn/examples/column-options/title/)

## titleTooltip

- **属性:** `data-title-tooltip`

- **类型:** `String`

- **详情:**

  列标题工具提示文本。此选项还支持标题HTML属性。

- **默认:** `undefined`

- **示例:** [标题工具提示](https://www.bootstrap-table.com.cn/examples/column-options/title-tooltip/)

## class

- **属性:** `class | data-class`

- **类型:** `String`

- **详情:**

  列类名称。

- **默认:** `undefined`

- **示例:** [列类](https://www.bootstrap-table.com.cn/examples/column-options/class/)

## width

- **属性:** `data-width`

- **类型:** `Number`

- **详情:**

  列的宽度。如果未定义，宽度将自动扩展以适合其内容。虽然如果表格保持响应并且大小太小，则`'width'` 可能会忽略该表格（通过类等使用min / max-width）。默认使用的单位是'px'，`widthUnit`用来改变它！

- **默认:** `undefined`

- **示例:** [列宽](https://www.bootstrap-table.com.cn/examples/column-options/width/)

## widthUnit

- **属性:** `data-width-unit`

- **类型:** `String`

- **详情:**

  定义用于选项的单位`width`.

- **默认:** `px`

- **示例:** [宽度单位](https://www.bootstrap-table.com.cn/examples/column-options/width-unit/)

## rowspan

- **属性:** `rowspan | data-rowspan`

- **类型:** `Number`

- **详情:**

  指示单元格应占用的行数。

- **默认:** `undefined`

- **示例:** [Rowspan Colspan](https://www.bootstrap-table.com.cn/examples/column-options/rowspan-colspan/)

## colspan

- **属性:** `colspan | data-colspan`

- **类型:** `Number`

- **详情:**

  指示单元格应占用的列数。

- **默认:** `undefined`

- **示例:** [Rowspan Colspan](https://www.bootstrap-table.com.cn/examples/column-options/rowspan-colspan/)

## align

- **属性:** `data-align`

- **类型:** `String`

- **详情:**

  指示如何对齐列数据。`'left'`, `'right'`, `'center'` 都可以使用。

- **默认:** `undefined`

- **示例:** [Aligning Columns](https://www.bootstrap-table.com.cn/examples/column-options/aligning-columns/)

## halign

- **属性:** `data-halign`

- **类型:** `String`

- **详情:**

  指示如何对齐表头。`'left'`, `'right'`, `'center'` 都可以使用。

- **默认:** `undefined`

- **示例:** [Aligning Columns](https://www.bootstrap-table.com.cn/examples/column-options/aligning-columns/)

## falign

- **属性:** `data-falign`

- **类型:** `String`

- **详情:**

  指示如何对齐表格页脚。 `'left'`, `'right'`, `'center'` 都可以使用。

- **默认:** `undefined`

- **示例:** [Aligning Footer](https://www.bootstrap-table.com.cn/examples/column-options/aligning-footer/)

## valign

- **属性:** `data-valign`

- **类型:** `String`

- **详情:**

  指出如何对齐单元格数据`'top'`, `'middle'`, `'bottom'` 都可以使用。

- **默认:** `undefined`

- **示例:** [Aligning Columns](https://www.bootstrap-table.com.cn/examples/column-options/aligning-columns/)

## cellStyle

- **属性:** `data-cell-style`

- **类型:** `Function`

- **详情:**

  单元格样式格式化函数，取四个参数：

  - `value`: 字段值。
  - `row`: 行记录数据。
  - `index`: 行索引。
  - `field`: 行字段。

  支持类或css。

- **默认:** `undefined`

- **示例:** [Cell Style](https://www.bootstrap-table.com.cn/examples/column-options/cell-style/)

## radio

- **属性:** `data-radio`

- **类型:** `Boolean`

- **详情:**

  设置`true` 为显示收音机。无线电列具有固定宽度。

  如果给出了值，则会自动检查复选框。也可以使用格式化程序检查/取消选中无线电（返回`true` 检查，返回 `false` 取消选中）。

- **默认:** `false`

- **示例:** [Column Radio](https://www.bootstrap-table.com.cn/examples/column-options/radio/)

## checkbox

- **属性:** `data-checkbox`

- **类型:** `Boolean`

- **详情:**

  设置`true` 为显示一个复选框。复选框列具有固定宽度。

  如果给出了值，则会自动检查复选框。也可以通过使用格式化程序来检查/取消选中该复选框（返回`true` 检查，返回 `false` 取消选中）。

- **默认:** `false`

- **示例:** [Column Checkbox](https://www.bootstrap-table.com.cn/examples/column-options/checkbox/)

## checkboxEnabled

- **属性:** `data-checkbox-enabled`

- **类型:** `Boolean`

- **详情:**

  设置`false` 为禁用复选框/ radioboxes。

- **默认:** `true`

- **示例:** [Checkbox Enabled](https://www.bootstrap-table.com.cn/examples/column-options/checkbox-enabled/) and [Checkbox Disabled](https://www.bootstrap-table.com.cn/examples/column-options/checkbox-disabled/)

## clickToSelect

- **属性:** `data-click-to-select`

- **类型:** `Boolean`

- **详情:**

  设置`true` 为在单击行时选择复选框或radiobox。

- **默认:** `false`

- **示例:** [Click to Select](https://www.bootstrap-table.com.cn/examples/column-options/click-to-select/)

## showSelectTitle

- **属性:** `data-show-select-title`

- **类型:** `Boolean`

- **详情:**

  设置`true` 为使用'radio'或'singleSelect''复选框'选项显示列的标题。

- **默认:** `false`

- **示例:** [Show Select Title](https://www.bootstrap-table.com.cn/examples/column-options/show-select-title/)

## sortable

- **属性:** `data-sortable`

- **类型:** `Boolean`

- **详情:**

  设置 `true`为允许列可以排序。

- **默认:** `false`

- **示例:** [Column Sortable](https://www.bootstrap-table.com.cn/examples/column-options/sortable/)

## sortName

- **属性:** `data-sort-name`

- **类型:** `String`

- **详情:**

  提供可自定义的排序名称，而不是标题中的默认排序名称或列的字段名称。例如，列可能会显示'html'的fieldName值，例如`<b><span style="color:red">abc</span></b>`，要排序的fieldName是'content'，其值为`'abc'`.

- **默认:** `undefined`

- **示例:** [Sort Name Order](https://www.bootstrap-table.com.cn/examples/column-options/sort-name-order/)

## order

- **属性:** `data-order`

- **类型:** `String`

- **详情:**

  默认排序顺序，只能是`'asc'` 或 `'desc'`.

- **默认:** `'asc'`

- **示例:** [Sort Name Order](https://www.bootstrap-table.com.cn/examples/column-options/sort-name-order/)

## sorter

- **属性:** `data-sorter`

- **类型:** `Function`

- **详情:**

  用于进行本地排序的自定义字段排序函数，有四个参数：

  - `fieldA`: 第一个字段值。
  - `fieldB`: 第二个字段值。
  - `rowA`: 第一排。
  - `rowB`: 第二排。

- **默认:** `undefined`

- **示例:** [Column Sorter](https://www.bootstrap-table.com.cn/examples/column-options/column-sorter/)

## visible

- **属性:** `data-visible`

- **类型:** `Boolean`

- **详情:**

  设置`false` 为隐藏列项。

- **默认:** `true`

- **示例:** [Column Visible](https://www.bootstrap-table.com.cn/examples/column-options/visible/)

## switchable

- **属性:** `data-switchable`

- **类型:** `Boolean`

- **详情:**

  设置`false` 为禁用可切换的列项。

- **默认:** `true`

- **示例:** [Column Switchable](https://www.bootstrap-table.com.cn/examples/column-options/switchable/)

## cardVisible

- **属性:** `data-card-visible`

- **类型:** `Boolean`

- **详情:**

  设置 `false` 为隐藏卡视图状态中的列项。

- **默认:** `true`

- **示例:** [Card Visible](https://www.bootstrap-table.com.cn/examples/column-options/card-visible/)

## searchable

- **属性:** `data-searchable`

- **类型:** `Boolean`

- **详情:**

  设置`true` 为搜索此列的数据。

- **默认:** `true`

- **示例:** [Column Searchable](https://www.bootstrap-table.com.cn/examples/column-options/searchable/)

## formatter

- **属性:** `data-formatter`

- **类型:** `Function`

- **详情:**

  上下文（this）是列Object。

  单元格格式函数，取三个参数：

  - `value`: 字段值。
  - `row`: 行记录数据。
  - `index`: 行索引。
  - `field`: 行字段。

- **默认:** `undefined`

- **示例:** [Column Formatter](https://www.bootstrap-table.com.cn/examples/column-options/format/)

## footerFormatter

- **属性:** `data-footer-formatter`

- **类型:** `Function`

- **详情:**

  上下文（this）是列Object。

  该函数，取一个参数：

  - `data`:所有数据行的数组。

  该函数应返回一个字符串，其中包含要在页脚单元格中显示的文本。

- **默认:** `undefined`

- **示例:** [Footer Formatter](https://www.bootstrap-table.com.cn/examples/column-options/footer-formatter/)

## detailFormatter

- **属性:** `data-detail-formatter`

- **类型:** `Function`

- **详情:**

  设置为 `detailView` 和时 `detailViewByClick` 设置 详细视图的格式 `true`. 返回a `String` 并将其附加到详细视图单元格中，可选地使用第三个参数直接渲染元素，该参数是目标单元格的jQuery元素。

  Fallback是表的详细格式化程序。

- **默认:** `function(index, row, $element) { return '' }`

- **示例:** [Detail Formatter](https://www.bootstrap-table.com.cn/examples/column-options/detail-formatter/)

## searchFormatter

- **属性:** `data-search-formatter`

- **类型:** `Boolean`

- **详情:**

  设置`true`为搜索使用格式化数据。

- **默认:** `true`

- **示例:** [Search Formatter](https://www.bootstrap-table.com.cn/examples/column-options/format-search/)

## escape

- **属性:** `data-escape`

- **类型:** `Boolean`

- **详情:**

  转义字符串以插入HTML，替换 &, <, >, “, `, 和 ‘ 字符。

- **默认:** `false`

- **示例:** [Column Escape](https://www.bootstrap-table.com.cn/examples/column-options/escape/)

## events

- **属性:** `data-events`

- **类型:** `Object`

- **详情:**

  使用格式化函数时的单元事件监听器，取四个参数：

  - `event`: jQuery事件。
  - `value`: 字段值。
  - `row`: 行记录数据。
  - `index`: 行索引。

  示例代码：

```
  <th .. data-events="operateEvent">
  var operateEvents = {
    'click .like': function (e, value, row, index) {}
  }
  
```

- **默认:** `undefined`
- **示例:** [Column Events](https://www.bootstrap-table.com.cn/examples/column-options/events/)

### 事件

要使用事件语法：

```
$('#table').bootstrapTable({
  onEventName: function (arg1, arg2, ...) {
    // ...
  }
})

$('#table').on('event-name.bs.table', function (e, arg1, arg2, ...) {
  // ...
})
```

## onAll

- **jQuery 事件:** `all.bs.table`

- **参数:** `name, args`

- **详情:**

  触发所有事件时触发，参数包含：

  - `name`: 事件名称，
  - `args`: 事件数据。

## onClickRow

- **jQuery 事件:** `click-row.bs.table`

- **参数:** `row, $element, field`

- **详情:**

  用户点击一行时触发，参数包含：

  - `row`: 与单击的行对应的记录。
  - `$element`: tr元素。
  - `field`:与单击的单元格对应的字段名称。

## onDblClickRow

- **jQuery 事件:** `dbl-click-row.bs.table`

- **参数:** `row, $element, field`

- **详情:**

  用户双击一行时触发，参数包含：

  - `row`: 与单击的行对应的记录。
  - `$element`: tr元素。
  - `field`: 与单击的单元格对应的字段名称。

## onClickCell

- **jQuery 事件:** `click-cell.bs.table`

- **参数:** `field, value, row, $element`

- **详情:**

  用户单击一个单元格时触发，参数包含：

  - `field`: 与单击的单元格对应的字段名称。
  - `value`: 与单击的单元格对应的数据值。
  - `row`: 与单击的行对应的记录。
  - `$element`: td元素。

## onDblClickCell

- **jQuery 事件:** `dbl-click-cell.bs.table`

- **参数:** `field, value, row, $element`

- **详情:**

  用户双击单元格时触发，参数包含：

  - `field`: 与单击的单元格对应的字段名称。
  - `value`: 与单击的单元格对应的数据值。
  - `row`: 与单击的行对应的记录。
  - `$element`:td元素。

## onSort

- **jQuery 事件:** `sort.bs.table`

- **参数:** `name, order`

- **详情:**

  用户对列进行排序时触发，参数包含：

  - `name`: 排序列字段名称。
  - `order`: 排序列顺序。

## onCheck

- **jQuery 事件:** `check.bs.table`

- **参数:** `row, $element`

- **详情:**

  当用户检查一行时触发，参数包含：

  - `row`: 与单击的行对应的记录。
  - `$element`: 检查DOM元素。

## onUncheck

- **jQuery 事件:** `uncheck.bs.table`

- **参数:** `row, $element`

- **详情:**

  当用户取消选中一行时触发，参数包含：

  - `row`: 与单击的行对应的记录。
  - `$element`: 未选中DOM元素。

## onCheckAll

- **jQuery 事件:** `check-all.bs.table`

- **参数:** `rowsAfter, rowsBefore`

- **详情:**

  当用户检查所有行时触发，参数包含：

  - `rowsAfter`: 现在检查的行的记录数组。
  - `rowsBefore`: 之前已检查行的记录数组。

## onUncheckAll

- **jQuery 事件:** `uncheck-all.bs.table`

- **参数:** `rowsAfter, rowsBefore`

- **详情:**

  当用户取消选中所有行时触发，参数包含：

  - `rowsAfter`: 现在检查的行的记录数组。
  - `rowsBefore`: 之前已检查行的记录数组。

## onCheckSome

- **jQuery 事件:** `check-some.bs.table`

- **参数:** `rows`

- **详情:**

  用户检查某些行时触发，参数包含：

  - `rows`: 与新检查的行对应的记录数组。

## onUncheckSome

- **jQuery 事件:** `uncheck-some.bs.table`

- **参数:** `rows`

- **详情:**

  当用户取消选中某些行时触发，参数包含：

  - `rows`: 与先前检查的行对应的记录数组。

## onLoadSuccess

- **jQuery 事件:** `load-success.bs.table`

- **参数:** `data`

- **详情:**

  成功加载远程数据时触发，参数包含：

  - `data`: 远程数据。

## onLoadError

- **jQuery 事件:** `load-error.bs.table`

- **参数:** `status, jqXHR`

- **详情:**

  在加载远程数据时发生某些错误时触发，参数包含：

  - `status`: 状态代码`jqXHR`.
  - `jqXHR`:jqXHR对象，它是XMLHTTPRequest对象的超集。有关更多信息，请参阅 [jqXHR Type](http://api.jquery.com/Types/#jqXHR).

## onColumnSwitch

- **jQuery 事件:** `column-switch.bs.table`

- **参数:** `field, checked`

- **详情:**

  切换列可见时触发 ([showColumns](https://www.bootstrap-table.com.cn/doc/api/table-options/#showcolumns))，参数包含：

  - `field`:与switch列对应的字段名称。
  - `checked`: 列的已检查状态。

## onPageChange

- **jQuery 事件:** `page-change.bs.table`

- **参数:** `number, size`

- **详情:**

  更改页码或页面大小时触发，参数包含：

  - `number`: 页码。
  - `size`:页面大小。

## onSearch

- **jQuery 事件:** `search.bs.table`

- **参数:** `text`

- **详情:**

  搜索表时触发，参数包含：

  - `text`: 搜索输入的文本。

## onToggle

- **jQuery 事件:** `toggle.bs.table`

- **参数:** `cardView`

- **详情:**

  切换表格视图时触发，参数包含：

  - `cardView`: 表的cardView状态。

## onPreBody

- **jQuery 事件:** `pre-body.bs.table`

- **参数:** `data`

- **详情:**

  在渲染表体之前触发，参数包含：

  - `data`: 渲染数据。

## onPostBody

- **jQuery 事件:** `post-body.bs.table`

- **参数:** `data`

- **详情:**

  在表体呈现并在DOM中可用之后触发，参数包含：

  - `data`: 渲染数据。

## onPostHeader

- **jQuery 事件:** `post-header.bs.table`

- **参数:** `undefined`

- **详情:**

  在表头呈现并在DOM中可用之后触发。

## onPostFooter

- **jQuery 事件:** `post-footer.bs.table`

- **参数:** `$tableFooter`

- **详情:**

  在页脚呈现并在DOM中可用后触发，参数包含：

  - `$tableFooter`: 页脚的DOM元素。

## onExpandRow

- **jQuery 事件:** `expand-row.bs.table`

- **参数:** `index, row, $detail`

- **详情:**

  单击详细信息图标以展开详细视图时触发，参数包含：

  - `index`: 扩展行的索引。
  - `row`: 与扩展行对应的记录。
  - `$detail`: `div` 当前 `tr` 元素之后的详细信息的DOM元素，您可以使用jQuery方法来自定义详细信息视图。

## onCollapseRow

- **jQuery 事件:** `collapse-row.bs.table`

- **参数:** `index, row, detailView`

- **详情:**

  单击详细信息图标时会触发，以折叠详细视图，参数包含：

  - `index`:折叠行的索引。
  - `row`:与折叠行对应的记录。
  - `detailView`: 折叠的detailView。

## onRefreshOptions

- **jQuery 事件:** `refresh-options.bs.table`

- **参数:** `options`

- **详情:**

  刷新选项后，在销毁和初始化表之前触发，参数包含：

  - `options`: 表选项对象。

## onResetView

- **jQuery 事件:** `reset-view.bs.table`

- **参数:** `undefined`

- **详情:**

  重置表格视图时触发。

## onRefresh

- **jQuery 事件:** `refresh.bs.table`

- **参数:** `params`

- **详情:**

  单击刷新按钮后触发，参数包含：

  - `params`: 对服务器的附加参数请求。

## onScrollBody

- **jQuery 事件:** `scroll-body.bs.table`

- **参数:**: `undefined`

- **详情:**

  桌面滚动时发射。

### 方法

## getOptions

- **参数:** `undefined`

- **详情:**

  返回选项对象。

- **示例:** [获取选项](https://www.bootstrap-table.com.cn/examples/methods/get-options/)

## refreshOptions

- **参数:** `options`

- **详情:**

  刷新表格`options`.

- **示例:** [刷新选项](https://www.bootstrap-table.com.cn/examples/methods/refresh-options/)

## getData

- **参数:** `params`

- **详情:**

  在调用此方法时获取表的加载数据

  - `useCurrentPage`:如果设置为true，则该方法仅在当前页面中返回数据。
  - `includeHiddenRows`: 如果设置为true，则该方法将包含隐藏的行。

- **示例:** [获取数据](https://www.bootstrap-table.com.cn/examples/methods/getData/)

## getSelections

- **参数:** `undefined`

- **详情:**

  返回选定的行，如果未选择任何记录，则返回一个空数组。

- **示例:** [获取选择](https://www.bootstrap-table.com.cn/examples/methods/get-selections/)

## getAllSelections

- **参数:** `undefined`

- **详情:**

  返回所有选定的行包含搜索或过滤，当没有选择记录时，将返回一个空数组。

- **示例:** [获取所有选择](https://www.bootstrap-table.com.cn/examples/methods/get-all-selections/)

## load

- **参数:** `data`

- **详情:**

  加载 `data` 到表，旧行将被删除。

- **示例:** [加载](https://www.bootstrap-table.com.cn/examples/methods/load/)

## append

- **参数:** `data`

- **详情:**

  附加`data`到表格。

- **示例:** [附加](https://www.bootstrap-table.com.cn/examples/methods/append/)

## prepend

- **参数:** `data`

- **详情:**

  前置`data`到表。

- **示例:** [前置](https://www.bootstrap-table.com.cn/examples/methods/prepend/)

## remove

- **参数:** `params`

- **详情:**

  从表中删除数据，params包含两个属性：

  - `field`: 删除行的字段名称。
  - `values`: 应删除的行的值数组。

- **示例:** [删除](https://www.bootstrap-table.com.cn/examples/methods/remove/)

## removeAll

- **参数:** `undefined`

- **详情:**

  从表中删除所有数据。

- **示例:** [全部删除](https://www.bootstrap-table.com.cn/examples/methods/remove-all/)

## insertRow

- **参数:** `params`

- **详情:**

  插入一个新行，params包含以下属性：

  - `index`: 要插入的行索引。
  - `row`: 行数据。

- **示例:** [插入行](https://www.bootstrap-table.com.cn/examples/methods/insert-row/)

## updateRow

- **参数:** `params`

- **详情:**

  更新指定的行，每个参数包含以下属性：

  - `index`:要更新的行索引。
  - `row`: 新的行数据。
  - `replace` （可选）:设置为`true` 替换行而不是扩展。

- **示例:** [更新行](https://www.bootstrap-table.com.cn/examples/methods/update-row/)

## getRowByUniqueId

- **参数:** `id`

- **详情:**

  从表中获取数据，该行包含`id`传递的参数。

- **示例:** [按唯一ID获取行](https://www.bootstrap-table.com.cn/examples/methods/get-row-by-unique-id/)

## updateByUniqueId

- **参数:** `params`

- **详情:**

  更新指定的行，每个参数包含以下属性：

  - `id`: 行id，其中id应该是分配给表的uniqueid字段。
  - `row`: 新的行数据。
  - `replace` （可选）:设置为`true` 替换行而不是扩展。

- **示例:** [按唯一ID更新](https://www.bootstrap-table.com.cn/examples/methods/update-by-unique-id/)

## removeByUniqueId

- **参数:** `id`

- **详情:**

  从表中删除数据，该行包含`id` 传递的参数。

- **示例:** [按唯一ID删除](https://www.bootstrap-table.com.cn/examples/methods/remove-by-unique-id/)

## updateCell

- **参数:** `params`

- **详情:**

  更新一个单元格，params包含以下属性：

  - `index`: 行索引。
  - `field`: 字段名称。
  - `value`: 新的字段值。

  要禁用表重新初始化，您可以设置`{reinit: false}`.

- **示例:** [更新Cell](https://www.bootstrap-table.com.cn/examples/methods/update-cell/)

## updateCellByUniqueId

- **参数:** `params`

- **详情:**

  更新id指定的单元格，每个参数包含以下属性：

  - `id`: row id，其中id应该是`uniqueId`分配给表的字段。
  - `field`: 要更新的单元格的字段名称。
  - `value`: 细胞的新价值。

- **示例:** [按唯一ID更新单元格](https://www.bootstrap-table.com.cn/examples/methods/update-cell-by-unique-id/)

## showRow

- **参数:** `params`

- **详情:**

  显示指定的行。参数必须至少包含以下属性之一：

  - `index`: 行索引。
  - `uniqueId`:该行的uniqueId的值。

- **示例:** [显示/隐藏行](https://www.bootstrap-table.com.cn/examples/methods/show-hide-row/)

## hideRow

- **参数:** `params`

- **详情:**

  隐藏指定的行。参数必须至少包含以下属性之一：

  - `index`: 行索引。
  - `uniqueId`: 该行的uniqueId的值。

- **示例:** [显示/隐藏行](https://www.bootstrap-table.com.cn/examples/methods/show-hide-row/)

## getHiddenRows

- **参数:** `show`

- **详情:**

  隐藏所有行，如果传递`show` 参数 `true` ，则会再次显示行，否则，该方法仅返回隐藏的行。

- **示例:** [获取隐藏的行](https://www.bootstrap-table.com.cn/examples/methods/get-hidden-rows/)

## showColumn

- **参数:** `field`

- **详情:**

  显示指定的`field`列。参数可以是字符串或字段数组。

- **示例:** [显示/隐藏列](https://www.bootstrap-table.com.cn/examples/methods/show-hide-column/)

## hideColumn

- **参数:** `field`

- **详情:**

  隐藏指定的`field`列。参数可以是字符串或字段数组。

- **示例:** [显示/隐藏列](https://www.bootstrap-table.com.cn/examples/methods/show-hide-column/)

## getVisibleColumns

- **参数:** `-`

- **详情:**

  获取可见列。

- **示例:** [获取可见/隐藏列](https://www.bootstrap-table.com.cn/examples/methods/get-visible-hidden-columns/)

## getHiddenColumns

- **参数:** `undefined`

- **详情:**

  获取隐藏的列。

- **示例:** [获取可见/隐藏列](https://www.bootstrap-table.com.cn/examples/methods/get-visible-hidden-columns/)

## showAllColumns

- **参数:** `undefined`

- **详情:**

  显示所有列。

- **示例:** [显示/隐藏所有列](https://www.bootstrap-table.com.cn/examples/methods/show-hide-all-columns/)

## hideAllColumns

- **参数:** `undefined`

- **详情:**

  隐藏所有列。

- **示例:** [显示/隐藏所有列](https://www.bootstrap-table.com.cn/examples/methods/show-hide-all-columns/)

## mergeCells

- **参数:** `params`

- **详情:**

  将一些单元格合并到一个单元格，params包含以下属性：

  - `index`: 行索引。
  - `field`: 字段名称。
  - `rowspan`: 要合并的rowspan计数。
  - `colspan`: 要合并的colspan计数。

- **示例:** [合并单元格](https://www.bootstrap-table.com.cn/examples/methods/merge-cells/)

## checkAll

- **参数:** `undefined`

- **详情:**

  检查所有当前页面行。

- **示例:** [选中/取消选中全部](https://www.bootstrap-table.com.cn/examples/methods/check-uncheck-all/)

## uncheckAll

- **参数:** `undefined`

- **详情:**

  取消选中所有当前页面行。

- **示例:** [选中/取消选中全部](https://www.bootstrap-table.com.cn/examples/methods/check-uncheck-all/)

## checkInvert

- **参数:** `undefined`

- **详情:**

  反转检查当前页面行。触发器`onCheckSome` 和 `onUncheckSome` 事件。

- **示例:** [检查反转](https://www.bootstrap-table.com.cn/examples/methods/check-invert/)

## check

- **参数:** `index`

- **详情:**

  检查一行，该行`index` 以0开头。

- **示例:** [选中/取消选中](https://www.bootstrap-table.com.cn/examples/methods/check-uncheck/)

## uncheck

- **参数:** `index`

- **详情:**

  取消选中一行，该行`index` 以0开头。

- **示例:** [选中/取消选中](https://www.bootstrap-table.com.cn/examples/methods/check-uncheck/)

## checkBy

- **参数:** `params`

- **详情:**

  按值数组检查行，参数包含：

  - `field`: 用于查找记录的字段的名称。
  - `values`: 要检查的行的值数组。

- **示例:** [选中/取消选中](https://www.bootstrap-table.com.cn/examples/methods/check-uncheck-by/)

## uncheckBy

- **参数:** `params`

- **详情:**

  取消按值数组取消行，params包含：

  - `field`: 用于查找记录的字段的名称。
  - `values`: 要取消选中的行的值数组。

- **示例:** [选中/取消选中](https://www.bootstrap-table.com.cn/examples/methods/check-uncheck-by/)

## refresh

- **参数:** `params`

- **详情:**

  刷新/重新加载远程服务器数据，您可以设置`{silent: true}` 为静默刷新数据，并设置`{url: newUrl, pageNumber: pageNumber, pageSize: pageSize}` 更改URL（可选），页码（可选）和页面大小（可选）。要提供特定于此请求的查询参数，请设置`{query: {foo: 'bar'}}`.

- **示例:** [刷新](https://www.bootstrap-table.com.cn/examples/methods/refresh/)

## destroy

- **参数:** `undefined`

- **详情:**

  销毁Bootstrap表。

- **示例:** [销毁](https://www.bootstrap-table.com.cn/examples/methods/destroy/)

## resetView

- **参数:** `params`

- **详情:**

  重置Bootstrap Table视图，例如重置表高度，params包含：

  - `height`: 桌子的高度。

- **示例:** [重置视图](https://www.bootstrap-table.com.cn/examples/methods/reset-view/)

## resetWidth

- **参数:** `undefined`

- **详情:**

  调整页眉和页脚的大小以适合当前列宽。

## showLoading

- **参数:** `undefined`

- **详情:**

  显示加载状态。

- **示例:** [显示/隐藏加载](https://www.bootstrap-table.com.cn/examples/methods/show-hide-loading/)

## hideLoading

- **参数:** `undefined`

- **详情:**

  隐藏加载状态。

- **示例:** [显示/隐藏加载](https://www.bootstrap-table.com.cn/examples/methods/show-hide-loading/)

## togglePagination

- **参数:** `undefined`

- **详情:**

  切换分页选项。

- **示例:** [切换分页](https://www.bootstrap-table.com.cn/examples/methods/toggle-pagination/)

## toggleFullscreen

- **参数:** `undefined`

- **详情:**

  切换全屏。

- **示例:** [切换全屏](https://www.bootstrap-table.com.cn/examples/methods/toggle-fullscreen/)

## toggleView

- **参数:** `undefined`

- **详情:**

  切换卡/表视图。

- **示例:** [切换卡/表视图](https://www.bootstrap-table.com.cn/examples/methods/toggle-view/)

## resetSearch

- **参数:** `text`

- **详情:**

  设置搜索`text`.

- **示例:** [重置搜索](https://www.bootstrap-table.com.cn/examples/methods/reset-search/)

## filterBy

- 参数:

  - `filter - An Object of filter` 默认: `{}`

  - ```
    options - An Object of options
    ```

     

    默认:

    ```
      {
          'filterAlgorithm': 'and'
      }
    ```

- **详情:**

  （只能在客户端使用）过滤表中的数据。有多种方法可以过滤：

  - 将选项留空以使用 `and`过滤器。
  - 设置`filterAlgorithm` （参见参数）`or` 以使用 `or`过滤器。
  - 将函数传递给`filterAlgorithm`（参见参数）以使用`custom` 过滤器。

  **过滤算法**

  - 和
    - 过滤`{age: 10}` 以显示仅数据年龄等于10.您还可以使用值数组进行过滤，如下所示：`{age: 10, hairColor: ['blue', 'red', 'green']}` 查找年龄等于10且hairColor为蓝色，红色或绿色的数据。
  - 要么
    - 过滤`{age: 10, name: "santa"}` 以显示所有年龄为10 或名称等于圣诞老人的数据。
  - 习惯
    - 按自定义算法过滤
    - 功能参数：
      - 行
      - 过滤器
    - 返回 `true` 以保留行并返回`false`以过滤行。

- **示例:** [过滤](https://www.bootstrap-table.com.cn/examples/methods/filter-by/)

## scrollTo

- **参数:** `value|object`
- **详情:**
  - 值
    - 滚动到数字`value` 位置，单位为`'px'`, 设置 `'bottom'`表示滚动到底部。
  - 宾语
    - 滚动到单位（(`px` 或 `rows (index starts by 0)`) 默认值： `{unit: 'px', value: 0}`
- **示例:** [滚动到](https://www.bootstrap-table.com.cn/examples/methods/scorll-to/)

## getScrollPosition

- **参数:** `undefined`

- **详情:**

  获取当前滚动位置，单位是`'px'`.

- **示例:** [获取滚动位置](https://www.bootstrap-table.com.cn/examples/methods/get-scroll-position/)

## selectPage

- **参数:** `page`

- **详情:**

  转到指定的`page`.

- **示例:** [选择/上一页/下一页](https://www.bootstrap-table.com.cn/examples/methods/select-prev-next-page/)

## prevPage

- **参数:** `undefined`

- **详情:**

  转到上一页。

- **示例:** [选择/上一页/下一页](https://www.bootstrap-table.com.cn/examples/methods/select-prev-next-page/)

## nextPage

- **参数:** `undefined`

- **详情:**

  转到下一页。

- **示例:** [选择/上一页/下一页](https://www.bootstrap-table.com.cn/examples/methods/select-prev-next-page/)

## toggleDetailView

- **参数:** `index`

- **详情:**

  `index` 如果详细视图选项设置为 ，则切换具有传递的参数的行`true`.

- **示例:** [切换细节视图](https://www.bootstrap-table.com.cn/examples/methods/toggle-detail-view/)

## expandRow

- **参数:** `index`

- **详情:**

  `index` 如果详细视图选项设置为 ，则展开具有传递的参数的行`true`.

- **示例:** [展开/折叠行](https://www.bootstrap-table.com.cn/examples/methods/expand-collapse-row/)

## collapseRow

- **参数:** `index`

- **详情:**

  `index` 如果详细视图选项设置为 ，则折叠具有传递的参数的行 `true`.

- **示例:** [展开/折叠行](https://www.bootstrap-table.com.cn/examples/methods/expand-collapse-row/)

## expandAllRows

- **参数:** `undefined`

- **详情:**

  如果详细视图选项设置为，则展开所有行 `true`.

- **示例:** [展开/折叠所有行](https://www.bootstrap-table.com.cn/examples/methods/expand-collapse-all-rows/)

## collapseAllRows

- **参数:** `undefined`

- **详情:**

  如果详细视图选项设置为，则折叠所有行`true`.

- **示例:** [展开/折叠所有行](https://www.bootstrap-table.com.cn/examples/methods/expand-collapse-all-rows/)

## updateColumnTitle

- **参数:** `params`

- **详情:**

  更新列的字段标题，参数包含以下属性：

  - `field`: 字段名称。
  - `title`: 字段标题。

- **示例:** [更新列标题](https://www.bootstrap-table.com.cn/examples/methods/update-column-title/)

## updateFormatText

- **参数:** `formatName, text`

- **详情:**

  更新本地化格式文本。

- **示例:** [更新格式文本](https://www.bootstrap-table.com.cn/examples/methods/update-format-text/)

### 本地化

我们可以导入所需的[所有语言环境文件：](https://github.com/wenzhixin/bootstrap-table/tree/master/src/locale)

```
​```html
<script src="bootstrap-table-en-US.js"></script>
<script src="bootstrap-table-zh-CN.js"></script>
...
```

然后使用JavaScript切换区域设置：

```
$.extend($.fn.bootstrapTable.Defaults, $.fn.bootstrapTable.locales['en-US'])
// $.extend($.fn.bootstrapTable.Defaults, $.fn.bootstrapTable.locales['zh-CN'])
// ...
```

或使用数据属性为表设置区域设置：

```
<table data-toggle="table" data-locale="en-US">
</table>
```

或者使用JavaScript为表设置语言环境：

```
$('#table').bootstrapTable({
  locale: 'en-US'
})
```

您可以自定义格式本地化，调用语法：

```
$('#table').bootstrapTable({
  formatName: function () {
    return 'Format message'
  }
})
```

## formatLoadingMessage

- **参数:** `undefined`
- **默认:** `'Loading, please wait…'`

## formatRecordsPerPage

- **参数:** `pageNumber`
- **默认:** `'%s records per page'`

## formatShowingRows

- **参数:** `pageFrom, pageTo, totalRows`
- **默认:** `'Showing %s to %s of %s rows'`

## formatSRPaginationPreText

- **参数:** `undefined`
- **默认:** `'previous page'`

## formatSRPaginationPageText

- **参数:** `page`
- **默认:** `'to page %s`

## formatSRPaginationNextText

- **参数:** `undefined`
- **默认:** `'next page'`

## formatDetailPagination

- **参数:** `totalRows`
- **默认:** `'Showing %s rows'`

## formatSearch

- **参数:** `undefined`
- **默认:** `'Search'`

## formatClearSearch

- **参数:** `undefined`
- **默认:** `'Clear Search'`

## formatNoMatches

- **参数:** `undefined`
- **默认:** `'No matching records found'`

## formatPaginationSwitch

- **参数:** `undefined`
- **默认:** `'Hide/Show pagination'`

## formatPaginationSwitchDown

- **参数:** `undefined`
- **默认:** `'Show pagination'`

## formatPaginationSwitchUp

- **参数:** `undefined`
- **默认:** `'Hide pagination'`

## formatRefresh

- **参数:** `undefined`
- **默认:** `'Refresh'`

## formatToggle

- **参数:** `undefined`
- **默认:** `'Toggle'`

## formatToggleOn

- **参数:** `undefined`
- **默认:** `'Show card view'`

## formatToggleOff

- **参数:** `undefined`
- **默认:** `'Hide card view'`

## formatColumns

- **参数:** `undefined`
- **默认:** `'Columns'`

## formatColumnsToggleAll

- **参数:** `undefined`
- **默认:** `'Toggle all'`

## formatFullscreen

- **参数:** `undefined`
- **默认:** `'Fullscreen'`

## formatAllRows

- **参数:** `undefined`
- **默认:** `'All'`