# 替换 s

用于替换输入的文本

## s命令语法
```
[address1[,address2]]s/pattern/replacement/[flags]
```

## 使用示例
### 匹配第一处替换
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 's/,/|/' book.txt]
1) A Storm of Swords| George R. R. Martin, 1216
2) The Two Towers| J. R. R. Tolkien, 352
3) The Alchemist| Paulo Coelho, 197
4) The Fellowship of the Ring| J. R. R. Tolkien, 432
5) The Pilgrimage| Paulo Coelho, 288
6) A Game of Thrones| George R. R. Martin, 864
```
### 匹配第n处替换
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 's/,/|/2' book.txt]
1) A Storm of Swords, George R. R. Martin| 1216
2) The Two Towers, J. R. R. Tolkien| 352
3) The Alchemist, Paulo Coelho| 197
4) The Fellowship of the Ring, J. R. R. Tolkien| 432
5) The Pilgrimage, Paulo Coelho| 288
6) A Game of Thrones, George R. R. Martin| 864
```

### 整行匹配替换
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 's/,/|/g' book.txt]
1) A Storm of Swords| George R. R. Martin| 1216
2) The Two Towers| J. R. R. Tolkien| 352
3) The Alchemist| Paulo Coelho| 197
4) The Fellowship of the Ring| J. R. R. Tolkien| 432
5) The Pilgrimage| Paulo Coelho| 288
6) A Game of Thrones| George R. R. Martin| 864
```
## 更多示例
### 对匹配行进行替换
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '/The Pilgrimage/ s/,/ | /g' books.txt ]
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage |  Paulo Coelho |  288
6) A Game of Thrones, George R. R. Martin, 864
```
### 只打印替换后的行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '/The Pilgrimage/ s/,/ | /gp' books.txt ]
5) The Pilgrimage |  Paulo Coelho |  288
```
### 打印替换后结果写入文件
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '/The Pilgrimage/ s/,/ | /g w junk.txt' book.txt ]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command cat junk.txt]
5) The Pilgrimage |  Paulo Coelho |  288
```
### 替换时忽略大小写匹配
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n 's/the pilgrimage/THE PILGRIMAGE/g p' book.txt ]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n 's/the pilgrimage/THE PILGRIMAGE/gi p' book.txt]
5) THE PILGRIMAGE, Paulo Coelho, 288  
```
## 高级替换
### 分隔符
如果我们替换的内容里包含保留符号（例如`/`）该怎么办？
一般我们如下操作：
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo "/bin/sed" | sed 's/\/bin\/sed/\/home\/zheng\/src\/sed\/sed-4.2.2\/sed/' ]
/home/zheng/src/sed/sed-4.2.2/sed
```
其实在用s命令匹配时，可以使用其他符号作为间隔符号。例如（`|`， `@`, `^`, `!`)

#### 竖线 ”|”
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo "/bin/sed" | sed 's|/bin/sed|/home/zheng/src/sed/sed-4.2.2/sed|' ]
/home/zheng/src/sed/sed-4.2.2/sed
```
#### AT ”@”
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo "/bin/sed" | sed 's@/bin/sed@/home/zheng/src/sed/sed-4.2.2/sed@' ]
/home/zheng/src/sed/sed-4.2.2/sed
```
#### caret “^”
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo "/bin/sed" | sed 's^/bin/sed^/home/zheng/src/sed/sed-4.2.2/sed^' ]
/home/zheng/src/sed/sed-4.2.2/sed
```
#### 叹号 “!”
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo "/bin/sed" | sed 's!/bin/sed!/home/zheng/src/sed/sed-4.2.2/sed!' ]
/home/zheng/src/sed/sed-4.2.2/sed
```

### 匹配内容获取
使用`&`获取`s`指令`pattern`部分的字符串
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo "One Two Three" | sed 's|\(\w\+\)|[&]|g' ]
[One] [Two] [Three]
```
### 分组处理
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo "Three One Two" | sed 's|\(\w\+\) \(\w\+\) \(\w\+\)|\2 \3 \1|' ]
One Two Three
```
