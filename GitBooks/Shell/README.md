# Introduction

## build
```
./make_standalone_toolchain.py  --arch arm --install-dir ~/Android/arm32 --api 24
```


```
export CFLAGS="-pie -fPIC"
export LDFLAGS="-pie -fPIC"
make -B CC=/home/zheng/Android/arm32/bin/arm-linux-androideabi-gcc
```
