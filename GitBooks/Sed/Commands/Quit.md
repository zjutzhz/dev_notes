# 退出 q

可用于定义退出逻辑，也可用于定义退出返回值

## 命令语法
```
[address]q
[address]q [value]
```

## 使用示例
### 满足条件退出处理
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '3q' book.txt ]
1) A Storm of Swords, George R. R. Martin, 1216
2) The Two Towers, J. R. R. Tolkien, 352
3) The Alchemist, Paulo Coelho, 197
```
### 自定义Retrun Code
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command sed '1q 10' book.txt ]
1) A Storm of Swords, George R. R. Martin, 1216
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo $? ]
10
```
