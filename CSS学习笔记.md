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
### css边框
border-style：
dotted：定义点状边框
dashed：定义虚线边框
solid：定义实线边框
double：定义双线边框
groove：定义三维沟槽边框。效果取决于 border-color 的值。
ridge：定义三维脊状边框。效果取决于 border-color 的值。
inset：定义三维嵌入边框。效果取决于 border-color 的值。
outset：定义三维突出边框。效果取决于 border-color 的值。
none：定义无边框。
hidden：定义隐藏边框。
```
{设置各边：
    border-top-style:dotted;
    border-right-style:solid;
    border-bottom-style:dotted;
    border-left-style:solid;
}
```
border-width 属性为边框指定宽度
border-color属性用于设置边框的颜色

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
### 继承
**会继承的属性（大部分和文本相关）**  
这些属性天生就会 “遗传” 给子元素：  
color（文字颜色）  
font-family（字体）、font-size（字号）、font-weight（加粗）  
line-height（行高）、text-align（文本对齐）  
list-style（列表样式）  
visibility（可见性）  
**不会继承的属性（大部分和布局、盒子相关）**  
这些属性只作用在当前元素，不会传给子元素，你截图里的 margin 就属于这类：  
margin（外边距）、padding（内边距）、border（边框）  
width/height（宽高）  
background（背景）  
position（定位）、float（浮动）  
display（显示模式）

### display 全属性 超直白解释（一秒看懂）
**基础布局**  
block：独占一行，像方块一样竖着排，可以设置宽高、内外边距  
inline：只能放文字、图片、链接，不能设置宽高、上下内外边距  
inline-block：像文字一样排列，但可以设置宽高、边距，最常用！  
**弹性布局**  
flex：父元素用，让子元素自动横向 / 纵向排列，超级好用  
inline-flex：和 flex 一样排列，但自身不独占一行   
**网格布局**  
grid：父元素用，像表格一样分格子布局，适合复杂页面  
inline-grid：和 grid 一样分栏，但自身不独占一行  
**清除浮动、稳定布局**  
flow-root：创建稳定块容器，自动清除内部浮动，不影响外部布局  
**显示 / 隐藏**  
none:直接隐藏元素，不占位置、不显示、不占空间  
contents：只保留子元素，自身容器消失，像没有这个标签一样
### 全貌代码
|代码	|作用|	大白话解释	|开发意义|
|---|----|---|----|
|*	|通配符选择器	|选中网页里所有 HTML 元素|	给全站元素统一设置基础规则，不用逐个标签写样式|
|margin: 0;|	清除外边距	|把所有元素「盒子外面的空隙」清零	|消除浏览器给`<body>、<h1>`等标签加的默认边距，避免页面出现白边、排版错位|
|padding: 0;|	清除内边距|	把所有元素「盒子里面的空隙」清零	|消除浏览器默认内边距，让内容紧贴元素边缘，精准控制布局|
|box-sizing: border-box;	|统一盒模型	|元素的宽高 = 内容 + 内边距 + 边框，不会撑大盒子	|解决「加内边距 / 边框就把盒子撑大、布局乱掉」的问题，是布局稳定的核心|
|font-family: "Microsoft YaHei", Arial, sans-serif;|	统一全局字体|	按优先级设置字体：1. 优先用「微软雅黑」（中文友好）2. 无则用「Arial」（英文 / 数字友好）3. 无则用系统默认无衬线字体|	保证不同设备、浏览器打开网站，字体显示一致，不会乱码、错乱|
  

1. 背景图适配
组合：background-size + background-position
释义：单独只能改大小或改位置，容易变形；组合使用，背景图不变形、居中完整展示。
用途：Banner、页面大图背景。
2. 渐变背景
组合：background + linear-gradient()
释义：单纯 background 只有纯色；搭配渐变函数，才能做出双色柔和过渡，增加页面层次感。
用途：标题栏、按钮、板块美化。
3. 盒模型稳定布局
组合：宽高 + padding/border + box-sizing: border-box
释义：只设宽高，内边距 / 边框会撑大盒子；组合后，边框和内边距算入盒子内部，布局不乱。
用途：全局所有模块通用规范。
4. 清除浮动
组合：float + overflow: hidden
释义：单独浮动会导致父盒子高度塌陷、排版错乱；组合使用，恢复父元素高度，布局稳定。
用途：图文排列、简易多列布局。
5. 容器整体水平居中
组合：固定宽度 + margin: 0 auto
释义：只写居中代码无效，必须先限制宽度；组合实现网页主体板块居中。
用途：网页版心、内容大容器。
6. 弹性基础居中
组合：display: flex + justify-content + align-items
释义：只开弹性只会横向排列；三者搭配，实现内容水平 + 垂直双向居中。
用途：导航、卡片、模块内容居中。
7. 弹性自动换行
组合：display: flex + flex-wrap: wrap
释义：只开弹性会挤在一行、溢出错乱；组合后，空间不足自动换行，简单适配窗口。
用途：招新卡片、多列表单。
8. 父子精准定位
组合：父position:relative + 子position:absolute
释义：单独绝对定位会随意乱跑；父级当参照物，子元素可以固定在盒子任意角落。
用途：角标、叠加文字、装饰小元素。
第二部分 图片 & 文字排版类（9–14）
9. 图片等比不变形
组合：固定宽高 + object-fit
释义：只设尺寸会强行拉伸图片；组合使用，自动裁剪保留原图比例。
用途：网站配图、卡片图片。
10. 单行文字完全居中
组合：text-align: center + line-height
释义：text-align 只管左右居中；行高和盒子高度一致，实现上下居中，组合才完美对齐。
用途：导航文字、按钮、标题。
11. 文字溢出省略号
组合：white-space:nowrap + overflow:hidden + text-overflow:ellipsis
释义：三个缺一不可；强制不换行、隐藏超出文字、自动显示省略号。
用途：卡片标题、过长文本缩略。
12. 超链接美化
组合：text-decoration:none + 自定义color
释义：链接默认自带下划线和蓝色字体；组合去除下划线、统一页面文字颜色。
用途：导航栏所有 a 链接。
13. 列表清除默认样式
组合：list-style:none + margin:0 + padding:0
释义：ul/li 自带圆点和空白间距；三者搭配，清空默认样式，用来做整齐导航。
14. 字体统一美化
组合：font-size + font-weight + font-family
释义：单独改大小排版杂乱；组合统一字号、粗细、字体，整体页面风格整洁。
第三部分 美化、交互、进阶适配（15–20）
15. 卡片质感美化
组合：border-radius + box-shadow
释义：单独圆角单调、单独阴影生硬；组合搭配，卡片更立体柔和，提升颜值。
16. 边框正常显示
组合：border-width + border-style + border-color
释义：边框需要同时具备粗细、线条样式、颜色，三个条件缺一不可，才能正常显示。
17. 按钮悬浮交互
组合：:hover 伪类 + cursor:pointer
释义：hover 负责变色美化，pointer 让鼠标变成小手；组合提醒用户此处可以点击。
18. 绝对定位万能居中
组合：left:50% + top:50% + transform:translate()
释义：只靠定位只能偏中心；搭配位移，实现任意元素精准正中间摆放。
19. 内容隐藏两种搭配
组合：display:none / visibility:hidden
释义：前者彻底消失不占空间，后者看不见但保留空白位置；根据需求搭配选用。
20. 装饰元素锁定
组合：user-select:none + pointer-events:none
释义：禁止选中文字、禁止鼠标点击；用来保护背景装饰、水印、纯美化元素。
