# 第一章JavaScript简介

## JavaScript 实现

    JavaScript 实现由三个不同的部分组成：核心（ECMAScript），文档对象模型（DOM），浏览器对象模型（BOM）

### ECMAscript
    Web浏览器只是ECMAscript实现的宿主环境之一（其他：node，Adobe flash），宿主环境提供基础的实现，也提供扩展，以便语言与环境之间对接交互
    ECMAscript规定了：语法、类型、语句、关键字、保留字、操作符、对象

## 文档对象模型（DOM）
    针对XML，但经过扩展用于HTML的应用程序编程接口。DOM把整个页面映射为一个多层节点结构。HTML或XML页面中的每个组成部分都是某种类型的节点，这些节点有包含不同类型的数据。
    好处： 开发者获得了控制页面内容和结构的主动权，通过DOM的API增删改查任何节点。

### DOM 级别
    DOM 1级组成：DOM核心和DOM HTML两个模块。
    DOM核心规定的是如何映射基于XML的文档结构，简化对文档中任意部分的访问和操作。
    DOM HTML在DOM核心的基础上扩展添加针对HTML的对象和方法。

    DOM 2级 更进一步扩充鼠标和用户界面事件、范围、遍历，通过对象接口增加对css的支持

    DOM 3级 引入统一方式加载和保存文档的方法，新增验证文档的方法。

## 浏览器对象模型（BOM）
    使用BOM可以控制浏览器显示的页面以为的部分。BOM没有标准，HTML5得到解决，其致力于将BOM功能写入正式规范。
    从根本上将，BOM只处理浏览器窗口和框架，但人们习惯把所有针对浏览器的JavaScript扩展算BOM的一部分：
    1、弹出新浏览器窗口的功能
    2、移动、缩放和关闭浏览器的功能
    3、提供浏览器详细信息的navigator对象
    4、提供浏览器所加载页面的详细信息的location对象
    5、提供用户显示器分辨率详细信息的screen对象
    6、对cookies的支持
    7、想XMLHTTPRequest和IE的ActiveXObject这样 自定义对象

## 扩充
    当前五个主要浏览器（IE、Firefox、Chrome、Safari 和 Opera）
    -ms-       //-ms代表ie内核识别码
    -moz-      //-moz代表火狐内核识别码
    -webkit-   //-webkit代表谷歌内核识别码
    -o-        //-o代表欧朋【opera】内核识别码

### css Hack

#### IE浏览器的CSS Hack

* ###### IE 6的CSS Hack
    css名称前面加上下划线`_`,只有IE 6可以识别
    css-hack {
        background-color: red; /* 其他浏览器上显示为红色 */
        _background-color: blue; /* 只有IE 6浏览器上显示为蓝色 */
    }
> 补充：IE 6支持!important，但有个bug，一个样式内重复设了属性，会忽略'!important'

* ###### IE 7的CSS Hack
    IE6、IE7都能够识别加了`+`、`*`或`#`前缀的css属性名称,IE 7不支持`_`前缀
    ``
    .css-hack {
        color: red; /* 其他浏览器上显示为红色 */
        +color: blue; /* 只有 IE 6、IE 7 浏览器上显示为蓝色 */
        _color: red; /* 让 IE 6 复原为之前设置的颜色 */
    }
    ``
    IE 7也支持在选择器前添加*+html,只有IE 7可以识别
    ``
    .css-hack {
        color: red; /* 其他浏览器显示红色 */
    }
    ``
 `+html`
    ``
    .css-hack {
        color: blue; /* 只有IE 7显示蓝色  */
    }
    ``

* ###### IE 8的CSS Hack
    只有IE8支持嵌套如下`@media`类型查询语句：@media \0screen。

    ``
    .css-hack {
        color: red; /* 其他浏览器显示红色 */
    }

    @media \0screen {
        .css-hack { color: blue; } /* 只有IE 8显示蓝色 */
    }
    ``

* ###### IE 9的CSS Hack
    `\0`;      /* ie 8/9*/
    `\9\0`;    /* ie 9*/

* ###### IE 10/11的CSS Hack

    ``
    /*ie11 css hack*/ 
    @media all and (-ms-high-contrast:none) { 
        *::-ms-backdrop, .class名字 { 里面的样式:样式值;} 
    }       /*ie11注意里面的标点符号*/ 
    /*ie10 css hack*/ 
    @media screen and (-ms-high-contrast: active), (-ms-high-contrast: none) { 
        .class名字 { 里面的样式:样式值;} 
    }
    ``

#### FireFox的CSS Hack
    FireFox支持嵌套其专用的css语句：@-moz-document url-prefix()。
    ``
    .css-hack {
        color: red; /* 其他浏览器显示红色 */
    }

    @-moz-document url-prefix() {
        .css-hack {
            color: blue; /* 只有FireFox显示为蓝色 */
        }
    }
    ``

#### Chrome、Safari等Webkit内核的浏览器的CSS Hack
    hrome、Safari等采用webkit内核的浏览器支持媒体类型查询语句：@media screen and (-webkit-min-device-pixel-ratio:0)。

    ``
    .css-hack {
        color: red; /* 其他浏览器显示红色 */
    }

    @media screen and (-webkit-min-device-pixel-ratio:0) { 
        .css-hack {
            color: blue; /* Webkit内核浏览器显示蓝色 */
        }
    }
    ``