# css清除浮动带来影响的方法

清除浮动

1.结尾处加空div标签 clear:both 
2.父级div定义 伪类:after
	display:block;           
 	clear:both;
 	content:""; 
3.父级div定义 overflow:hidden  缺点：不能和position配合使用，因为超出的尺寸的会被隐藏。

4.父级div定义 overflow:auto    这个不能用滚动条，所以不推荐使用哦！

5.父级div 也一起浮动  会产生新的浮动问题。不推荐使用，只作了解。

6.父级div定义 display:table  会产生新的未知问题。不推荐使用，只作了解。

7.结尾处加 br标签 clear:both  与1一样，这里只要是块元素都是可以的;
