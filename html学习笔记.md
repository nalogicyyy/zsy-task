### html骨架
    <!DOCTYPE html>（声明，不属于标签层级）
    <html lang="zh-CN">（根标签，包裹所有内容）
    <head>> （头部，元数据，不显示）
    <meta charset="UTF-8">
    <title>标题</title>
    </head>
    <body>
        网页内容 （主体，所有可视内容）
    </body>
    </html>
### HTML 注释与排版标签
注释：`<!-- 注释内容 -->`，快捷键 Ctrl + /
标题标签：`<h1> ~ <h6> `逐级变小，h1 一个页面只用一次
段落标签：`<p>一段文字</p>`
换行：`<br> 单标签`
水平线：`<hr> 单标签`
### 文本格式化标签
加粗：`<strong> 或 <b>`（推荐 strong，语义更强）
倾斜：`<em> 或 <i>`
删除线：`<del> 或 <s>`
下划线：`<ins> 或 <u>`
### 图像标签
```<img src="图片路径" alt="图片加载失败显示文字" title="鼠标悬停文字" width="宽度" height="高度">```
src：必须写，图片路径
alt：图片无法显示时的替换文本
只改宽或高，图片等比缩放
### 路径
相对路径
当前目录：./ 或直接写文件名
上级目录：../
绝对路径：本地完整盘符 / 网络完整 URL
### 超链接标签`<a>`
`<a href="跳转地址" target="_blank">文字/图片</a>`
href：# 表示空链接
target="_blank"：新窗口打开
可以给图片加链接：`<a><img></a>`
### 音频标签
`<audio src="音频路径" controls autoplay muted>`
controls：显示播放控件
autoplay：自动播放（需配合 muted 静音
### 视频标签 `<video>`
`<video src="视频路径" controls autoplay muted loop></video>`
loop：循环播放
### 列表标签
**无序列表**
    
    <ul>
    <li>列表项1</li>
    <li>列表项2</li>
    </ul>
ul 里面只能放 li，li 里面可以放任意内容

**有序列表**  
    
    <ol>
    <li>第一项</li>
    <li>第二项</li>
    </ol>

**自定义列表**

    <dl>
    <dt>标题</dt>
    <dd>描述1</dd>
    <dd>描述2</dd>
    </dl>

### 布局标签 div 和 span
`<div>`：块级元素，独占一行，用来装大内容
`<span>`：行内元素，一行可以多个，装小文字 / 小内容
### 特殊字符

    空格：&nbsp;
    小于号 <：&lt;
    大于号 >：&gt;
    