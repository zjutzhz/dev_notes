# Nginx
## 路径匹配

### location：http核心模块

语法：`location [=|~|~*|^~|@] /uri/ { ... }`

默认值：no

使用字段：server

这个参数根据URI的不同需求来进行配置，可以使用字符串与正则表达式匹配，如果要使用正则表达式，你必须指定下列前缀：

1. ~* 不区分大小写。
2. ~ 区分大小写。

要确定该指令匹配特定的查询，程序将首先对字符串进行匹配，字符串匹配将作为查询的开始，最确切的匹配将被使用。然后，正则表达式的匹配查询开始，匹配查询的第一个正则表达式找到后会停止搜索，如果没有找到正则表达式，将使用字符串的搜索结果。

在一些操作系统，如Mac OS X和Cygwin，字符串将通过不区分大小写的方式完成匹配（0.7.7），但是，比较仅限于单字节的语言环境。

正则表达式可以包含捕获（0.7.40），并用于其它指令中。

可以使用“^~”标记禁止在字符串匹配后检查正则表达式，如果最确切的匹配location有这个标记，那么正则表达式不会被检查。

使用“=”标记可以在URI和location之间定义精确的匹配，在精确匹配完成后并不进行额外的搜索，例如有请求“/”发生，则可以使

用“location = /”来加速这个处理。
即使没有“=”和“^~”标记，精确的匹配location在找到后同样会停止查询。

下面是各种查询方式的总结：
1. 前缀“=”表示精确匹配查询，如果找到，立即停止查询。
2. 指令仍然使用标准字符串，如果匹配使用“^~”前缀，停止查询。
3. 正则表达式按照他们在配置文件中定义的顺序。
4. 如果第三条产生一个匹配，这个匹配将被使用，否则将使用第二条的匹配。

例:
```ini
location  = / {  
  # 只匹配 / 的查询.  
  [ configuration A ]  
}  
location  / {  
  # 匹配任何以 / 开始的查询，但是正则表达式与一些较长的字符串将被首先匹配。  
  [ configuration B ]  
}  
location ^~ /images/ {  
  # 匹配任何以 /images/ 开始的查询并且停止搜索，不检查正则表达式。  
  [ configuration C ]  
}  
location ~* \.(gif|jpg|jpeg)$ {  
  # 匹配任何以gif, jpg, or jpeg结尾的文件，但是所有 /images/ 目录的请求将在Configuration C中处理。  
  [ configuration D ]  
}
```
各请求的处理如下例：
```
·/ -> configuration A
·/documents/document.html -> configuration B
·/images/1.gif -> configuration C
·/documents/1.jpg -> configuratio
```
注意你可以以任何顺序定义这4个配置并且匹配结果是相同的，但当使用嵌套的location结构时可能会将配置文件变的复杂并且产生一些比较意外的结果。

### expires:http头处理模块

语法：`expires [time|@time-of-day|epoch|max|off]`

默认值：expires off

使用字段：http, server, location

这个指令控制是否在应答中标记一个过期时间，如果是，如何标记。
1. off 将禁止修改头部中的 Expires和Cache-Control字段。
2. epoch 将Expires头设置为1 January, 1970 00:00:01 GMT。
3. max 将Expires头设置为31 December 2037 23:59:59 GMT，将Cache-Control最大化到10 years。
4. 如果将指令设置为一个不带@标记的值，那么过期时间将是应答时间的相对时间（如果这个时间在“modified”之前），或者是文件的修改时间（当"modified"存在，在版本0.7.0和0.6.32可用），并且可以指定一个负的时间，它将Cache-Control头设置为no-cache比较。
5. 如果指令的值被设置为一个带@标记的值，那么将指定一个绝对的time-of-day过期时间，可以指定两种格式分别为Hh或Hh:Mm，其中H的大小范围为0到24，M的大小范围为0到59（在0.7.9和0.6.34可用）。
一个非负的时间值将Cache-Control头设置为 max-age = #，#将适当的换算为秒数。
注意：expires仅仅适用于200, 204, 301, 302,和304应答


重要补充内容:

URL重写模块
### break

语法：break

默认值：none

使用字段：server, location, if

完成当前设置的规则，停止执行其他的重写指令。

### if

语法：  `if (condition) { ... } `

默认值：none

使用字段：server, location

判断一个条件，如果条件成立，则后面的大括号内的语句将执行，相关配置从上级继承。
可以在判断语句中指定下列值：

1. 一个变量的名称；不成立的值为：空字符传""或者一些用“0”开始的字符串。
2. 一个使用=或者!=运算符的比较语句。
3. 使用符号`~*`和`~`模式匹配的正则表达式：
```
·~为区分大小写的匹配。
·~*不区分大小写的匹配（firefox匹配FireFox）。
·!~和!~*意为“不匹配的”。
·使用-f和!-f检查一个文件是否存在。
·使用-d和!-d检查一个目录是否存在。
·使用-e和!-e检查一个文件，目录或者软链接是否存在。
·使用-x和!-x检查一个文件是否为可执行文件。
```


### return
语法：return code

默认值：none

使用字段：server, location, if

这个指令结束执行配置语句并为客户端返回状态代码，可以使用下列的值：204，400，402-406，408，410, 411, 413, 416与500-504。此外，非标准代码444将关闭连接并且不发送任何的头部。



### rewrite

语法：`rewrite regex replacement flag `

默认值：none

使用字段：server, location, if
按照相关的正则表达式与字符串修改URI，指令按照在配置文件中出现的顺序执行。
注意重写规则只匹配相对路径而不是绝对的URL，如果想匹配主机名，可以加一个if判断，如：

```
if ($host ~* www\.(.*)) {  
  set $host_without_www $1;  
  rewrite ^(.*)$ http://$host_without_www$1 permanent; # $1为'/foo'，而不是'www.mydomain.com/foo'  
}
```
可以在重写指令后面添加标记。
如果替换的字符串以`http://`开头，请求将被重定向，并且不再执行多余的rewrite指令。

标记可以是以下的值：
```
·last - 完成重写指令，之后搜索相应的URI或location。
·break - 完成重写指令。
·redirect - 返回302临时重定向，如果替换字段用http://开头则被使用。
·permanent - 返回301永久重定向。
```
参考：[nginx配置六（URL匹配配置）](http://lobert.iteye.com/blog/1933417
  )
