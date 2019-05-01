# css

### 一、样式的创建(内部样式表 外部样式表 内联样式表)

#### A、内部样式表 

语法：
<style type="text/css">
/*css语句*/
</style>

注：使用style标记创建样式时，最好将该标记写在<head></head>;

#### B、外部样式 

*方法一：外部样式表的创建： <link rel="stylesheet" type="text/css" href="目标文件的路径及文件名全称" /> 说明： 使用link元素导入外部样式表时，需将该元素写在文档头部，即<head>与</head>之间。 rel（relation）：用于定义文档关联，表示关联样式表； type：定义文档类型； 

方法二：外部样式表的导入 <style type="text/css"> @import url(目标文件的路径及文件名全称); </style> **注：@和import之间没有空格 url和小括号之间也没有空格；必须结尾以分号结束；** 

#### C、内联样式 （行间样式，行内样式，嵌入式样式、内嵌样式） 

语法：<标签 style="属性：属性值;属性:属性值;"></标签>

例：<div style="width:500px; height:200px;"></div>

### 二、两种引入外部样式表link和import之间的区别

**差别1：本质的差别：**link属于XHTML标签，而@import完全是CSS提供的一种方式。

**差别2：加载顺序的差别：**当一个页面被加载的时候（就是被浏览者浏览的时候），link引用的CSS会同时被加载，而@import引用的CSS会等到页面全部被下载完再被加载。所以有时候浏览@import加载CSS的页面时开始会没有样式（就是闪烁），网速慢的时候还挺明显。
**差别3：兼容性的差别：**@import是CSS2.1提出的，所以老的浏览器不支持，@import只有在IE5以上的才能识别，而link标签无此问题。
**差别4：使用dom(document object model文档对象模型 )控制样式时的差别**：当使用javascript控制dom去改变样式的时候，只能使用link标签，因为@import不是dom可以控制的.

### 三、样式表的优先级

A、内联样式表的优先级别最高
B、内部样式表与外部样式表的优先级和书写的顺序有关，后书写的优先级别高。

C、作用域：内联样式的作用域最小，只能应用于当前元素，其次是内部样式表，能应用于当前HTML文件，最后是外部样式表，能应用于所有链接的HTML文件。

### 四、CSS选择符（选择器）:表示要定义样式的对象

#### 1） 元素选择符/类型选择符（element选择器	)   如：div{width:100px; height:100px; background:red;} 

语法：元素名称{属性：属性值；}

说明：

a)元素选择符就是以文档语言对象类型作为选择符，即使用结构中元素名称作为选择符。例如body、div、p,img,em,strong,span......等。

b)所有的页面元素都可以作为选择符;

用法：
1)如果想改变某个元素得默认样式时，可以使用类型选择符；
（如：改变一个div、p、h1样式）

2) 当统一文档某个元素的显示效果时，可以使用类型选择符
（如：改变文档所有p段落样式）

#### 2) id选择器 

语法：#id名{属性：属性值;}
说明：
A）当我们使用id选择符时，应该为每个元素定义一个id属性
如：<div id="box"></div>
B）id选择符的语法格式是“#”加上自定义的id名
如：#box{width:300px; height:300px;}

C) 起名时要取英文名，不能用关键字：(所有的标记和属性都是关键字)
如：head标记
D）一个id名称只能对应文档中一个具体的元素对象，因为id只能定义页面中某一个唯一的元素对象。
E) 最大的用处：创建网页的外围结构。

#### **3）群组选择器** 

语法：选择符1，选择符2，选择符3{属性：属性值;} 例：#top1,#nav1{width:960px;} 说明：当有多个选择符应用相同的样式时，可以将选择符用“，”分隔的方式，合并为一组。 

#### **4）class选择器**/类选择器 

语法：·class名{属性：属性值;}
说明：
A）当我们使用class选择符时，应先为每个元素定义一个class名称
B）class选择符的语法格式是：

"如：<div class="top"></div>"

.top{width:200px; height:100px; background:green;}
用法：class选择符更适合定义一类样式；

#### **5)\*通配符**/通配选择器 

语法：*{属性：属性值；}
说明：通配选择符的写法是“*”，其含义就是所有元素。

*{margin:0; padding:0;}代表清除所有元素的默认边距和填充值；

margin:0 auto;元素的水平居中

#### **6） 包含选择器**/后代选择器 

语法：选择符1   选择符2{属性：属性值;}
说明：含义就是选择符1中包含的所有选择符2;
用法：当我的元素存在父级元素的时候，我要改变自己本身的样式，可以不另加选择符，直接用包含选择器的方式解决。

如：结构：<ul class="list">

​                   <li></li>

​                   <li></li>

​                   <li></li>

​        </ul>

​      样式 ： .list li{background:red;}

6.1:子选择器

语法：选择符1>选择符2{属性：属性值；}

说明：选择符1中的直接子选择符2

例：<div>

​         <p><span>111111111</span></p>

​         <span>2222222</span>

</div>

div>span{color:red;}只能将内容为222222的span标签改颜色

#### **7） 伪类选择器(伪类选择符)** 

语法 ： a:link{属性：属性值;}超链接的初始状态; 

a:visited{属性：属性值;}超链接被访问后的状态; 

a:hover{属性：属性值;}鼠标悬停，即鼠标划过超链接时的状态; 

a:active{属性：属性值;}超链接被激活时的状态，即鼠标按下时超链接的状态;

 **Link--visited--hover--active。** 

