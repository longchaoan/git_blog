---
title: 个人JS学习笔记
---

``` bash
$ "Welcome"
```

### 一、parentNode

①parentNode：获取选中元素的父节点
//获取ID的父节点
ID.parentNode.style.display='none';

### 二、nextSibling，nextElementSibling，previousSibling，previousElementSibling
①nextSibling：上一个兄弟节点	→	只有IE678认识
②nextElementSibling：上一个兄弟节点		→	其他浏览器认识，所以要结合①②
//兼容写法,要先写正常浏览器的再写IE678的，否则报错
var obj=ID.nextElementSibling || ID.nextSibling;
③④：上一个兄弟节点，不兼容问题同上

### 三、fistChild，fistElementChild，lastChild，fistElementChild
①②：第一个子节点
③④：最后一个子节点
//同样是有兼容性问题，解决方法同第二标题
//这种方法很少用，因为空格也算是第一个子节点

### 四、childNodes，children
①childNodes：获取选中元素下的所有子节点，换行也包括在其中，可以通过nodeType==1过滤所有的元素出来，遍历
②children：获取选中的元素的子节点，没有兼容问题，这个最好用，IE8下会包含注释，所以不能有注释

### 五、createElement()，appendChild()，insetBefore()，removeChild()，cloneNode()
①creatElement()：创建节点
②appendChild()：向选中元素的最后添加子节点
③insertBefore()：向选中元素前面插入节点，有两个参数：插入的节点    插入谁的前面（children[0]：第一个子节点，表示永远插入第一个）
④removeChild()：移除子节点
⑤cloneNode(true)：复制节点，传入true复制本盒子和盒子中的子节点，false只复制本盒子

### 六、getAttribute()，setAttribute()，removeAttribute()
①getAttribute()：获得选中元素的属性
②setAttribute()：设置选中元素的属性
③removeAttribute()：删除选中元素的属性

### 七、Date对象
①getDate()	获取日1-31
②getDay()	获取星期0-6
③getMonth()		获取月0-11
④getFullYear()		获取完整的年份
⑤getHours()		获取小时0-23
⑥getMinutes()	获取分钟0-59
⑦getSeconds()	获取秒0-59
⑧getMilliseconds()		获取当前的毫秒
⑨getTime()	返回累计毫秒数
//指定某个时间
var time=new Date("2016/11/30 00:39:00");

### 八、charAt()，charCodeAt()，indexOf()，lastIndexOf()
①charAt()：根据索引号找出对应的值
②charCodeAt()：根据索引号返回对应值的uniCode编码
③indexOf()：根据字符返回索引号，从0开始找到第一个，只找一次
④lastIndexOf()：根据字符从后面开始找

### 九、encodeURIComponent()，decodeURIComponent()
①encodeURIComponent("字符串")：把字符作为URI组件进行编码
②decodeURIComponent()：把字符作为URI组件进行解码

### 十、concat()，slice()，substr()，substring()，toFixed()，toUpperCase()
①concat()：连接两个字符串
②slice(3,5)：截取字符串，从哪个索引开始，到哪个索引结束
③substr(3,5)：截取字符串，从哪个索引开始，截取多少个数量
④substring()：同slice()原理一样，但是总是把最小的参数作为起始索引
⑤toFixed(2)：保留多少位小数
⑥toUpperCase()：将选中的字符串转为大写

### 十一、缓冲公式：learder=learder+(target-learder) /10 
//learder：开始位置		target：结束位置

### 十二、offsetWidth，offsetHeight，offsetLeft，offsetTop，offsetParent
①offsetWidth：获取对象的宽度，width+border+padding的宽度
②offsetHeight：获取对象的高度，同上
④offsetLeft：获取对象到左边的距离，父级有定位就到到定位父亲的距离
⑤offsetTop：获取对象到顶部的距离，同上
⑥offsetParent：找到对象的定位父亲

### 十三、事件对象event
①event.clientX：获取鼠标到浏览器的X坐标（可视区的）
②event.clientY：获取鼠标到浏览器Y坐标
③event.screenX：获取鼠标到整个屏幕的X坐标
④event.screenY：同上
⑤pageX：获取鼠标到文档的坐标，有滚动条时的坐标    //IE678不兼容啊
⑥pageY：同上
//兼容性写法：
//标准下支持直接传入使用e，IE678下不支持直接传入使用window.event
var  ev=e || window.event

### 十四、清除选中的内容，文字，就是无法选取的意思
window.getSelection?window.getSelection().removeAllRanges():document.selection.empty();

### 十五、scrollTop，scrollLeft，pageYOffset，pageXOffset，scrollTo()
①scrollTop：滚动的距离
②pageYOffset：同上，但是只有IE9+和最新的浏览器认识
③scrollTo(15,15)：滚动到指定的坐标
兼容写法：
//第一IE9+以上支持，第二除了谷歌都支持，第三谷歌支持，第四所有都不支持时为0开始
var scrollTop=window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop || 0 ;

### 十六、窗口事件
①window.onscroll=function(){}     窗体滚动事件
②window.onresize=function(){}     窗体改变大小事件

### 十七、window.screen.width：返回电脑的分辨率

### 十八、阻止冒泡
①event.stopPropagation()：标准浏览器下的处理方法
②event.cancelBubble=true：IE678下的处理方法
兼容写法：
var ev=event || window.event;
if(ev && ev.stopPropagation){
ev.stopPropagation();
}else{
ev.cancelBubble=true;
}

### 十九、event.target.id，event.srcElement.id
①event.target.id：获取当前对象的ID   //标准浏览器下的
②event.srcElement.id：同上		//IE678下的
兼容写法：
var targetId = event.target ? event.target.id : event.srcElement.id;

### 二十、window.getSelection()，document.selection.ceateRange()
①window.getSelection()：标准浏览器下获取用户选中的内容
②document.selection.createRange().text：IE下用户选中的文字
兼容写法：
if(window.getSelection){
txt=window.getSelection().toString();
}else{
txt=document.selection.createRange().text;
}

### 二十一、Math.ceil()，Math.floor()，Math.abs()，Math.round()
①Math.ceil()：向上取整		1.1→2
②Math.floor()：向下取整		1.9→1
③Math.abs()：绝对值
④Math.round()：四舍五入

### 二十二、遍历json：
for(var k in json){
k：属性
json[k]：属性的值
}

### 二十三、prototype	原型
//扩展方法，所有的数组都能使用这个扩展方法
Array.prototype.run=function(){};

### 二十四、数组的操作
①push()：向数组后面添加一个或者多个元素
②unshift()：向数组前面添加一个或者多个元素
③pop()：删除数组的最后一个元素
④shift()：删除数组的第一个元素
⑤concat()：连接两个数组
⑥join("-")：将数组转为字符串，“-”连接每个值
⑦split("-")：将一个字符串分割成数组

### 二十五、屏幕可视区的兼容写法
var clientWidth=window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth || 0 ;

### 二十六、检测屏幕宽度，分辨率
window.screen.Width;




