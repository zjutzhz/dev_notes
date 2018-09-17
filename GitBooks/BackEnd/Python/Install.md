# Python Install

## Install Pyhton3 by Source on CentOS 7
```
yum install wget gcc make zlib-devel readline-devel
# 解决 import bz2 报错
yum install  bzip2-devel
# 解决 import curses 报错
yum install  ncurses-devel
# 解决 import sqlite3 报错
yum install sqlite-devel
# 解决 _dbm _gdbm 缺失提醒
yum install gdbm-devel
# 解决 _lzma 缺失提醒
yum install xz-devel
# 解决 _tkinter 缺失提醒
yum install tk-devel
# 解决 readline 缺失提醒及方向键行为非预期的问题
yum install readline-devel

yum install gcc-c++

# download
wget https://www.python.org/ftp/python/3.6.5/Python-3.6.5.tgz
tar zxf Python-3.6.5.tgz
cd Python-3.6.5

./configure --prefix=/usr/local/python3.6 --enable-optimizations --enable-shared CFLAGS=-fPIC CXX=/usr/bin/g++
export LD_LIBRARY_PATH=/usr/local/python3.6/lib:$LD_LIBRARY_PATH
ln -s /usr/local/python3.6/bin/python3.6 /usr/local/bin/python3.6
ln -s /usr/local/python3.6/bin/pip3.6 /usr/local/bin/pip3.6
ln -s /usr/local/bin/python3.6 /usr/local/bin/python3
ln -s /usr/local/bin/pip3.6 /usr/local/bin/pip3

```
