# 插入 i

用于在指定位置前插入文本

## i命令语法
```
[address1]i
```

## 使用示例
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 'i NEW LINE' book.txt]
NEW LINE
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
```

## 更多示例
### 用于在指定位置前插入文本
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '1i NEW LINE' book.txt]
NEW LINE
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
```
