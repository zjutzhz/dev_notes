# 执行 e

在指定位置执行命令行

## 命令语法
```
[address1[,address2]]e [command]
```

## 使用示例
### 在指定位置执行命令行
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '3 e date' book.txt]
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
2018年 07月 06日 星期五 12:21:46 CST
3) The Alchemist, Paulo Coelho, 197
4) The Fellowship of the Ring, J. R. R. Tolkien, 432
5) The Pilgrimage, Paulo Coelho, 288
6) A Game of Thrones, George R. R. Martin, 864
```
### 执行文件里的语句
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command cat script.txt]
echo "LINE TWO"
date
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command  sed 'e' script.txt]
LINE TWO
2018年 07月 06日 星期五 12:29:26 CST
```
