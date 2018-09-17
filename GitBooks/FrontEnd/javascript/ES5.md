# ES5
## 1. NodeList to Array
```javascript
var list = document.querySelectorAll("ul")
// method 1
var listArray = Array.prototype.slice.call(list)
// method 2
var listArray2 = [].slice.call(list)
```

## 2. get keys of dictionary
```javascript
var a = {"name": "hz"}
var keyArray = Object.keys(a)
```

## 3. json Object 序列化
```
JSON.stringify(res, null, 2); //res是要JSON化的对象，2是spacing
```
参考[在html页面中展示JSON](https://www.jianshu.com/p/04127d74d88c)


## 4. XMLHttpRequest 用法
```javascript
var xhr = new XMLHttpRequest();
//向 server 端获取一张图片
xhr.open('GET', '/path/to/image.png', true);

// 这行是关键！
//将响应数据按照纯文本格式来解析，字符集替换为用户自己定义的字符集
xhr.overrideMimeType('text/plain; charset=x-user-defined');

xhr.onreadystatechange = function(e) {
  if (this.readyState == 4 && this.status == 200) {
    //通过 responseText 来获取图片文件对应的二进制字符串
    var binStr = this.responseText;
    //然后自己再想方法将逐个字节还原为二进制数据
    for (var i = 0, len = binStr.length; i < len; ++i) {
      var c = binStr.charCodeAt(i);
      //String.fromCharCode(c & 0xff);
      var byte = c & 0xff;
    }
  }
};
xhr.send();
```
参考：[你真的会使用XMLHttpRequest吗？](https://segmentfault.com/a/1190000004322487)
2. [XMLHttpRequest Level 2 使用指南](http://www.ruanyifeng.com/blog/2012/09/xmlhttprequest_level_2.html)
3. [XMLHttpRequest2 新技巧](https://www.html5rocks.com/zh/tutorials/file/xhr2/)
