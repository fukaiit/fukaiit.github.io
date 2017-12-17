---
layout:     post
title:      "自适应网页设计"
subtitle:   ""
date:       2017-12-15 20:00:00
categories: [前端]
tags:       [自适应]
header-img: "img/article-bg.jpg"
---

## 一、自适应网页设计基础  
1. **允许网页宽度自动调整**  
首先，在网页头部加入viewport元标签
	```
	<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
	```
2. **不使用绝对宽度**  
不能指定`width: xx px;`，只能指定`width: xx%;`或者`width:auto;`。
3. **使用相对大小的字体**  
字体也不能使用绝对大小（px），而只能使用相对大小（em）。
	```
	body {
		font: normal 100% Helvetica, Arial, sans-serif;
	}
	```
	上面的代码指定，字体大小是页面默认大小的100%，即16像素。
4. **采用流式布局**  
流式布局（float）避免水平滚动条的出现。
5. **选择加载css**  
"自适应网页设计"的核心，就是CSS3引入的Media Query模块。  
自动探测屏幕宽度，然后加载相应的CSS文件。
	```
	<link rel="stylesheet" type="text/css" media="screen and (max-device-width: 400px)" href="tinyScreen.css" />
	```
6. **css的@media规则**
	```
	@media screen and (max-device-width: 400px) {
　　　　.column {
　　　　　　float: none;
　　　　　　width:auto;
　　　　}
　　　　#sidebar {
　　　　　　display:none;
　　　　}
　　}
	```
7. **图片的自适应**  
通常只需要一句话即可：
	```
	img { max-width: 100%;}
	```
对于不支持`max-width`的老版本IE：
	```
	img { width: 100%; }
	```
windows平台缩放图片时，可能出现图像失真现象。这时，可以尝试使用IE的专有命令：
	```
	img { -ms-interpolation-mode: bicubic; }
	```

## 二、<a href="http://www.bootcss.com/" target="_blank">Bootstrap</a>中的自适应设计
### 1. Bootstrap基本模板

	<!DOCTYPE html>
	<html lang="zh-CN">
	  <head>
	    <meta charset="utf-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
	    <title>Bootstrap 101 Template</title>

	    <!-- Bootstrap -->
	    <link href="css/Bootstrap.min.css" rel="stylesheet">

	    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
	    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
	    <!--[if lt IE 9]>
	      <script src="https://cdn.bootcss.com/html5shiv/3.7.3/html5shiv.min.js"></script>
	      <script src="https://cdn.bootcss.com/respond.js/1.4.2/respond.min.js"></script>
	    <![endif]-->
	  </head>
	  <body>
	    <h1>你好，世界！</h1>

	    <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
	    <script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min.js"></script>
	    <!-- Include all compiled plugins (below), or include individual files as needed -->
	    <script src="js/Bootstrap.min.js"></script>
	  </body>
	</html>

> **little tips:**  
将下面的`<meta>`标签加入到页面中，可以让部分国产浏览器默认采用高速模式渲染页面：  
`<meta name="renderer" content="webkit">`  
目前只有360浏览器支持此`<meta>`标签。  

### 2. <a href="http://necolas.github.io/normalize.css/" target="_blank">Normalize.css</a>  
### 3. <a href="https://v3.bootcss.com/css/#grid" target="_blank">栅格系统（栅栏布局）</a>  
1. **媒体查询**    
	```
	@media (max-width: @screen-xs-max) { ... }
	@media (min-width: @screen-sm-min) and (max-width: @screen-sm-max) { ... }
	@media (min-width: @screen-md-min) and (max-width: @screen-md-max) { ... }
	@media (min-width: @screen-lg-min) { ... }
	```
2. **栅格参数**  
	<div class="table-responsive">
	    <table class="table table-hover">
	        <tbody>
	            <tr>
	                <td>&nbsp;</td>
	                <td>超小屏幕 手机 (&lt;768px)</td>
	                <td>小屏幕 平板 (≥768px)</td>
	                <td>中等屏幕 桌面显示器 (≥992px)</td>
	                <td>大屏幕 大桌面显示器 (≥1200px)</td>
	            </tr>
	            <tr>
	                <td>栅格系统行为</td>
	                <td>总是水平排列</td>
	                <td colspan="3">开始是堆叠在一起的，当大于这些阈值时将变为水平排列</td>
	            </tr>
	            <tr>
	                <td>.container 最大宽度</td>
	                <td>None （自动）</td>
	                <td>750px</td>
	                <td>970px</td>
	                <td>1170px</td>
	            </tr>
	            <tr>
	                <td>类前缀</td>
	                <td>.col-xs-</td>
	                <td>.col-sm-</td>
	                <td>.col-md-</td>
	                <td>.col-lg-</td>
	            </tr>
	            <tr>
	                <td>列（column）数</td>
	                <td colspan="4">12</td>
	            </tr>
	            <tr>
	                <td>最大列（column）宽</td>
	                <td>自动</td>
	                <td>~62px</td>
	                <td>~81px</td>
	                <td>~97px</td>
	            </tr>
	            <tr>
	                <td>槽（gutter）宽</td>
	                <td colspan="4">30px （每列左右均有 15px）</td>
	            </tr>
	            <tr>
	                <td>可嵌套</td>
	                <td colspan="4">是</td>
	            </tr>
	            <tr>
	                <td>偏移（Offsets）</td>
	                <td colspan="4">是</td>
	            </tr>
	            <tr>
	                <td>列排序</td>
	                <td colspan="4">是</td>
	            </tr>
	        </tbody>
	    </table>
	</div>
3. **基本结构及具体样式定义**  
	基本结构：
	```
	<div class="container">
		<div class="row">
			<div class="col-xx-4"></div>
			<div class="col-xx-4"></div>
			<div class="col-xx-4"></div>
		</div>
	</div>
	```	
	基本样式：
	```
	.container-fluid {
	  padding-right: 15px;
	  padding-left: 15px;
	  margin-right: auto;
	  margin-left: auto;
	}
	.row {
	  margin-right: -15px;
	  margin-left: -15px;
	}
	.col-xx-i {
	  position: relative;
	  min-height: 1px;
	  padding-right: 15px;
	  padding-left: 15px;

	  float: left;
	  width: xx%；
	}
	```
	列偏移：
	```
	.col-xs-offset-1 {
	  margin-left: 8.33333333%;
	}
	```
	列排序：
	```
	.col-xs-push-1 {
	  left: 8.33333333%;
	}
	.col-xs-pull-1 {
	  right: 8.33333333%;
	}
	```

## 三、网页自适应设计常用结构
### 1. 多列等宽布局

### 2. 一侧固定宽度、一侧自适应两栏布局

### 3. 两栏等高布局


## 参考资料
> 1. <a href="http://www.ruanyifeng.com/blog/2012/05/responsive_web_design.html" target="_blank">阮一峰的网络日志-自适应网页设计（Responsive Web Design）</a>
> 2. <a href="https://v3.bootcss.com/" target="_blank">Bootstrap中文网</a>