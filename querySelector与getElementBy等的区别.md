# querySelector与getElementBy等的区别

获取元素DOM对象有很多种方法，以前一直在用getElementById和getElementsByTagName等，现在对这些方法和querySelector做一个总结． 
常见的获取元素的方法有3种，分别是通过元素ID、通过标签名字和通过类名字来获取。 
DOM提供了一个名为getElementById的方法，这个方法将返回一个与之对应id属性的节点对象，它是document对象特有的函数，只能通过其来调用该方法，使用方法如下:document.getElementById('idName');

getElementsByTagName方法返回一个对象数组（准确的说是HTMLCollection集合）,返回元素的顺序是它们在文档中的顺序,传递给 getElementsByTagName() 方法的字符串可以不区分大小写,使用方法如下:document.getElementsByTagName(tagName);

DOM还提供了getElementsByClassName方法来获取指定class名的元素,该方法返回文档中所有指定类名的元素集合，作为 NodeList 对象。NodeList 对象代表一个有顺序的节点列表。NodeList 对象 我们可通过节点列表中的节点索引号来访问列表中的节点(索引号由0开始), 所以有时使用时要指定下标，使用方法如下:document.getElementsByClassName('className');

querySelector() 方法返回匹配指定 CSS 选择器元素的第一个子元素 。 该方法只返回匹配指定选择器的第一个元素。如果要返回所有匹配元素，需要使用 querySelectorAll() 方法替代．

由于querySelector是按css规范来实现的，所以它传入的字符串中第一个字符不能是数字.

最后再根据查询的资料总结一下： 
query选择符选出来的元素及元素数组是静态的，而getElement这种方法选出的元素是动态的。静态的就是说选出的所有元素的数组，不会随着文档操作而改变． 
在使用的时候getElement这种方法性能比较好，query选择符则比较方便．
--------------------- 
作者：levinhax 
来源：CSDN 
原文：https://blog.csdn.net/levinhax/article/details/71274456 
版权声明：本文为博主原创文章，转载请附上博文链接！