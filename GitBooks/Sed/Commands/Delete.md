# 删除 d

用于删除输入的文本

## d命令语法
```
[address1[,address2]]d
```

## 使用示例
### 直接使用d命令
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 'd' book.txt]
```

## 更多示例
### 删除特定行
- 删除第4行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '4d' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
```
- 删除最后一行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '$d' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
```

### 删除第n到m行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '2,4d' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
```
### 删除从n行开始的m行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '2,+4d' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
```
### 从n行开始每m行删除一次
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '2~4d' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
```

### 删除匹配到特定关键字的行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n '/The/d' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
6) A Game of Thrones, George R. R. Martin, 864
```
