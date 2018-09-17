# 打印 p

用于打印输入的文本

## p命令语法
```
[address1[,address2]]p
```

## 使用示例
### 直接使用p命令
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 'p' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
6) A Game of Thrones, George R. R. Martin, 864
```

### 配合`-n`去除模式空间输出
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n 'p' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
```

## 更多示例
### 打印第n行
- 打印第一行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '1p' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
```
- 打印最后一行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '$p' book.txt]
6) A Game of Thrones, George R. R. Martin, 864
```

### 打印第n到m行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '2,4p' book.txt]
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
```
### 打印从n行开始的m行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '2,+4p' book.txt]
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
```
### 从n行开始每m行打印一次
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '2~4p' book.txt]
2) The Two Towers, J. R. R. Tolkien, 352
6) A Game of Thrones, George R. R. Martin, 864
```

### 匹配到特定关键字的行打印
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '/Paulo/p' book.txt]
3) The Alchemist, Paulo Coelho, 197
5) The Pilgrimage, Paulo Coelho, 288 
```