说明： A）当这4个超链接伪类选择符联合使用时，应注意他们的顺序，正常顺序为： a:link,a:visited,a:hover,a:active,错误的顺序有时会使超链接的样式失效；

 B）为了简化代码，可以把伪类选择符中相同的声明提出来放在a选择符中； 例如：a{color:red;} a:hover{color:green;} 表示超链接的初始和访问过后的状态一样，鼠标划过的状态和点击时的状态一样。

### 五、CSS选择符的权重

css中用四位数字表示权重，权重(特殊性)的表达方式如：0，0，0，0
类型选择符（元素选择器）的权重为0001       如：div{width:100px; height:100px;}
class选择符的权重为0010       如：.box{width:100px; height:100px;}
id选择符的权重为0100

伪类选择符的权重为0010     如:a:link a:visited......

包含选择符的权重：为包含选择符的权重之和
子选择符的权重为0000

属性选择符的权重为0010
伪元素选择符的权重为0001 
内联样式的权重为1000
继承样式的权重为0000 

### 六、页面中的注释

Html注释
<!-- 注释内容 -->

css的注释
/* 我是css的注释 */  

## 七、css属性和属性值的定义

- 属性：属性是指定选择符所具有的属性，它是css的核心，css2共有150多个属性

- 属性值：属性值包括法定属性值及常见的数值加单位，如25px，或颜色值等。



- 

## 八、CSS文本属性

#### 1、文本大小：{font-size:12px;}单位还可以是em，是父级元素的font-size的倍数；/系统默认的字号大小为16px 

**说明：**

1） 属性值为数值型时，必须给属性值加单位，属性值为0时除外。

2）单位还可以是pt，9pt=12px;

3）为了减小系统间的字体显示差异，IE Netscape Mozilla的浏览器制作商于1999年召开会议，*共同确定16px/ppi为标准字体大小默认值,即1em.默认情况下，*1em=16px,0.75em=12px; rem

#### 2、文本字体：{font-family:字体1，字体2，字体3；} 

**说明：**

浏览器首先会寻找字体1、如存在就使用改字体来显示内容，如在字体1不存在的情况下，则会寻找字体2，如字体2也不存在，按字体3显示内容，如果字体3 也不存在；则按系统默认字体显示； 

当字体是中文字体时，需加双引号；

当英文字体由多个单词组成时，需加双引号如（“Times New Roman”）

当英文字体只有一个单词组成是不加双引号；如：（Arial）；

Windows中文版本操作系统下，中文默认字体为宋体或者新宋体，英文字体默认为Arial.

#### 3、文本颜色：{color:颜色值;}red/#f00/rgb(255,0,0) 

**说明：** 

用十六进制(是计算机中数据的一种表示方法)表示颜色值： 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 A B C D E F 

颜色模式：光色模式
R G B
FF 00 00
颜色值的缩写：
当表示三原色的三组数字同时相同时，可以缩写为三位;
当用十六进制表示颜色值时，需要在颜色值前加“#”
\# fa 00 00

RGB表示方式：color:rgb(255,0,0);

#### 4、文字加粗font-weight:bolder(更粗的)/bold（加粗）/normal（常规）/100—900; 

**说明：**

在css规范中，把字体的粗细分为9个等级，分别为100——900，其中100对应最轻的字体变形，而900对应最重的字体变形，

#### 5、文本倾斜：font-style：italic/oblique/normal（取消倾斜，常规显示）; 

**说明：**

italic和oblique都是倾斜的文字, 但区别在于Italic是指斜体字，而Oblique是倾斜的文字，对于没有斜体的字体应该使用Oblique属性值来实现倾斜的文字效果.

#### 6、水平对齐方式{text-align:left左/right右/center居中/justify两端对齐(在部分浏览器中，对于中文不起作用);} 只针对文本或图片 

#### 7、垂直对齐方式 {vertical-align:top上/bottom下/middle居中/baseline基线（某些特定的元素类型起作用）;} 

#### 8、文字行高 {line-height:normal/value;}line-height:20px; line-height:2em; (当行高的单位省略时，默认为em) 

**说明：**

当单行文本的行高*等于*容器高时，可实现单行文本在容器中*垂直方向居中对齐；*
当单行文本的行高*小于*容器高时，可实现单行文本在容器中*垂直中齐以上；*
当单行文本的行高*大于*容器高时，可实现单行文本在容器中*垂直中齐以下*（IE6及以下版本存在浏览器兼容问题） 

#### 9、文本修饰 text-decoration:none/underline/overline/line-through 

**说明：**

none:没有修饰

underline:添加下划线

overline:添加上划线

line-through:添加删除线

#### 10、首行缩进：{text-indent:value;} 

**说明：**

1）text-indent可以取负值；

2）text-indent属性只对第一行起作用。

#### 11、检索英文字母大小写{text-transform:none无转换/capitalize首字母大写/uppercase全都大写/lowercase全都小写;}。 

#### 12、字间距{letter-spacing:value;}控制英文字母或汉字的字距。 

#### 13、词间距{word-spacing:value;}控制英文单词词距。 

#### 扩展：14、文本流控制{layout-flow:horizontal/vertical-ideographic;} 

**说明：**

1）horizontal:自左向右

2）vertical-ideographic:自上而下

#### 15、文字属性简写：font:bolder italic 12px/1.5em "宋体";     简写时，字体和字号是必备 

font属性的简写：字号，行高，字体 说明:font的属性值应按以下次序书写(各个属性之间用空格隔开) 顺序: font-style font-weight font-size / line-height font-family

(1)简写时 , font-size和line-height只能通过斜杠/组成一个值，不能分开写。

(2) 这种简写法只有在同时指定font-size和font-family属性时才一起作用,如果你没有设定font-weight , font-style , 他们会使用缺省值。

## 九、CSS列表属性

