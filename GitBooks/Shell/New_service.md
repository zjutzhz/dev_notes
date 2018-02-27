# 新建启动服务

## 1. 编写启动脚本
```shell
#!/bin/sh
### BEGIN INIT INFO
# Provides:          aria2
# Required-Start:    $remote_fs $network
# Required-Stop:     $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Aria2 Downloader
### END INIT INFO

case "$1" in
start)

echo -n "Starting aria2c"
sudo -u xbian aria2c --conf-path=/etc/aria2/aria2.conf -D
#sudo -u后面的是你正在使用的用户名，因为我用的XBian，用debian的是pi（没改用户的话）
;;
stop)

echo -n "Shutting down aria2c "
killall aria2c
;;
restart)
# 这里需要修改，有问题
killall aria2c
sudo -u xbian aria2c --conf-path=/etc/aria2/aria2.conf -D
#同上面的一样，根据自己的用户名改xbian。
;;
esac
exit
```

## 2. 自动生成启动项
```shell
sudo update-rc.d aria2c defaults
```

## 3. 参考资料
- [参考](https://www.jianshu.com/p/b2649d073741)
