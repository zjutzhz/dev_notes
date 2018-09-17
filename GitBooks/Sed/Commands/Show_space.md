# 特殊打印 l

可用于展示文件里的换行符及制表符，也用于控制一行的输出长度

## l命令语法
```
[address1[,address2]]l [len]
```

## 使用示例
### 显示制表符，换行符
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed 's/ /\t/g' book.txt | sed -n 'l']
1)\tA\tStorm\tof\tSwords,\tGeorge\tR.\tR.\tMartin,\t1216\t$
2)\tThe\tTwo\tTowers,\tJ.\tR.\tR.\tTolkien,\t352\t$
3)\tThe\tAlchemist,\tPaulo\tCoelho,\t197\t$
4)\tThe\tFellowship\tof\tthe\tRing,\tJ.\tR.\tR.\tTolkien,\t432\t$
5)\tThe\tPilgrimage,\tPaulo\tCoelho,\t288\t$
6)\tA\tGame\tof\tThrones,\tGeorge\tR.\tR.\tMartin,\t864$
```
### 控制一行输出长度（长度）
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed -n 'l 30' book.txt ]
1) A Storm of Swords, George \
R. R. Martin, 1216 $
2) The Two Towers, J. R. R. T\
olkien, 352 $
3) The Alchemist, Paulo Coelh\
o, 197 $
4) The Fellowship of the Ring\
, J. R. R. Tolkien, 432 $
5) The Pilgrimage, Paulo Coel\
ho, 288 $
6) A Game of Thrones, George \
R. R. Martin, 864$
```