1、定义列表符号样式

list-style-type：disc(实心圆)/circle(空心圆)/square(实心方块)/none(去掉列表符号)；

2、使用图片作为列表符号

list-style-image：url(所使用图片的路径及全称)；

3、定义列表符号的位置

list-style-position:outside(外边)/inside(里边)；

*list-style:none;去掉列表符号*

## 十、边框的属性和属性值

border:边框宽度 边框风格 边框颜色;

例如：border:5px solid #ff0000

边框宽度：border-width:

边框颜色：border-color:

边框样式：*border-style:solid(实线)/dashed(虚线)dotted(点划线)double(双线)*none(去掉边框);

可单独设置一方向边框，

border-bottom:边框宽度 边框风格 边框颜色;      底边框

border-left:边框宽度 边框风格 边框颜色;             左边框

border-right:边框宽度 边框风格 边框颜色;          右边框

border-top:边框宽度 边框风格 边框颜色;           上边框

## 十一、CSS背景属性

1、背景颜色 {background-color:颜色值;}

2、背景图片的设置 background-image：url(背景图片的路径及全称）；

3、背景图片平铺属{background-repeat:no-repeat不平铺/repeat平铺/repeat-x  X轴平铺/repeat-y   Y轴平铺 }

4、背景图的位置{background-position:left/center/right/数值      top/center/bottom/数值;}

水平方向上的对齐方式（left/center/right）或值 
垂直方向上的对齐方式(top/center/bottom)或值 
background-position:值1 值2; 
两个值 ：第一个值表示水平位置的值，第二个值：表示垂直的位置。 
当两个值都是center的时候写一个值就可以代表的是水平位置和垂直位置 ；

当元素小背景图大的时候，想显示右下方的背景图，通过负值来调整背景图的位置；

5、背景图的固定{background-attachment:fixed固定/scroll滚动;}

fixed 固定，不随内容一块滚动，根据可视窗口固定位置；
scroll:随内容一块滚动。
*网页上常用的图片格式*
1）jpg :有损压缩格式，靠损失图片本身的质量来减小图片的体积，适用于颜色丰富的图像;(像素点组成的，像素点越多会越清晰 )
2）gif：无损压缩格式，支持透明，支持动画，适用于颜色数量较少的图像;
3）png:无损压缩格式，支持透明，不支持动画，(是fireworks的 源文件格式)，适用于颜色数量较少的图像; 

## 十二、CSS浮动属性

语法：float:none/left/right;

的：就是让竖着的元素横着显示

一个元素设置float：left/right;时，元素会脱离文档流（半脱离），不占空间；
有三个取值：
left:元素向左浮动

right:元素向右浮动
none:默认值，不浮动。

![img](file:///C:/Users/Administrator/Desktop/%E7%AC%AC%E4%B8%80%E5%91%A8/day03/%E8%B5%84%E6%96%99/%E7%AC%94%E8%AE%B0/float.jpg)

清除浮动可以理解为打破横向排列*。

*清除浮动的属性是clear，语法：*

clear : none | left | right | both

none：默认值。允许两边都可以有浮动对象

left：清除左浮动/不允许左边有浮动对象

right  :  清除右浮动/不允许右边有浮动对象

both  :  清除两端浮动/不允许有浮动对象

有一点是要记住的那就是*

对于CSS的清除浮动(clear)，一定要牢记：这个规则只能影响使用清除的元素本身，不能影响其他元素

## 十三、 padding 

padding是内容与边框之间的距离 ，我们称它为内边距。  
padding有四个方向，我们可以采用简写:
padding:10px;  上右下左四个方向的padding都为10px
padding:10px 20px; 上下10 左右20
padding:10px 20px 30px ; 上10 左右20 下30 
padding:10px 20px 30px 40px; 上10 右20 下30 左40

单独某个方向设置值：
padding-top
padding-right
padding-bottom
padding-left 

可以进行padding覆盖
padding:10px;
padding-left:20px;

Tip:padding使用后会增加盒子实际所占的宽度和高度，如果不想改变盒子原本所占有的宽度和高度，那么就把宽度和高度减少(内容的宽度和高度)

## 十四、渐进增强和优雅降级

渐进增强 progressive enhancement：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。  优雅降级 graceful degradation：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。  区别：优雅降级是从复杂的现状开始，并试图减少用户体验的供给，而渐进增强则是从一个非常基础的，能够起作用的版本开始，并不断扩充，以适应未来环境的需要。降级（功能衰减）意味着往回看；而渐进增强则意味着朝前看，同时保证其根基处于安全地带。 

## 十五、CSS3选择器

#### 一、层级选择器

E>F 子选择器 选择匹配的F元素，且匹配的F元素所匹配的E元素的子元素

E+F 相邻兄弟选择器 选择匹配的F元素，且匹配的F元素紧位于匹配的E元素的后面

E~F 通用选择器 选择匹配的F元素，且位于匹配的E元素后的所有匹配的F元素

#### 二、属性选择器

1、E[attr]：只使用属性名，但没有确定任何属性值；
2、E[attr="value"]：指定属性名，并指定了该属性的属性值；
3、E[attr~="value"]：指定属性名，并且具有属性值，此属性值是一个词列表，并且以空格隔开，其中词列表中包含了一个value词，而且等号前面的“〜”不能不写
4、E[attr^="value"]：指定了属性名，并且有属性值，属性值是以value开头的；
5、E[attr$="value"]：指定了属性名，并且有属性值，而且属性值是以value结束的
6、E[attr*="value"]：指定了属性名，并且有属性值，而且属值中包含了value；
7、E[attr|="value"]：指定了属性名，并且属性值是value或者以“value-”开头的值（比如说zh-cn）;

#### 三、伪类选择器

##### 1、结构性伪类选择器

X:first-child 匹配子集的第一个元素。IE7就可以支持
X:last-child匹配父元素中最后一个X元素
X:nth-child(n)用于匹配索引值为n的子元素。索引值从1开始
X:only-child这个伪类一般用的比较少，比如上述代码匹配的是div下的有且仅有一个的p，也就是说，如果div内有多个p，将不匹配。
X:nth-of-type(n)匹配同类型中的第n个同级兄弟元素X
X:only-of-type匹配属于同类型中唯一兄弟元素的X
X:first-of-type匹配同级兄弟元素中的第一个X元素
X:nth-last-child(n)从最后一个开始算索引。
X:nth-last-of-type(n) 匹配同类型中的倒数第n个同级兄弟元素X
X:root匹配文档的根元素。在HTML（标准通用标记语言下的一个应用）中，根元素永远是HTML
X:empty匹配没有任何子元素（包括包含文本）的元素X

##### 2、目标伪类选择器

E:target	选择匹配E的所有元素，且匹配元素被相关URL指向

##### 3、UI 元素状态伪类选择器

E:enabled 匹配所有用户界面（form表单）中处于可用状态的E元素
E:disabled 匹配所有用户界面（form表单）中处于不可用状态的E元素
E:checked 匹配所有用户界面（form表单）中处于选中状态的元素E
E:selection 匹配E元素中被用户选中或处于高亮状态的部分

##### 4、否定伪类选择器

E:not(s)	（IE6-8浏览器不支持:not()选择器。）
匹配所有不匹配简单选择符s的元素E

##### 5、动态伪类选择器

E:link
链接伪类选择器 
  选择匹配的E元素，而且匹配元素被定义了超链接并未被访问过。常用于链接描点上 
E:visited  
链接伪类选择器
选择匹配的E元素，而且匹配元素被定义了超链接并已被访问过。常用于链接描点上 
E:active
用户行为选择器
选择匹配的E元素，且匹配元素被激活。常用于链接描点和按钮上 
E:hover
用户行为选择器
选择匹配的E元素，且用户鼠标停留在元素E上。IE6及以下浏览器仅支持a:hover 
E:focus 用户行为选择器 选择匹配的E元素，而且匹配元素获取焦点

## 十六、CSS3文本属性

### 1、浏览器前缀的简介及应用

某些CSS属性还只是最新版的预览版，并未发布成最终的正式版，而大部分浏览器已经为这些属性提供了支持，但这些属性是小部分浏览器专有的；有些时候，有些浏览器为了扩展某方面的功能，它们会选择新增的一些CSS属性，这些自行扩展的CSS属性也是浏览器专属的。为了让这些浏览器识别这些专属属性，CSS规范允许在CSS属性前增加各自的浏览器前缀。 

![img](file:///C:/Users/Administrator/Desktop/%E7%AC%AC%E4%B8%89%E5%91%A8/day02/%E8%B5%84%E6%96%99/%E7%AC%94%E8%AE%B0/a.png) 

###  2、文本阴影属性语法及应用

![img](file:///C:/Users/Administrator/Desktop/%E7%AC%AC%E4%B8%89%E5%91%A8/day02/%E8%B5%84%E6%96%99/%E7%AC%94%E8%AE%B0/a.jpg) 

### 3、文本换行的相关属性

#### Word-wrap

属性值：
normal
说明：只在允许的断字点换行（浏览器保持默认处理）
break-word
说明：属性允许长单词或 URL 地址换行到下一行。
属性用来标明是否允许浏览器在单词内进行断句，这是为了防止当一个字符串太长而找不到它的自然断句点时产生溢出现象。

#### Word-break

属性值：
break-all
说明：它断句的方式非常粗暴，它不会尝试把长单词挪到下一行，而是直接进行单词内的断句
Keep-all
说明：文本不会换行，只能在半角空格或连字符处换行。

### 4、@font-face

@font-face是CSS3中的一个模块，他主要是把自己定义的Web字体嵌入到你的网页中，随着@font-face模块的出现，我们在Web的开发中使用字体不怕只能使用Web安全字体（@font-face这个功能早在IE4就支持）

@font-face的语法规则：@font-face {
font-family: <YourWebFontName>; 
src: <source> [<format>][,<source> [<format>]]*; 
[font-weight: <weight>]; 
[font-style: <style>]; 
}

#### @font-face语法说明：

1、YourWebFontName:此值指的就是你自定义的字体名称，最好是使用你下载的默认字体，他将被引用到你的Web元素中的font-family。如“font-family:"YourWebFontName";” 
2、source:此值指的是你自定义的字体的存放路径，可以是相对路径也可以是绝路径； 
3、format：此值指的是你自定义的字体的格式，主要用来帮助浏览器识别，其值主要有以下几种类型：truetype,opentype,truetype-aat,embedded-opentype,avg等； 
4、weight和style:这两个值大家一定很熟悉，weight定义字体是否为粗体，style主要定义字体样式，如斜体。

实例：@font-face {
font-family: 'icomoon';
src:url('fonts/icomoon.eot');
src:url('fonts/icomoon.eot?#iefix') format('embedded-opentype'),
url('fonts/icomoon.svg#icomoon') format('svg'),
url('fonts/icomoon.woff') format('woff'),
url('fonts/icomoon.ttf') format('truetype');
font-weight: normal;
font-style: normal;
}

## 十七、CSS3 背景的新增属性

### 1、Background-origin 背景原点

说明：指定background-origin属性应该是相对位置属性值：padding-box	背景图像填充框的相对位置 
border-box	背景图像边界框的相对位置 
content-box	背景图像的相对位置的内容框 
注：默认值为：padding-box;

### 2、Background-clip 背景裁切

说明：background-clip 属性规定背景的绘制区域。属性值：border-box	背景被裁剪到边框盒。
padding-box	背景被裁剪到内边距框。
content-box	背景被裁剪到内容框
。 
注：默认值：border-box;

### 3、Background-size 背景尺寸

说明：background-size 规定背景图像的尺寸属性值：length
规定背景图的大小。第一个值宽度，第二个值高度。
Percentage(%)
以百分比为值设置背景图大小
cover
把背景图像扩展至足够大，以使背景图像完全覆盖背景区域
contain
把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域。

### 4、css3多背景属性

Eg:p{ background:url(demo.gif) no-repeat; //这是写给不识别下面这句的默认背景图片
background:url(demo.gif) no-repeat ,url(demo1.gif) no-repeat left bottom, url(demo2.gif) no-repeat 10px 15px; //这是高级浏览器的css多重背景，第一个最上面 
background-color:yellow; //这是定义的默认背景颜色，全部适合 }

## 十八、CSS3 颜色特性

#### 1、rgba 颜色模式

#### 2、 Hsl 颜色模式（了解）

#### 3、 Hsla 颜色模式（了解）

## 十九、CSS3 边框的新增属性

### 1、border-color

EG:border-color:red green #000 yellow;(上右下左)

### 2、border-image

border-image 属性是一个简写属性，用于设置以下属性:
border-image-source	用在边框的图片的路径。
border-image-slice	图片边框向内偏移。
border-image-repeat	图像边框是否应平铺(repeated)、铺满(rounded)或拉伸(stretched)
border-image-outset	边框图像区域超出边框的量

### 3、Border-radius 圆角边框

(1).box{     border-radius: 5px 10px 20px 50px          } 

![img](file:///C:/Users/Administrator/Desktop/%E7%AC%AC%E4%B8%89%E5%91%A8/day02/%E8%B5%84%E6%96%99/%E7%AC%94%E8%AE%B0/bor1.png) 

(2).div1{border-radius: 2em/1em} 

![img](file:///C:/Users/Administrator/Desktop/%E7%AC%AC%E4%B8%89%E5%91%A8/day02/%E8%B5%84%E6%96%99/%E7%AC%94%E8%AE%B0/bor2.png) 

以斜杠/分开后面的参数: 第一个参数表示圆角的水平半径，第二个参数表示圆角的垂直半径 

(3).div1{         border-radius:10px 20px 30px 40px**/**40px 30px 20px 10px } 

![img](file:///C:/Users/Administrator/Desktop/%E7%AC%AC%E4%B8%89%E5%91%A8/day02/%E8%B5%84%E6%96%99/%E7%AC%94%E8%AE%B0/bor3.png) 

按顺时针的顺序，斜杠/左边是四个圆角的水平半径，右边是四个圆角的垂直半径，但是通常我们很少写右边的参数，那就是默认右边等于左边的值。 

## 二十、box-shadow 盒子阴影

属性值： 

![img](file:///C:/Users/Administrator/Desktop/%E7%AC%AC%E4%B8%89%E5%91%A8/day02/%E8%B5%84%E6%96%99/%E7%AC%94%E8%AE%B0/img.png) 

Eg:box-shadow: 10px 10px 5px #888888 

## 二十一、 颜色和渐变

### 1、rbg、英文单词 、进制 rgba。

不透明度:
	rgba
	opacity: 使用的时候会连字都变得透明

### 2、颜色渐变 --- 应用在元素的背景上

渐变分为两种：线性渐变 和 径向渐变

#### linear-gradient() 线性渐变  

	Tip：线性渐变的初始颜色变化默认是从上到下。
		而且，渐变必须设置在background的身上。
		
		background-image: linear-gradient;


	首先，线性渐变是支持多个颜色渐变的。
		background: linear-gradient(red,yellow,blue,pink);
	
	设置渐变方向：
		background: -webkit-linear-gradient(bottom,red,pink);
	如果在参数里直接设置方向，那么需要加浏览器前缀。
	如果在方向的前面加上to，那么就不需要加浏览器前缀。
		background: linear-gradient(to left,red,pink);
		to left 、 to right 、 to top 、to bottom ,没有to center
	当然，关于方向我们也可以组合来使用：
		to left top 或者top left bottom.....
		
	我们除了设置具体的方向值，还可以通过  angle 来设置角度。
	
		在代码中deg表示角度
			0deg表示从下向上
			如果角度为正，则为顺时针，如果角度为负，则为逆时针。
			
	渐变百分比
		background: linear-gradient(to left,red 10%,black 90%);
		方向：从右到左，
			表示从起始方向开始，从右向左的10%为纯红色，从10%到90%为红色向黑色的渐变色，剩下的
			为纯黑色。
			
		练习：
			红、绿、蓝、黄
			
			灰  绿 灰  绿  
			
	线性渐变在IE:
		filter:progid:DXImageTransform.Microsoft.gradient(startColorstr='#ffffff',
		endColorstr='#ff0000',GradientType='1');   
	GradientType = 0 方向是从上向下  1为从左向右
	
	重复线性渐变
		一个渐变的过程已经完成，后续重复的进行这个过程。
		repeating-linear-gradient() ;

#### radial-gradient:径向渐变

​	方向：
		left top right bottom ，前面要加webkit
		也可以设置具体的值：apx  bpx 
	还可以设置圆的形状：
		正圆:circle
		椭圆:ellipse

## 二十二、圆角

border-radius:圆角
	boder-top-left-radius: 左上
	border-top-right-radius:右上
	border-bottom-right-radius:
	border-bottom-left-riadus:
	
	border-radius：可以设置一个值到四个值。
		顺序：
			1个值：四个角
			2个值: 左上右下 右上左下
			三个值:  左上  右上左下  右下 
			四个值: 左上 右上  右下  左下 

## 二十三、border-image 边框图片

​	目前IE11以上才支持。

border-image 是一个简写值，分别有以下属性值,
		border-image-source	图片地址
		border-image-slice   图片切片
		border-image-width  图片宽度
		border-image-outset  图片外凸
		border-image-repeat  图片重复  


	border-image-slice：图像切片
		值：number  | 百分比  {1,4}
		Tip：
			{1,4} 表示最少一个值，最多四个值
		指定边框图像顶部，右侧，底部，左侧内偏移量。没有具体的单位值，px em rem都不可以。
		只可以用数字或者百分比。


​	
	border-image-width  图片宽度  
		值：lenghth | number | 百分比 {1,4}
		
	border-image-outset  图片外凸
	
	border-image-repeat  图片重复  			

## 二十四、盒子阴影

box-shadow :
	h-shadow v-shadow blur spread color inset;
	

	h-shadow：水平阴影的位置 允许负值
	v-shadow：垂直阴影的位置 允许负值
	blur : 模糊值
	spread 阴影的大小
	color	颜色
	inset 内部阴影
## 二十五、弹性盒子模型

### 怪异盒子模型：

​	设置的宽度和高度就是元素在网页中实际占据的宽度和高度。
	开启怪异盒子模型：
		box-sizing:border-box|content-box
	

### 弹性盒子模型：

#### 核心概念

​	主轴
	侧轴
	弹性容器
	弹性子元素

#### 弹性容器专用属性：

##### flex-direction:

​	作用：弹性容器中子元素的排列方式(主轴排列方式)【子元素在主轴上的排列方式】
	属性：
		row:默认在一行排列
		row-reverse:反转横向排列（右对齐，从后往前排，最后一项排在最前面。）
		column：纵向排列。
		column-reverse：反转纵向排列，从下往上排，最后一项排在最上面

##### flex-wrap:

​	作用:设置弹性盒子的子元素超出父容器时是否换行 
	属性值：
		nowrap: 默认值。规定元素不拆行或不拆列。
		wrap:规定元素在必要的时候拆行或拆列。
		wrap-reverse:规定元素在必要的时候拆行或拆列，但是以相反的顺序。
	flex-flow: flex-direction和flex-wrap的缩写

##### align-item:

​	作用:设置弹性盒子元素在侧轴（纵轴）方向上的对齐方式
	属性值：
		flex-start：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。
        flex-end：弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。
        center：弹性盒子元素在该行的侧轴（纵轴）上居中放置。（如果该行的尺寸小于弹性盒子元素的尺寸，则会向两个方向溢出相同的长度）。
        baseline：如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。其它情况下，该值将参与基线对齐。

##### align-content:

​	作用:修改 flex-wrap 属性的行为，类似 align-items, 但不是设置子元素对齐，
			而是设置行对齐(行与行的对其方式)
	属性:
		flex-start没有行间距
		flex-end底对齐没有行间距
		center居中没有行间距
		space-between两端对齐，中间自动分配
		space-around自动分配距离

##### justify-content:

​	作用:设置弹性盒子元素在主轴（横轴）方向上的对齐方式
	属性：
		flex-start默认，顶端对齐
        flex-end末端对齐
        center居中对齐
        space-between两端对齐，中间自动分配
        space-around自动分配距离

### 弹性子元素相关属性：

#### order

设置弹性盒子的子元素排列顺序。 number排序优先级，数字越大越往后排，默认为0，支持负数。

####  flex-grow:

设置或检索弹性盒子元素的扩展比率。flex-grow用于设置各item项按对应比例划分剩余空间，若flex中没有指定flex-grow,则相当于设置了   flex-grow:1

参数：
	 <integer>：一个数字，规定项目将相对于其他灵活的项目进行扩展的量。默认值是 0。
	瓜分容器的剩余空间。
	什么是剩余空间？
		假设父元素的宽度是500px，
		有三个子元素，每个宽度是100，那么剩余空间就是500 - 100 * 3 = 200。
		而flex-grow就是用来瓜分剩余空间的。
		例如第一个盒子属性为flex-grow:1;那么剩余空间就会被分成一份，第一个盒子额外的占据了这一份。
		如果这个时候第二个盒子flex-grow:2;那么此时剩余空间就被分成三分，第一个盒子占一份，第二个盒子占两份。	

####  flex-shrink:

指定了 flex 元素的收缩规则。flex 元素仅在默认宽度之和大于容器的时候才会发生收缩，其收缩的大小是依据 flex-shrink 的值。flex-shrink用于设置item的总和超出容器空间时，各item的收缩比例，若flex中没有指定flex-shrink, 则等同于设置了flex-shrink:1

指定了 flex 元素的收缩规则。
    参数：<integer>：一个数字，规定项目将相对于其他灵活的项目进行收缩的量。默认值是 1。

```
当父容器的剩余空间为0的时候，并且默认处于非换行状态的情况下，子元素是没有办法利用弹性容器的剩余空间
进行扩展的。
如果如容器的剩余宽度为负数的情况下(子元素的宽度之和大于父容器的宽度)，那么子元素就会被收缩。
收缩的比例为1:1.
例如，一个弹性容器中有三个子元素，那么他们的收缩比例就为1:1:1.
如果这个时候，第一个子元素设置了flex-shrink:2;那么我们就会发现，这个元素比其他两个元素收缩的幅度更大。
同时呢，因为第一个子元素空间的更多收缩，所以第二个和第三个元素就会获得更多的空间。
我们假设第二个和第三个盒子收缩比例为x1,那么第一个盒子的收缩比例就为x2.

举个例子：

父元素 500px。三个子元素分别设置为 150px，200px，300px。

三个子元素的 flex-shrink 的值分别为 1，2，3。

首先，计算子元素溢出多少：150 + 200 + 300 - 500 = -150px。

那这 -150px 将由三个元素的分别收缩一定的量来弥补。

具体的计算方式为：每个元素收缩的权重为其 flex-shrink 乘以其宽度。

所以总权重为 1 * 150 + 2 * 200 + 3 * 300 = 1450
    总权重: 收缩比 * 宽度 之和
三个元素分别收缩：
溢出值 * 收缩比  * width / 总权重 = 收缩的宽度
150 * 1(flex-shrink) * 150(width) / 1450 = -15.5
150 * 2(flex-shrink) * 200(width) / 1450 = -41.4
150 * 3(flex-shrink) * 300(width) / 1450 = -93.1
三个元素的最终宽度分别为：

150 - 15.5 = 134.5
200 - 41.4 = 158.6
300 - 93.1 = 206.9
同样，当所有元素的 flex-shrink 之和小于 1 时，计算方式也会有所不同：

此时，并不会收缩所有的空间，而只会收缩 flex-shrink 之和相对于 1 的比例的空间。

还是上面的例子，但是 flex-shrink 分别改为 0.1，0.2，0.3。

于是总权重为 145（正好缩小 10 倍，略去计算公式）。

三个元素收缩总和并不是 150px，而是只会收缩 150px 的 (0.1 + 0.2 + 0.3) / 1 即 60% 的空间：90px。

每个元素收缩的空间为：

90 * 0.1(flex-shrink) * 150(width) / 145 = 9.31
90 * 0.2(flex-shrink) * 200(width) / 145 = 24.83
90 * 0.3(flex-shrink) * 300(width) / 145 = 55.86
三个元素的最终宽度分别为：

150 - 9.31 = 140.69
200 - 24.83 = 175.17
300 - 55.86 = 244.14
```

####  flex-basis:

用于设置或检索弹性盒伸缩基准值。flex-basis用于设置各item项的伸缩基准值，可以取值为长度或百分比，如果flex中省略了该属性，则相当 于设置了flex-basis:0.

参数：<integer>：一个长度单位或者一个百分比，规定元素的初始长度。
	auto：默认值。长度等于元素的长度。如果该项目未指定长度，则长度将根据内容决定。
	

```
flex-basis是width的替代品。如果子元素设置了flex-basis或者width，那么在分配空间之前，就会跟父容器预约这么多
的空间，然后剩下的才归到剩余空间，然后父容器再把剩余空间分配给flex-grow的容器。如果同时设置了flex-basis
和width，那么width的属性就会被覆盖，也就是说flex-basis的优先级比width高。
```

####  align-self:

在弹性子元素上使用。覆盖容器的 align-items 属性。

#### flex:

设置弹性盒子的子元素如何分配空间。 

flex的值的完整写法是[<flex-grow> <flex-shrink> <flex-basis>],不过它的取值还有可能是单个数字 或者单个百分比等，不同种类的取值所表示的意思是大有不同的。

当flex为none时,等同于flex: 0 0 auto;     

当flex为auto时，等同于flex: 1 1 auto; 

当flex取值为一个数字，则该数字是设置的flex-grow值，其它两个属性用初始值，如flex:1时， 等同于flex: 1 1 0% 

当flex取值为2个数字时，相当于设置的flex-grow和flex-shrink值，flex-basis取值为初始值，如flex:1 0时，等同于flex: 1 0 0%

flex值为一个数字和一个长度或百分比时
 当flex取值为1个数字和1个长度或百分比时，设置的是flex-grow和flex-basis的值，flex-shrink值
    时初始值，如flex:1 20%,等同于flex: 1 1 20%

 flex 属性用于设置或检索弹性盒模型对象的子元素如何分配空间。

        flex 属性是 flex-grow、flex-shrink 和 flex-basis 属性的简写属性。
        详情参阅flex缩写文档

#### align-self:

在弹性子元素上使用。覆盖容器的 align-items 属性。

	值与容器属性一样，只是这个是单独的设置某个元素。

## 二十六、响应式布局

### 1、 相关人物介绍：

伊桑·马科特（Ethan Marcotte）在2010年首先提出了响应式网页设计（RWD,Responsive Web Design）这个术语。
在他的一篇文章《Responsive Web Design · An A List Apart Article》中他将已有的三种发开技巧（弹性
图片，弹性网格布局，媒体与媒体查询） 进行了整合，命名为响应式网页设计。
那什么才是真正的响应式设计？马科特说，真正的响应式设计方法不仅仅是根据可视区域大小而改变网页布局，而是要
从整体上颠覆当前网页的设计方法，是针对任意设备的网页内容进行完美布局的一种显示机制。

### 2、当今流行的网页布局方案

固定布局：以像素作为页面的基本单位，不管设备屏幕及浏览器宽度，只设计一套尺寸；

可切换的固定布局：同样以像素作为页面单位，参考主流设备尺寸，设计几套不同宽度的布局。通过识别的屏幕尺寸或
    浏览器宽度，选择最合适的那套宽度布局；

响应式布局：对页面进行响应式的设计实现，需要对相同内容进行不同宽度的布局设计，有两种方式：pc优先（从pc
端开始向下设计）；移动优先（从移动端向上设计）；无论基于那种模式的设计，要兼容所有设备，布局响应时不
可避免地需要对模块布局做一些变化（发生布局改变的临界点称之为断点）。

弹性布局：以百分比作为页面的基本单位，可以适应一定范围内所有尺寸的设备屏幕及浏览器宽度，并能完美利用有效空
    间展现最佳效果；

混合布局：同弹性布局类似，可以适应一定范围内所有尺寸的设备屏幕及浏览器宽度，并能完美利用有效空间展现最佳效果；
    只是混合像素、和百分比两种单位作为页面单位。

### 3、响应式布局的优缺点

设计特点：
    面对不同分辨率设备灵活性强
    能够快捷解决多设备显示适应问题
缺点：
    兼容各种设备工作量大，效率低下
    代码累赘，会出现隐藏无用的元素，加载时间加长
    其实这是一种折中性质的设计解决方案，多方面因素影响而达不到最佳效果
    一定程度上改变了网站原有的布局结构，会出现用户混淆的情况

### 4、 Meta标签的设置

​    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0,minimum-scale=1.0,  user-scalable=no">
    这段代码的几个参数解释：
    width = device-width：宽度等于当前设备的宽度
    initial-scale： 初始的缩放比例（默认设置为1.0）
    minimum-scale：允许用户缩放到的最小比例（默认设置为1.0）
    maximum-scale：允许用户缩放到的最大比例（默认设置为1.0）
    user-scalable：用户是否可以手动缩放（默认设置为no，因为我们不希望用户放大缩小页面）

### 5、meta标签其他可选设置

H5页面窗口自动调整到设备宽度，并禁止用户缩放页面
<meta name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no" />
忽略将页面中的数字识别为电话号码
<meta name="format-detection" content="telephone=no" />
忽略Android平台中对邮箱地址的识别
<meta name="format-detection" content="email=no" />
当网站添加到主屏幕快速启动方式，可隐藏地址栏，仅针对ios的safari
<meta name="apple-mobile-web-app-capable" content="yes" />
<!-- ios7.0版本以后，safari上已看不到效果 -->
将网站添加到主屏幕快速启动方式，仅针对ios的safari顶端状态条的样式
<meta name="apple-mobile-web-app-status-bar-style" content="black" />

### 6、rem 和 vw/vh

rem是以html根元素的字体大小为参考。
默认情况下，1rem = 16px，此时html相当于font-size:100%。

html {
    font-size:100px;
   }

 1rem = ;


vh|vw这两个单位，以视口为参考。
视口单位中的“视口”，桌面端指的是浏览器的可视区域；移动端指的就是Viewport中的Layout Viewport。

    1vw等于视口宽度的1%。
    1vh等于视口高度的1%。
    Tip：并且会随着视口的变化而变化。
### 7、什么是断点？

断点，响应式网页发生变化的临界点。

### 8、什么是媒体查询，响应式网页与媒体查询的关系

媒体查询是css当中的一种技术，通过这种技术可以判断用户的浏览器宽度，类型，以及横屏还是竖屏等。

响应式网页的实现方式有很多，主流方式是通过媒体查询的形式来实现响应式网页。

### 9、媒体查询特性

媒体查询可以让我们根据设备显示器的特性（如视口宽度、屏幕比例、设备方向：横向或纵向）为其设定CSS样式，
媒体查询由媒体类型和一个或多个检测媒体特性的条件表达式组成。媒体查询中可用于检测的媒体特性有 width 、
height 和 color （等）。使用媒体查询，可以在不改变页面内容的情况下，为特定的一些输出设备定制显示效果。

### 10、媒体查询基本语法

@media 媒体类型  关键字 (条件1) 关键字 (条件2) ... {
    css code
}

常用媒体类型：
    all     所有设备
    aural    听觉设备
    braille   点字触碰设备
    print    打印
    tty      打字机设备
    tv      电视机等设备
    screen  显示器、笔记本、电脑等设备
    ...

    上述的设备有很多，只是简单的陈述几种，但是我们常用的设备只有all和screen

关键字：
    and 并且 和
    not 否定、排除
    only 限定
    or 或者
条件：
    min-width:400px

媒体查询语法示例:
    @media all (min-width:480px) {
        html {
            background:red;
        }
    }

    上述示例表示当用户设备屏幕处于最小宽度为480px以上的时候，网页的背景颜色为红色
    
    /* 竖屏 */
    @media screen and (orientation:portrait) {对应样式}
    
    /* 横屏 */
    @media screen and (orientation:landscape){对应样式}
### 11、常用断点值

    320px
    480px
    768px
    1024px
### 12、css2中媒体查询的用法

其实并不是只有CSS3才支持Media的用法，早在CSS2开始就已经支持Media，具体用法，就是在HTML页面的head标签中插入如下的一段代码
<link rel="stylesheet" type="text/css" media="screen" href="style.css">;
想知道现在的移动设备是不是纵向放置的显示屏，可以这样写：
<link rel=“stylesheet” type=“text/css” media=“screen and  (orientation:portrait)”  	href="style.css">
orientation:portrait：指定输出设备中的页面可见区域高度大于或等于宽度
landscape：除portrait值情况外，都是landscape
第一段的代码也用CSS2来实现，让它一样可以让页面宽度小于960的执行指定的样式文件：
<link rel="stylesheet" type="text/css" media="screen and (max-width:960px)" href="style.css">

### 13、移动端优先和pc端优先

在开发响应式网页的时候，我们有两种选择，一种是从移动端开始开发然后逐渐升级到pc，这种方式叫做移动端优先
pc端优先则正好相反。

### 