# Node.js 基础复习与 Express

## 1.什么nodeJS

### 1.概念

#### 	nodeJS Node.js是一个基于Chrome V8引擎(编译成原生机器码)的让JavaScript运行在服务器端的运行环境，它让JavaScript的触角伸到了服务器端。

###2.nodeJS特性

#### 1.单线程 NodeJS不会为每个连接客户创造一个新的线程,仅用一个线程!

![1560764483545](C:\Users\ADMINI~1\AppData\Local\Temp\1560764483545.png)

#### 2.非阻塞式IO

##### 	NodeJS在访问高IO操作后不会等待其完成，而是立即去执行其他代码，操作完成后会使用回调函数返回保证高效的利用当前线程的cpu 不造成硬件浪费

#### 3.事件驱动

- [ ] ##### 	[事件驱动 通过事件来驱动整个程序的进行]()  

##### 	 由于是单线程，所以把高io的操作 就会移动到事件队列中等待完成，完成后通过回调函数的方式返回给线程来进行处理。这个循环处理的过程称之为：事件环

## 2.nodeJS模块

### 1.nodeJS模块书写

#### 	模块书写 js文件因为作用域的问题，变量和函数只能在当前文件中进行使用，如果在当前模块外引用，必须使用exports/module.exports(特定的类型使用)让这些内容进行暴漏，使用的时候使用require来进行引入。

### 2.nodeJS模块优点

#### 	模块有优点：减少代码重复，提高利用率划分功能，方便管理方便使用第三方模块

### 3.基本服务器创建过程HTTP模块

#### 	http模块 是node重要的核心模块

![1560765042223](C:\Users\ADMINI~1\AppData\Local\Temp\1560765042223.png)

### 4.URL模块

#### 1.路由  路由就是根据对不同的请求，找到不同的代码完成处理

#### 	通过URL路径来区分不同的请求，从而找到不同的功能模块来进行执行。

## 2.Express

### 1.Express基本概念

##### 	express 是一个简洁而灵活的 node.js Web应用框架, 提供了一系列强大特性和丰富的 HTTP 工具

##### 	功能：扩展了web所需要的基本功能

##### 		丰富了HTTP工具

##### 		可以快速搭建一个网站

### 2.Express----安装

#### 	1.初始化 npm init

#### 	2.npm install --save express

### 3.Express 处理静态资源

#### 	使用中间件配合app.use(express.static(path.join(__dirname, “文件夹名”)));

### 4.Express  路由与中间件

#### 	1.Express----路由

##### 		1.路由是根据url 决定了那部分去响应客户端请求。

##### 		在HTTP请求中，可以通过路由提取出请求的URL以及GET/POST参数。

​		![1560766041965](C:\Users\ADMINI~1\AppData\Local\Temp\1560766041965.png)

##### 		2.代码格式

​							![1560766170510](C:\Users\ADMINI~1\AppData\Local\Temp\1560766170510.png)

##### 		app.post() 接受post请求;

##### 		app.all() 方法让路由函数接收所有指定URL的HTTP方法。

##### 		路径中使用*通配符可以匹配所有例：app.get("/a*b",function(req,res){}

#### 2.Express--中间件

##### 	中间件 每次接收到请求都会被先调用的函数 。就是给一些特定功能添加的一个场所。所有路由都是用的内容可以放入中间件中

​			![1560766317132](C:\Users\ADMINI~1\AppData\Local\Temp\1560766317132.png)

### 5.Express  模板引擎

#### 		1.![1560766481969](C:\Users\ADMINI~1\AppData\Local\Temp\1560766481969.png)

#### 		2.模板引擎 EJS--配置和使用

​			![1560766550952](C:\Users\ADMINI~1\AppData\Local\Temp\1560766550952.png)

#### 		3.模板引擎 EJS--模板编写

##### 				ejs文件内的内容和html相同  可以写一个基本html页面框架放置当中

##### 			插入数据:  ejs的数据源是在 render（“文件名”,{数据}）中进行传递的 使用数据  <%=数据%>

##### 				