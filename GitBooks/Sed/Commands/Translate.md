# 翻译 y

用于把列表1里的字符替换成列表2对应位置的字符。类似于翻译，但是翻译前后文本长度需要一致。而且是字符级别的匹配

## y命令语法
```
[address1[,address2]]y/list-1/list-2/
```

## 使用示例
```
**[terminal]
**[prompt zheng@hz]**[path ~]**[delimiter $ ]**[command echo "0xfe12" | sed 'y/abcdefx/ABCDEFX/']
0xFE12
```
