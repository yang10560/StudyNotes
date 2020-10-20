### 介绍

日期插件

### 入门

```html
<!doctype html>
<html lang="zh">
	
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Hello, Bootstrap Table!</title>

    <link rel="stylesheet" href="./table/bootstrap.min.css" integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS" crossorigin="anonymous">
    <!-- <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.6.3/css/all.css" integrity="sha384-UHRtZLI+pbxtHCWp1t77Bi1L4ZtiqrqD80Kn4Z8NTSRyMA2Fd33n5dQ8lWUE00s/" crossorigin="anonymous"> -->
    <link rel="stylesheet" href="./table/bootstrap-table.min.css">
   <!-- <link rel="stylesheet" href="./daterangepicker/css/bootstrap-datepicker.css"> -->
    <link rel="stylesheet" href="./daterangepicker/css/bootstrap-datepicker3.css">
   <!-- <link rel="stylesheet" href="./daterangepicker/css/bootstrap-datepicker.standalone.css"> -->
    <link rel="stylesheet" href="./daterangepicker/css/bootstrap-datepicker3.standalone.css">
  </head>
	<body>
		
		<hr>
		<h1>daterangepicker</h1>
		<div class="input-group">
		<p>起始日期 :</p></label<><input type="text" class="form-control" id="start_day"  />
		   截止日期 : <input type="text" class="form-control" id="end_day"  />
		</div>
		
		<div>
			<input class="datepicker form-control" data-date-format="mm/dd/yyyy">
			<input type="text" id="dp1" class="form-control" value="02-16-2012">
		</div>
		
		<div class="input-group date">
		    <input id="dp2" type="text" class="form-control" value="12-02-2012">
		    <div class="input-group-addon">
		        <span class="glyphicon glyphicon-th"></span>
		    </div>
		</div>
		
		
		
		
		<script src="js/jquery-3.3.1.min.js" integrity="sha256-FgpCb/KJQlLNfOu91ta32o/NMZxltwRo8QtmkMRdAu8=" crossorigin="anonymous"></script>
		<script src="./table/popper.min.js" integrity="sha384-wHAiFfRlMFy6i5SRaxvfOCifBUQy1xHdJ/yoi7FRNXMRBu5WHdZYu1hA6ZOblgut" crossorigin="anonymous"></script>
		<script src="./table/bootstrap.min.js" integrity="sha384-B0UglyR+jN6CkvvICOB2joaf5I4l3gm9GU6Hc1og6Ls7i6U/mkkaduKaBhlAXv9k" crossorigin="anonymous"></script>
		<script src="./daterangepicker/js/bootstrap-datepicker.js"></script>
		<script src="./daterangepicker/locales/bootstrap-datepicker.zh-CN.min.js"></script>
		
	</body>
	<script>
		$(document).ready(function(){
			
		   $("#start_day").datepicker({
			   format:'yyyy-mm-dd',
			  /* startDate: '+0d', */
			   clearBtn:true,
			   autoclose:true,
			   calendarWeeks:true,
			   language:'zh-CN',
			   multidate:true,
			   multidateSeparator:',',
			   orientation:'auto',
			   todayBtn:true,
			   todayHighlight:true,
			   forceParse:0
			   
			   
		   })
		  
		   
		   $("#end_day").datepicker()
		   
		})
		
		$('.datepicker').datepicker({
		    startDate: '-3d'
    
		});
		
		$('#dp1').datepicker();
		$('#dp2').datepicker();
		/* $('.form-control').datepicker(); */
		
	</script>
</html>

```



```js
//zh-CN.js
!function(a){a.fn.datepicker.dates["zh-CN"]={days:["星期日","星期一","星期二","星期三","星期四","星期五","星期六"],daysShort:["周日","周一","周二","周三","周四","周五","周六"],daysMin:["日","一","二","三","四","五","六"],months:["一月","二月","三月","四月","五月","六月","七月","八月","九月","十月","十一月","十二月"],monthsShort:["1月","2月","3月","4月","5月","6月","7月","8月","9月","10月","11月","12月"],today:"今天",monthsTitle:"选择月份",clear:"清除",format:"yyyy-mm-dd",titleFormat:"yyyy年mm月",weekStart:1}}(jQuery);
```

### Date API

https://bootstrap-datepicker.readthedocs.io/en/stable/



### dateTimePicker

https://www.bootcss.com/p/bootstrap-datetimepicker/index.htm