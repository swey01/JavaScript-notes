# 在 HTML 中使用 JavaScript 

## \<script>元素
    在HTML中插入JavaScript的主要方法。使用方式：直接嵌入和包含外部JavaScript文件

* 属性：
    * asyns：可选，标识立即下载脚本，不妨碍页面中的其他操作（下载其他资源或等待加载其他脚本），只对外部文件有效。
    * charset：可选，表示通过src属性指定的代码的字符集。大多数浏览器会忽略他的值。
    * defer：可选，表示脚本延迟到文档完全被解析和显示之后在执行。只对外部脚本文件有效。IE及更早也支持。
    * src：可选，表示外部文件的地址
    * type：可选，language（已废弃）的替代属性，表示脚本语言的内容类型。默认值‘text/JavaScript’。实际‘text/JavaScript’和‘text/ecmascript’已经不推荐使用，服务器在传送时使用的是‘application/x-JavaScript’（但可能导致脚本被忽略），非IE还可以使用‘application/x-JavaScript’和‘ecmascript’。

    JavaScript代码从上往下依次执行，
    不能出现‘<\/script>’字符串，会抛出错误。该标签的一个结束标签。通过`\`转义。
    带src属性，script标签中间不能有代码块。会被忽略

    ### 标签位置
    传统放在\<head>元素中,在\<head>元素中意味着必须等所有的JavaScript代码下载解析完毕才能加载页面内容，会造成明显的加载延迟。
    放在\<body>内容后面

    ### 延迟脚本
    defer属性，脚本会被延迟到整个页面都解析完毕后再执行。
    只使用外部脚本文件
    立即下载文件，但是延迟加载
    多个延迟脚本按照规范先后顺序执行，defer会先于DOMCenrentLoaded事件执行。
    凡是有万一，在实际中，不一定按照顺序执行，也不一定先于DOMContentLoaded事件触发前执行，因此一个defer就好

    ### 异步脚本
    asynsc属性，跟defer类型，只使用外部脚本文件
    不同，不保证按照指定的先后顺序执行，目的的不让页面等待不同的脚本下载和执行，能异步加载页面其他内容。
    一定在load事件前执行，但可能在DOMContentLoaded事件之前或之后

## 嵌入代码与外部文件

    使用外部文件的优点:
    1、可维护性：方便管理
    2、可缓存：同个JavaScript文件不同页面引用，只需下载一次
    3、适应未来

> DOMContentLoaded与load的区别
    先触发DOMContentLoaded事件，后触发load事件
    DOMContentLoaded是DOM加载完毕触发，不需要等待图片等其他资源加载完毕，但是遇到js脚本解析会中断，处理完脚本才能继续。
    load需要等待页面所有的资源（图片，音频，视频等）加载完才会触发

>onload和ready的区别
    onload需要等待页面所有的资源加载完毕触发，页面只能使用一次，多个后面只执行最后一个
    ready只需要等待文档结构加载完毕，可以多次使用


