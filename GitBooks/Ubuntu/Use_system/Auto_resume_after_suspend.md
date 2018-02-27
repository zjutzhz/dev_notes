# 待机自动苏醒

## 问题现象

待机之后立即苏醒，无法待机

## 解决方案
使用`acpitool`工具

### 1. 安装`acpitool`
```
sudo apt-get install acpitool
```

### 2. 查看清单
```
sudo acpitool -w
```
例如：
```
31. GLAN	  S4	*disabled  pci:0000:00:19.0
32. EHC1	  S0	*disabled  pci:0000:00:1d.0
33. EHC2	  S0	*disabled  pci:0000:00:1a.0
35. HDEF	  S4	*disabled  pci:0000:00:1b.0
36. LID0	  S3	*enabled   platform:PNP0C0D:00
37. PBTN	  S3	*enabled   platform:PNP0C0C:00
```

### 3. 关闭除platform以外的
```
sudo acpitool -W 编号
```

### 4. 其他查看电源情况的方法
```
cat /proc/acpi/wakeup
```

## 参考文档
1. [Why does my laptop resume immediately after suspend](https://askubuntu.com/questions/144932/why-does-my-laptop-resume-immediately-after-suspend)
