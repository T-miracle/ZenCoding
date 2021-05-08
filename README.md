# zenCoding入门到精通：提高html编码速度

## zenCoding是什么

**zenCoding**是一款快速编写HTML,XML,XSL（或其他格式化语言）的编辑器插件，这个插件的实现了用缩写方式完成大量重复的书写工作。

他的核心是一个强大的缩写引擎，掌握这些缩写技巧，给我们的编写代码带来极高的编写效率。

现在主流的IDE（如：IntelliJ IDEA、VSCode、HBuilderX等）都默认支持了zenCoding，即使有一些编辑器（如：sublime Text、Notepad++等）不支持，也可以通过安装插件的方式，使其支持。

## 语法

### E：element，元素

例如：p、ul等标签元素

缩写：

```text
p
```

在html中写入**p**，按下Tab键（vscode中为自动提示），结果为：

```html
<p></p>
```

### *：数量

缩写：

```text
a*3
```

结果为：

```html
<a href=""></a>
<a href=""></a>
<a href=""></a>
```

### >：后代

缩写：

```text
ul>li
```

结果：

```html
<ul>
    <li></li>
</ul>
```

### +：兄弟

缩写：

```text
h1+h2+h3
```

结果：

```html
<h1></h1>
<h2></h2>
<h3></h3>
```

### ^：上级

缩写：

```text
div>span^p
```

结果：

```html
<div><span></span></div>
<p></p>
```

**p**元素会向上提升一级，与**div**持平，允许多个 `^` ：

缩写：

```text
div>p>span^^bq
```

结果：

```html
<div>
    <p><span></span></p>
</div>
<blockquote></blockquote>
```

### ()：分组

缩写：

```text
div>(p>span)*3
```

结果：

```html
<div>
    <p><span></span></p>
    <p><span></span></p>
    <p><span></span></p>
</div>
```

### #：id属性

缩写：

```text
div#demo
```

结果：

```html
<div id="demo"></div>
```

### .：class属性

缩写：

```text
div.demo
```

结果：

```html
<div class="demo"></div>
```

### $：自增符号

缩写：

```text
.demo>#box$*3
```

结果：

```html
<div class="demo">
    <div id="box1"></div>
    <div id="box2"></div>
    <div id="box3"></div>
</div>
```

>允许同时使用多个 `$`

缩写：

```text
ul>li.num$$$*3
```

结果：

```html
<ul>
    <li class="num001"></li>
    <li class="num002"></li>
    <li class="num003"></li>
</ul>
```

>可以使用 `@` 定义初始值

缩写：

```text
ul>li.num$@20*3
```

结果：

```html
<ul>
    <li class="num20"></li>
    <li class="num21"></li>
    <li class="num22"></li>
</ul>
```

### []：自定义符号

缩写：

```text
a[id='btn' class='qwq' href='github.com']
```

结果：

```html
<a href="github.com" id="btn" class="qwq"></a>
```

### {}：文本

缩写：

```text
p{text$}*3
```

结果：

```html
<p>text1</p>
<p>text2</p>
<p>text3</p>
```

### :：引用

缩写：

```text
a:link
```

结果：

```html
<a href="http://"></a>
```

引用功能大多不常用，更多方式可自行探索。

### 隐式标签

>E之前无关联元素，E默认为div

缩写：

```text
.qqq#ppp
```

结果：

```html
<div class="qqq" id="ppp"></div>
```

>E之前有关联元素，E默认匹配相应元素

缩写：

```text
ul>.idx$*3
```

结果：

```html
<ul>
    <li class="idx1"></li>
    <li class="idx2"></li>
    <li class="idx3"></li>
</ul>
```

缩写：

```text
table>.row*2>.col*3
```

结果：

```html
<table>
    <tr class="row">
        <td class="col"></td>
        <td class="col"></td>
        <td class="col"></td>
    </tr>
    <tr class="row">
        <td class="col"></td>
        <td class="col"></td>
        <td class="col"></td>
    </tr>
</table>
```

>感叹号

缩写：

```text
!
```

结果：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

### 模拟文本

缩写：

```text
lorem
```

结果：

```text
Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt, voluptate amet. At possimus porro molestiae tenetur dignissimos dolores minima nihil. Enim qui quo similique ratione fugiat assumenda vero aut at?
```

>后面添加数字，代表生成单词的个数

缩写：

```text
p>lorem3
```

结果：

```html
<p>Lorem, ipsum dolor.</p>
```

### 包装文本

vscode中写法如下（其他编辑器自行使用相应快捷键）：

缩写：

```text
text1
text2
text3
```

选中文本，按下`ctrl+shift+p`打开命令窗口输入**ewrap**

选择Emmet：使用缩写包围个别行（Wrap Individual Lines with Abbreviation）选项

输入: 

```text
ul>li*
```

结果：

```html
<ul>
    <li>text1</li>
    <li>text2</li>
    <li>text3</li>
</ul>
```

### 复杂组合示例

缩写：

```text
.tx>h1#txt+(span{text-$@16})*4
```

结果：

```html
<div class="tx">
    <h1 id="txt"></h1>
    <span>text-16</span>
    <span>text-17</span>
    <span>text-18</span>
    <span>text-19</span>
</div>
```

## 官方手册

[点击前往](https://docs.emmet.io/cheat-sheet/)
