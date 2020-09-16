

###  if

```
<#if animals.python.price < animals.elephant.price>
  Pythons are cheaper than elephants today.
<#else>
  Pythons are not cheaper than elephants today.
</#if>

<#if animals.python.price < animals.elephant.price>
  Pythons are cheaper than elephants today.
<#elseif animals.elephant.price < animals.python.price>
  Elephants are cheaper than pythons today.
<#else>
  Elephants and pythons cost the same today.
</#if>

```

###  list

```

<#list animals as animal>
   <tr><td>${animal.name}<td>${animal.price} Euros
 </#list>

<p>Fruits: <#list misc.fruits as fruit>${fruit}<#sep>, </#list>
<p>Fruits: orange, banana

<p>Fruits: <#list misc.fruits as fruit>${fruit}<#sep>, <#else>None</#list>
```

### include 指令

使用 `include` 指令， 我们可以在模板中插入其他文件的内容。

```
<html>
<head>
  <title>Test page</title>
</head>
<body>
  <h1>Test page</h1>
  <p>Blah blah...
  <#include "/copyright_footer.html">
</body>
</html>
```



### 内建函数

内建函数很像子变量(如果了解Java术语的话，也可以说像方法)， 它们并不是数据模型中的东西，是 FreeMarker 在数值上添加的。 为了清晰子变量是哪部分，使用 `?`(问号)代替 `.`(点)来访问它们。常用内建函数的示例：

- `user?html` 给出 `user` 的HTML转义版本， 比如 `&` 会由 `&` 来代替。
- `user?upper_case` 给出 `user` 值的大写版本 (比如 "JOHN DOE" 来替代 "John Doe")
- `animal.name?cap_first` 给出 `animal.name` 的首字母大写版本(比如 "Mouse" 来替代 "mouse")
- `user?length` 给出 `user` 值中 *字符*的数量(对于 "John Doe" 来说就是8)
- `animals?size` 给出 `animals` 序列中 *项目* 的个数(我们示例数据模型中是3个)
- 如果在 `<#list animals as animal>` 和对应的 `</#list>` 标签中：
  - `animal?index` 给出了在 `animals` 中基于0开始的 `animal`的索引值
  - `animal?counter` 也像 `index`， 但是给出的是基于1的索引值
  - `animal?item_parity` 基于当前计数的奇偶性，给出字符串 "odd" 或 "even"。在给不同行着色时非常有用，比如在 `<td class="${animal?item_parity}Row">`中。

一些内建函数需要参数来指定行为，比如：

- `animal.protected?string("Y", "N")` 基于 `animal.protected` 的布尔值来返回字符串 "Y" 或 "N"。
- `animal?item_cycle('lightRow','darkRow')` 是之前介绍的 `item_parity` 更为常用的变体形式。
- `fruits?join(", ")` 通过连接所有项，将列表转换为字符串， 在每个项之间插入参数分隔符(比如 "orange,banana")
- `user?starts_with("J")` 根据 `user` 的首字母是否是 "J" 返回布尔值true或false。

内建函数应用可以链式操作，比如`user?upper_case?html` 会先转换用户名到大写形式，之后再进行HTML转义。(这就像可以链式使用 `.`(点)一样)

