## Content-type 简介

### 1. Content-Type

Content-Type是Http报文头的重要组成部分。
在服务器返回浏览器的响应报文里，Content-Type标头告诉客户端实际返回的内容类型。
在浏览器发给服务器的请求报文里，Content-Type标头告诉服务器发送的数据类型。

一般Content-Type由两部分组成：MIMETYPE 和 charset。例如：

`Content-Type: text/html; charset=utf-8`

而当通过浏览器上传文件时，Content-Type为：

`Content-Type: multipart/form-data; boundary=something`

其中boundary部分是用于分隔提交的表单里各个部分。

### 2. 默认的MIMETYPE

#### 2.1 text/plain 
text/plain 表示文本文件的默认值。一个文本文件应当是人类可读的，并且不包含二进制数据。

#### 2.2 application/octet-stream 
application/octet-stream 表示所有其他情况的默认值。一种未知的文件类型应当使用此类型。浏览器在处理这些文件时会特别小心, 试图避免用户的危险行为.

### 3. 常见的MIMETYPE 

|扩展名|类型|MIMETYPE|
|----|----|----|
|无|普通文本|text/plain|
|.html|超文本标记语言|text/html|
|.css||text/css|
|.csv|CSV文件|text/csv|
|.xml|XML文件|application/xml|
|.json|JSON|application/json|
|.zip|ZIP压缩包|application/zip|
|.pdf|PDF文件|application/pdf|
|.jpg|JPEG图片|image/jpeg|
|.gif|GIF图片|image/gif|

### 4. 使用案例

对于相同的Response HTTP报文体，如果使用不同的Content-Type，那么不同的浏览可能会出现不同的处理结果。

例如服务器收到前端POST表单后，要返回json字符串到表单所在form的隐藏iframe里.

* 如果使用默认的MIMETYPE（text/plain），那么前端可以通过JSON.parse(response)把Json 字符串解析成浏览器对象。
* 如果使用的是（application/json）,那么在IE浏览期里就会被识别成下载，把json的内容当成一个文件下载下来。





