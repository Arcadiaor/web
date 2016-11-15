# webcss中的position:relative和absolute 属性
     因为最近要用Jquery做一些基本的特效，本来学的不是很深的CSS知识更是捉襟见肘，惭愧啊！

     css初学者最怕的就是这些问题，繁琐，API文档上写的也过于官方，看了好几遍不是很明白。下面引用官方的说明文档：

语法：

position : static | absolute | fixed | relative

取值：

static :默认值。无特殊定位，对象遵循HTML定位规则

absolute :将对象从文档流中拖出，使用 left ， right ， top ， bottom 等属性相对于其最接近的一个最有定位设置的父对象进行绝对定位。如果不存在这样的父对象，则依据 body 对象。而其层叠通过 z-index 属性定义

fixed :未支持。对象定位遵从绝对(absolute)方式。但是要遵守一些规范

relative :对象不可层叠，但将依据 left ， right ， top ， bottom 等属性在正常文档流中偏移位置

     对于文档中所说的几个属性，除了relative，其它的一试，就效果出来了，对于个relative，真是难理解。

     通过资料加上网上一些大神的理解，大致上有了一下总结，也算是理解了吧！

     position的默认值是static，（也就是说对于任意一个元素，如果没有定义它的position属性，那么它的position:static） 
     如果你想让DIV #demo里的一个div#sub相对于#demo定位在右上角的某个地方，应该给#demo相对定位，#sub绝对定位。 
     absolute是相对于自己最近的父元素来定位的，如果你不给#demo相对定位，那么#sub的绝对定位就是相对于body来定位的。 
     relative是相对于自己来定位的，例如：#demo{position:relative;top:-50px;},这时#demo会在相对于它原来的位置上移50px。 
       另：relative 不脱离文档流，absolute 脱离文档流。也就是说：relative 的元素尽管表面上看到它偏离了原来的位置，但它实际上在文档流中还是没变。absolute的元素不仅位置改变了，同时也脱离了文档流。 

        具体可以参考网上的一个例子，下面给出代码：

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8">
<title>position</title>
<style type="text/css">
	<!--
	body{
		font-size:12px;
		margin:0 auto;
	}

	div#demo{
		position:relative;
		border:1px solid #000;
		margin:50px;
		top:-50px;
		line-height:18px;
		overflow:hidden;
		clear:both;
		height:1%;
	}

	div#sub{
		position:absolute;
		right:10px;
		top:10px;
	}

	div.relative{
		position:relative;
		left:400px;
		top:-20px;
	}

	div.static,div.fixed,div.absolute,div.relative{
		width:300px;	
	}

	div.static{
		background-color:#bbb;
		position:static;
	}

	div.fixed{
		background-color:#ffc0cb;
	}

	div.absolute{
		background-color:#b0c4de;
	}

	div.relative{
		background-color:#ffe4e1;
	}
	-->
</style>
</head>
<body>
	<div id="demo">
		<div class="static">static: 默认值。无特殊定位，对象遵循HTML定位规则 </div>
		<div id="sub" class="absolute">absolute: 将对象从文档流中拖出,使用left,right,top,bottom 等属性
                                  相对于其最接近的一个最有定位设置的父对象进行绝对定位。
                                  如果不存在这样的父对象,则依据body对象。而其层叠通过z-index属性定义 
                 </div>
		<div class="fixed">fixed:未支持。对象定位遵从绝对(absolute)方式。但是要遵守一些规范 
                </div>
		<div class="relative">relative:对象不可层叠，但将依据 left,right,top,bottom 等属性
                                             在正常文档流中偏移位置
                 </div>
	</div>
</body>
</html>
