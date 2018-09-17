# SED和AWK

## 快速替换文件里的字符
```shell
sed -i "s|\\x1b|,|g" file_name # 替换HEX字符
```