### css的引入样式
```
行内样式：
<div style="color:red;">文字</div>
```
直接把样式写在 HTML 标签内部，用 style="属性:值;"
**优点:**
写起来最快
优先级最高（会覆盖其他样式）
**缺点:**
代码乱，难以维护
不能复用（每个标签都要写一遍）
不符合 “结构样式分离” 原则
项目大了完全没法用
```
内部样式表
<head>
  <style>
    div {
      color: blue;
    }
  </style>
</head>
```
写在 `<head>` 里的 `<style>` 标签中，只对当前页面生效。
**优点：**
样式和结构分开
比行内样式干净
适合单页面小项目
**缺点：**
不能跨页面复用（A 页面写的，B 页面用不了）
页面代码会变多
```
外部样式表
div {
  color: green;
}
<link rel="stylesheet" href="style.css">
```
**优点：**
结构与样式完全分离（最标准）
可以复用（所有页面都能引同一个 css）
代码整洁、易维护、易扩展
浏览器会缓存，加载更快
**缺点：**
需要新建文件，稍微麻烦一点点
**优先级：**
行内样式 > 内部样式 > 外部样式
```
语法规则
选择器 {
  属性名: 属性值; ( 必须加分号 )
  width: 100px;
}
```
### 选择器
**基础选择器**
```
元素选择器：
div {
  color: red;
}
```
写法：直接写标签名
作用：选中页面里所有这个标签
例子：
p {} → 所有段落
span {} → 所有 span
特点：范围大，改一个全站生效
```
类选择器
css：
.box {
  font-size: 20px;
}
html:
<div class="box">我会变大</div>
```
作用：给一类标签统一样式
```
ID选择器
css:
#header {
  background: blue;
}
html:
<div id="header">头部</div>
```
规则：同一个 ID 一个页面只能用一次,优先级高，一般不用来写样式
**复合选择器**
后代选择器：选中 class="box" 里面所有的 p
不管嵌套多少层都能选中
子元素选择器
只选 .box 的直接儿子 p
孙子、重孙都不选
**并集选择器：**
```
div, p, span, .box {
  color: pink;
}
```
同时给这些标签 / 类设置同一样式
用来统一颜色、字体很方便
**伪类选择器**
```
hover 鼠标悬浮
css
a:hover {
  color: orange;
}
鼠标放上去才生效，按钮、链接必用
```
```
focus 输入框聚焦
css
input:focus {
  border: 2px solid blue;
}
点进输入框时样式变化
```
```
first-child 第一个子元素
css
div:first-child {
  font-weight: bold;
}
选中父元素里第一个子元素
```
**优先级：**!important > 行内 > ID > 类 > 标签 > *
### 常用文本样式
**文字颜色:**
color: red; ( 英文 / 十六进制 #fff / rgb(0,0,0) )
**字体:**
font-size: 16px;    (字号)
font-weight: 700;   ( 加粗 100-900 )
font-family: 微软雅黑; ( 字体 )
line-height: 1.5;   (行高（垂直居中神器）)
text-align: center; ( 水平居中 )  
**文本修饰:**
text-decoration: none; (去掉下划线 )
text-indent: 2em;      ( 首行缩进 )
### 盒子模型
```
内容区:
width: 200px;
height: 200px;

内边距（内容和边框之间）:
padding: 10px; (上右下左 )

边框距：
border: 1px solid #000;

外边距：
margin: 0 auto; （水平居中）
标准盒子总宽度 = width + padding + border
```
### 元素显示模式
```
1. 块级元素（独占一行）
div / p / h1~h6 / ul / li
可设置宽高
独占一行
2. 行内元素（不换行）
span / a / img / input
不能设置宽高
同行显示
3. 转换模式
css
display: block;    ( 转块级 )
display: inline;   ( 转行内 )
display: inline-block; (行内块（常用）)
display: none;     ( 隐藏元素（不占位置）)
```
### 背景样式
```
background-color: #f5f5f5; (背景色)
background-image: url(1.jpg);(背景图)
background-repeat: no-repeat;(不重复)
background-position: center; (居中)
background-size: cover; (覆盖盒子)
```
### 浮动
```
作用
让块级元素同行显示
用法
css:
float: left;  (左浮动)
float: right; (右浮动 )
浮动问题：父元素塌陷
清除浮动
css:
(万能清除法 )
.clearfix::after {
  content: "";
  display: block;
  clear: both;
  height: 0;
  visibility: hidden;
}
```
### 定位
```
静态定位（默认）
position: static;
相对定位（不脱标）
css
position: relative;
top: 10px; (相对自己原来位置移动)
绝对定位（脱标，常用）
css
position: absolute;
top: 0;
left: 0;
(子绝父相：子元素绝对，父元素相对)
固定定位（固定在屏幕）
css
position: fixed;
层级
z-index: 999; 数值越大越在上层
```
### 居中方案
```
水平居中：
行内元素：text-align: center
块级元素：margin: 0 auto
绝对定位：left: 50%; transform: translateX(-50%)
垂直居中：
单行文字：line-height = 盒子高度
绝对定位：top: 50%; transform: translateY(-50%)
水平 + 垂直居中
css
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
```
### Flex布局
给父元素加：
css
display: flex;
父元素属性
css
主轴方向：
flex-direction: row; （默认 横向）
flex-direction: column; （纵向）

水平对齐
justify-content: center; （居中）
justify-content: space-between; （两端对齐）

垂直对齐
align-items: center; （垂直居中）

换行
flex-wrap: wrap;
子元素属性
css
flex: 1; （平分剩余空间）
### 过度与活动
```过渡（hover 动效）
css
transition: all 0.3s ease;
动画
css
@keyframes move {
  0% { transform: translateX(0); }
  100% { transform: translateX(100px); }
}

div {
  animation: move 1s infinite;
}
```


