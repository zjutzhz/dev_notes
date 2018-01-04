#  环境搭建
## 配置node
```Shell
node config set registry  "http://registry.npm.taobao.org/"
node config set cache "配置cache路径"
```

## windows 7下离线安装node-sass [Ref](https://github.com/lmk123/blog/issues/28)
node-sass安装时需要下载二进制问题，在离线环境下就会安装失败。
解决方案是离线安装
1. 先从[淘宝镜像服务器](https://npm.taobao.org/mirrors/node-sass/) 下载所需版本的二进制文件，例如win32-ia32-48_binding.node
2. 设置环境变量
`SET SASS_BINARY_SITE=PATH_TO_BINARY_FILE`
3. 执行`npm install node-sass`