[全部内建函数参考](http://freemarker.foofun.cn/ref_builtins.html)



### 处理不存在的变量

不论在哪里引用变量，都可以指定一个默认值来避免变量丢失这种情况， 通过在变量名后面跟着一个 `!`(叹号，译者注)和默认值。

```
<h1>Welcome ${user!"visitor"}!</h1>
```

也可以在变量名后面通过放置 `??` 来询问一个变量是否存在。将它和 `if` 指令合并， 那么如果 `user` 变量不存在的话将会忽略整个问候的代码段：

```
<#if user??><h1>Welcome ${user}!</h1></#if>
```



### 快速清单

- 直接指定值

  - [字符串](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_direct_string)： `"Foo"` 或者 `'Foo'` 或者 `"It's \"quoted\""` 或者 `'It\'s "quoted"'` 或者 `r"C:\raw\string"`
  - [数字](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_direct_number)： `123.45`
  - [布尔值](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_direct_boolean)： `true`， `false`
  - [序列](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_direct_seuqence)： `["foo", "bar", 123.45]`； 值域： `0..9`, `0..<10` (或 `0..!10`), `0..`
  - [哈希表](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_direct_hash)： `{"name":"green mouse", "price":150}`

- 检索变量

  - [顶层变量](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_var_toplevel)： `user`
  - [从哈希表中检索数据](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_var_hash)： `user.name`， `user["name"]`
  - [从序列中检索数据](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_var_sequence)： `products[5]`
  - [特殊变量](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_var_special)： `.main`

- 字符串操作

  - [插值(或连接)](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_stringop_interpolation)： `"Hello ${user}!"` (或 `"Hello " + user + "!"`)
  - [获取一个字符](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_get_character)： `name[0]`
  - [字符串切分：](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_stringop_slice) 包含结尾： `name[0..4]`，不包含结尾： `name[0..<5]`，基于长度(宽容处理)： `name[0..*5]`，去除开头： `name[5..]`

- 序列操作

  - [连接](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_sequenceop_cat)： `users + ["guest"]`
  - [序列切分](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_seqenceop_slice)：包含结尾： `products[20..29]`， 不包含结尾： `products[20..<30]`，基于长度(宽容处理)： `products[20..*10]`，去除开头： `products[20..]`

- 哈希表操作

  - [连接](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_hashop_cat)： `passwords + { "joe": "secret42" }`

- [算术运算](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_arit)： `(x * 1.5 + 10) / 2 - y % 100`

- [比较运算](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_comparison)： `x == y`， `x != y`， `x < y`， `x > y`， `x >= y`， `x <= y`， `x lt y`， `x lte y`， `x gt y`， `x gte y`， 等等。。。。。。

- [逻辑操作](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_logicalop)： `!registered && (firstVisit || fromEurope)`

- [内建函数](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_builtin)： `name?upper_case`, `path?ensure_starts_with('/')`

- [方法调用](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_methodcall)： `repeat("What", 3)`

- 处理不存在的值

  ：

  - [默认值](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_missing_default)： `name!"unknown"` 或者 `(user.name)!"unknown"` 或者 `name!` 或者 `(user.name)!`
  - [检测不存在的值](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_missing_test)： `name??` 或者 `(user.name)??`

- [赋值操作](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_assignment)： `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `++`, `--`



原生字符串是一种特殊的字符串。在原生字符串中， 反斜杠和 `${` 没有特殊含义， 它们被视为普通的字符。为了表明字符串是原生字符串， 在开始的引号或单引号之前放置字母`r`

```
${r"${foo}"}
${r"C:\foo\bar"}

output:
${foo}
C:\foo\bar
```



如果插值在 [文本 区](http://freemarker.foofun.cn/dgui_template_overallstructure.html) (也就是说，不在 [字符串表达式](http://freemarker.foofun.cn/dgui_template_exp.html#dgui_template_exp_stringop_interpolation) 中)，如果 [`escape` 指令](http://freemarker.foofun.cn/ref_directive_escape.html#ref.directive.escape) 起作用了，那么将被插入的字符串会被自动转义。如果要生成HTML， 那么强烈建议你利用它来阻止跨站脚本攻击和非格式良好的HTML页面。这里有一个示例：

```
<#escape x as x?html>
  ...
  <p>Title: ${book.title}</p>
  <p>Description: <#noescape>${book.description}</#noescape></p>
  <h2>Comments:</h2>
  <#list comments as comment>
    <div class="comment">
      ${comment}
    </div>
  </#list>
  ...
</#escape>
```



### 自定义指令

```
自定义指令可以有多个参数。
<#macro greet person color>
  <font size="+2" color="${color}">Hello ${person}!</font>
</#macro>

<@greet person="Fred" color="black"/>


```

### 嵌套内容

自定义指令可以嵌套内容，和预定义指令相似：

```
`<#if *...*>*nested content*</#if>`。
```

```
<#macro border>
  <table border=4 cellspacing=0 cellpadding=4><tr><td>
    <#nested>
  </tr></td></table>
</#macro>
<@border>The bordered text</@border>

output:
<table border=4 cellspacing=0 cellpadding=4><tr><td>
    The bordered text
  </td></tr></table>
  
```

`nested` 指令也可以多次被调用，例如：

```
<#macro do_thrice>
  <#nested>
  <#nested>
  <#nested>
</#macro>
<@do_thrice>
  Anything.
</@do_thrice>

output:
<@greet person="Joe">
  Anything.
</@greet>
```

嵌套的内容可以是任意有效的FTL，包含其他的用户自定义指令.

在嵌套的内容中，宏的 [局部变量](http://freemarker.foofun.cn/dgui_misc_var.html) 是不可见的。

```
<#macro repeat count>
  <#local y = "test">
  <#list 1..count as x>
    ${y} ${count}/${x}: <#nested>
  </#list>
</#macro>
<@repeat count=3>${y!"?"} ${x!"?"} ${count!"?"}</@repeat>

output:
    test 3/1: ? ? ?
    test 3/2: ? ? ?
    test 3/3: ? ? ?
```

### 命名空间

```
<#macro copyright date>
  <p>Copyright (C) ${date} Julia Smith. All rights reserved.</p>
</#macro>

<#assign mail = " xxxx@acme.com">

<#import "/lib/my_test.ftl" as my> <#-- the hash called "my" will be the "gate" -->
<@my.copyright date="1999-2002"/>
${my.mail}

Output:
<p>Copyright (C) 1999-2002 Julia Smith. All rights reserved.</p>
xxxx@acme.com
```

### 空白处理

使用compress指令

```
<#compress>
<#assign users = [{"name":"Joe",        "hidden":false},
                  {"name":"James Bond", "hidden":true},
                  {"name":"Julia",      "hidden":false}]>
List of users:
<#list users as user>
  <#if !user.hidden>
  - ${user.name}
  </#if>
</#list>
That's all.
</#compress>

Output:
List of users:
- Joe
- Julia
That's all.

```

在默认情况下，名为 `compress` 的用户自定义指令是可以在数据模型中存在的(由于向下兼容特性)。 这和指令是相同的，除了可以选择设置 `single_line` 参数， 这将会移除所有的介于其中的换行符

```
<@compress single_line=true>...</@compress>
```

