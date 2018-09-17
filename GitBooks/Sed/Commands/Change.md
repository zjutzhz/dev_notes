# 修改 c

用于在指定位置覆盖修改后的文本

## c命令语法
```
[address1[,address2]]c
```

## 使用示例
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 'c NEW LINE' book.txt]
NEW LINE
NEW LINE
NEW LINE
NEW LINE
NEW LINE
NEW LINE
```

## 更多示例
### 修改指定行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '3c NEW LINE' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
NEW LINE
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
```
