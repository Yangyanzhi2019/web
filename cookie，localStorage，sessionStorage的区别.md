# cookie，localStorage，sessionStorage的区别



cookie是在HTML4中使用的给客户端保存数据的，也可以和session配合实现跟踪浏览器用户身份；而webstorage（包括：localStorage和sessionStorage）是在HTML5提出来的，纯粹为了保存数据，不会与服务器端通信。WebStorage两个主要目标：（1）提供一种在cookie之外存储会话数据的路径。（2）提供一种存储大量可以跨会话存在的数据的机制。

 

相同点：

 cookie，localStorage，sessionStorage都是在客户端保存数据的，存储数据的类型：都是字符串。

不同点：

1、生命周期：

1）、cookie如果不设置有效期，那么就是临时存储（存储在内存中），是会话级别的，会话结束后，cookie也就失效了，如果设置了有效期，那么cookie存储在硬盘里，有效期到了，就自动消失了。

2）、localStorage的生命周期是永久的，关闭页面或浏览器之后localStorage中的数据也不会消失。localStorage除非主动删除数据，否则数据永远不会消失。

3）、sessionStorage仅在当前会话下有效。sessionStorage引入了一个“浏览器窗口”的概念，sessionStorage是在同源的窗口中始终存在的数据。只要这个浏览器窗口没有关闭，即使刷新页面或者进入同源另一个页面，数据依然存在。但是sessionStorage在关闭了浏览器窗口后就会被销毁。同时独立的打开同一个窗口同一个页面，sessionStorage也是不一样的。

2、网络流量：cookie的数据每次都会发给服务器端，而localstorage和sessionStorage不会与服务器端通信，纯粹为了保存数据，所以，webstorage更加节约网络流量。

3、大小限制：cookie大小限制在4KB，非常小；localstorage和sessionStorage在5M

4、安全性：WebStorage不会随着HTTP header发送到服务器端，所以安全性相对于cookie来说比较高一些，不会担心截获。

5、使用方便性上：WebStorage提供了一些方法，数据操作比cookie方便；

               setItem (key, value) ——  保存数据，以键值对的方式储存信息。

      　　  getItem (key) ——  获取数据，将键值传入，即可获取到对应的value值。

        　　removeItem (key) ——  删除单个数据，根据键值移除对应的信息。

        　　clear () ——  删除所有的数据

        　　key (index) —— 获取某个索引的key
--------------------- 
作者：田江 
来源：CSDN 
原文：https://blog.csdn.net/jiang7701037/article/details/89118086 
版权声明：本文为博主原创文章，转载请附上博文链接！