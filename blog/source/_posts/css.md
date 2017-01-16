---
title: IE678下常见的兼容性问题及解决方法
---


 `常见问题及解决方法`


* 1、IE6双边距bug：IE6下块元素float会出现margin双边距问题，解决办法设为内联元素，display:inline;或者使用padding代替margin
* 2、IE6，IE7下float后li之间出现间隙，使用vertical-align:top解决
* 3、IE6，IE7下img有下边距，使用border：none;vertical-align:top解决
* 4、滤镜：opacity：0~1，IE8以下不支持，使用它的私有滤镜，filter：alpha(opacity(0~100))
* 5、IE6的最小边框问题，小于19像素当19像素处理，使用overflower:hidden
* 6、在IE6，7下，子元素有相对定位的话，父级的overflow包不住子元素
*	解决办法: 给父级也加相对定位

`个人开发过程遇到的问题总结：`

* 1、png图片处理后IE6下出现边线，修改图片格式解决，可以将png格式图片改为gif，jpeg
* 2、img图片IE6下鼠标经过无法出现边框，给a：hover加｛zoom1｝
* 3、line-height无法居中img，使用只能使用padding解决
* 4、IE6下li，dl无法float，给li，dl加宽度


`$ IE6无法正常显示png格式的图片`

可以通过一个js库解决。
使用方法：
	1、引入DD_belatedPNG_0.0.8a.js包。下载地址：还未上传github，待更新。
	2、加上条件注释语句，只有IE6下才加载DD_belatedPNG_0.0.8a.js这个包，其他浏览器无法识别，这样可以有效的提高页面在其他浏览器的性能
	3、写于执行语句，* 代表选择所有的png图片，也可以写入单个png图片，填入对应的类名即可。
	```javascript
	<!--[if IE 6]>
		<script src="js/DD_belatedPNG_0.0.8a.js" type="text/javascript" charset="utf-8"></script>
		<script src="./js/DD_belatedPNG_0.0.8a.js"></script>
		<script>
		DD_belatedPNG.fix('*');
		</script>
	<![endif]-->
	```
##### 以上笔记仅个人学习笔记，未作详细解释。




