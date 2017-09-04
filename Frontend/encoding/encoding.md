## 前台页面避免乱码

1. html页面 

html页面的编码方式要与html `<head>`里定义的编码方式一致，如果不一致页面里的非英文字符就会出现乱码。
如下就定义了html的编码方式，同时也定义了html加载js的默认编码方式。

```html
<head>
    <meta charset="GBK">
</head>
```

2. js脚本
对于html 引用的js脚本，如果与html页面的默认编码方式不一致，那么就可能出现乱码，避免的方法是在引用js的时候显式声明js脚本的的编码方式。
```html
<script src="zh_CN.utf8.js" charset="UTF-8"></script>
```


