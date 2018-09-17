# 命令格式及选项

## 命令格式
```
sed [options] 'command' file(s)
sed [options] -f scriptfile file(s)
```
## 命令选项
|选项|含义|
|-----|-----|
|-n, --quiet, --silent| 安静模式，仅显示script处理后的结果 |
|-e script, --expression=script|以选项中的指定的script来处理输入的文本文件|
|-f script-file, --file=script-file|以选项中指定的script文件来处理输入的文本文件|
|-i[SUFFIX], --in-place[=SUFFIX]|直接修改文件，SUFFIX可以传入备份文件名|
