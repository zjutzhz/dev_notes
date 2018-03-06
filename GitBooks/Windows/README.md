# Introduction

## 凭据管理
```cmd
rundll32.exe keymgr.dll,KRShowKeyMgr
```
参考：[How do I clear cached credentials from my Windows Profile?](https://security.stackexchange.com/questions/15574/how-do-i-clear-cached-credentials-from-my-windows-profile)

## Windows 下计算 MD5
```cmd
certutil -hashfile filename MD5
certutil -hashfile filename SHA1
certutil -hashfile filename SHA256
```
参考：[Windows下查看文件MD5值](http://blog.csdn.net/xibeichengf/article/details/48750315)
