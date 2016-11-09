# HTML规范

##### **尽量遵循 HTML 标准和语义，但是不要以牺牲实用性为代价。任何时候都要尽量使用最少的标签并保持最小的复杂度。**

## 通用约定

* 自闭合（self-closing）标签，无需闭合 ( 例如： img input br hr 等 )
* 可选的闭合标签(closing tag),需闭合(例如:`</li>`或 `</body>`)
* 尽量减少标签数量

## Class 与 ID
* class 应以功能或内容命名，不以表现形式命名
* class 与 id 单词字母小写，多个单词组成时，采用中划线-分隔
* class 与 id 单词字母小写，多个单词组成时根据BEM命名法来命名
* 使用唯一的 id 作为 Javascript hook, 同时避免创建无样式信息的 class

```HTML
<!-- Not recommended -->
<div class="j-hook left contentWrapper"></div>

<!-- Recommended -->
<div id="j-hook" class="sidebar content-wrapper"></div>
```

## 属性顺序
HTML 属性应该按照特定的顺序出现以保证易读性
* id
* class
* name
* data-xxx
* src,for,type,href
* title,alt
* aria-xxx,role

```HTML
<a id="..." class="..." data-modal="toggle" href="###"></a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

## 引号
属性的定义，统一使用双引号。(`HTML` 与 `CSS`引号统一单引号 )

```HTML
<!-- Not recommended -->
<span id='j-hook' class=text>Google</span>

<!-- Recommended -->
<span id="j-hook" class="text">Google</span>
```

## 嵌套
`a` 不允许嵌套 `div`这种约束属于`语义嵌套约束`

与之区别的约束还有`严格嵌套约束`，比如`a` 不允许嵌套 `a`

严格嵌套约束在所有的浏览器下都不被允许；

而语义嵌套约束，浏览器大多会容错处理，生成的文档树可能相互不太一样。

### 语义嵌套约束
* `<li>` 用于 `<ul>` 或 `<ol>` 下
* `<dd>`, `<dt>` 用于 `<dl>` 下
* `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<td>` 用于 <table> 下

### 严格嵌套约束
* inline-Level 元素，仅可以包含文本或其它 inline-Level 元素
* `<a>`里不可以嵌套交互式元素`<a>`、`<button>`、`<select>`等
* `<p>`里不可以嵌套块级元素`<div>`、`<h1>`~`<h6>`、`<p>`、`<ul>/<ol>`/`<li>`、`<dl>/<dt>`/`<dd>`、`<form>`等

![](http://i.imgur.com/D5U4DKj.png)

### 示例
将你构建的页面当作一本书，将标签的语义对应的其功能和含义
* 书的名称：`<h1>`
* 书的每个章节标题: `<h2>`
* 章节内的文章标题: `<h3>`
* 小标题/副标题: `<h4>` `<h5>` `<h6>`
* 章节的段落: `<p>`

***

# HEAD规范

## 文档类型
为每个 HTML 页面的第一行添加标准模式（standard mode）的声明， 这样能够确保在每个浏览器中拥有一致的表现。

```html
<!DOCTYPE html>
```

## 语言属性
为什么使用 lang="zh-cmn-Hans" 而不是我们通常写的 lang="zh-CN" 呢? 请参考知乎上的讨论: [网页头部的声明应该是用 lang="zh" 还是 lang="zh-cn"？](https://www.zhihu.com/question/20797118 "网页头部的声明应该是用 lang="zh" 还是 lang="zh-cn"？")

```html
<!-- 中文 -->
<html lang="zh-Hans">

<!-- 简体中文 -->
<html lang="zh-cmn-Hans">

<!-- 繁体中文 -->
<html lang="zh-cmn-Hant">

<!-- English -->
<html lang="en">
```

## 字符编码
* 以无 BOM 的 utf-8 编码作为文件格式;
* 指定字符编码的 meta 必须是 head 的第一个直接子元素

```HTML
<html>
    <head>
        <meta charset="utf-8">
            ......
    </head>
    <body>
        ......
    </body>
</html>
```

## IE 兼容模式
优先使用最新版本的IE 和 Chrome 内核
```html
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
```

## SEO 优化

```html
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <!-- SEO -->
    <title>Style Guide</title>
    <meta name="keywords" content="your keywords">
    <meta name="description" content="your description">
    <meta name="author" content="author,email address">
</head>
```

## viewport
* `viewport`: 一般指的是浏览器窗口内容区的大小，不包含工具条、选项卡等内容
* `width`: 浏览器宽度，输出设备中的页面可见区域宽度
* `device-width`: 设备分辨率宽度，输出设备的屏幕可见宽度
* `initial-scale`: 初始缩放比例
* `maximum-scale`: 最大缩放比例

为移动端设备优化，设置可见区域的宽度和初始缩放比例
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## iOS 图标
* apple-touch-icon 图片自动处理成圆角和高光等效果
* apple-touch-icon-precomposed 禁止系统自动添加效果，直接显示设计原图

```html
<!-- iPhone 和 iTouch，默认 57x57 像素，必须有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png">

<!-- iPad，72x72 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-72x72-precomposed.png" sizes="72x72">

<!-- Retina iPhone 和 Retina iTouch，114x114 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-114x114-precomposed.png" sizes="114x114">

<!-- Retina iPad，144x144 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-144x144-precomposed.png" sizes="144x144">
```

## favicon
在未指定 favicon 时，大多数浏览器会请求 Web Server 根目录下的 favicon.ico 。为了保证 favicon 可访问，避免404，必须遵循以下两种方法之一：
* 在 Web Server 根目录放置 favicon.ico 文件
* 使用 link 指定 favicon
```html
<link rel="shortcut icon" href="path/to/favicon.ico">
```

## HEAD 模板
```html
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <title>Style Guide</title>
    <meta name="description" content="不超过150个字符">
    <meta name="keywords" content="">
    <meta name="author" content="name, email@gmail.com">

    <!-- 为移动设备添加 viewport -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- iOS 图标 -->
    <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png">

    <link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml" />
    <link rel="shortcut icon" href="path/to/favicon.ico">
</head>
```
