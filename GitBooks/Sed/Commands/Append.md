# 追加 a

用于在指定位置之后追加文本

## a命令语法
```
[address1]a
```

## 使用示例
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 'a NEW LINE' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
NEW LINE
2) The Two Towers, J. R. R. Tolkien, 352
NEW LINE
3) The Alchemist, Paulo Coelho, 197
NEW LINE
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
NEW LINE
5) The Pilgrimage, Paulo Coelho, 288
NEW LINE
6) A Game of Thrones, George R. R. Martin, 864
NEW LINE
```



## 更多示例
### 在指定行后追加（不可加在第一行之前）
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '1a NEW LINE' book.txt]
1) A Storm of Swords| George R. R. Martin, 1216
NEW LINE
2) The Two Towers| J. R. R. Tolkien, 352
3) The Alchemist| Paulo Coelho, 197
4) The Fellowship of the Ring| J. R. R. Tolkien, 432
5) The Pilgrimage| Paulo Coelho, 288
6) A Game of Thrones| George R. R. Martin, 864
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '0a NEW LINE' book.txt]
**[error sed: -e expression #1, char 2: invalid usage of line address 0]
```
### 在最后行后追加
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '$a NEW LINE' book.txt]
1) A Storm of Swords| George R. R. Martin, 1216
2) The Two Towers| J. R. R. Tolkien, 352
3) The Alchemist| Paulo Coelho, 197
4) The Fellowship of the Ring| J. R. R. Tolkien, 432
5) The Pilgrimage| Paulo Coelho, 288
6) A Game of Thrones| George R. R. Martin, 864
NEW LINE
```
### 在匹配行后追加
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '/The/a NEW LINE' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
NEW LINE
3) The Alchemist, Paulo Coelho, 197 
NEW LINE
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
NEW LINE
5) The Pilgrimage, Paulo Coelho, 288
NEW LINE
6) A Game of Thrones, George R. R. Martin, 864
```
