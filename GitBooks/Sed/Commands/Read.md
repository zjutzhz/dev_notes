# 读入 r

可用于在指定位置插入读入文件的内容

## 命令语法
```
[address]r file
```

## 使用示例
### 在指定位置插入文件的内容
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command cat script.txt ]
LINE ONE
echo "LINE TWO"
date
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '1r script.txt' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
LINE ONE
echo "LINE TWO"
date
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
```
