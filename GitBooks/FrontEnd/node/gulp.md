# gulp

##  Error in call `gulp watch`
### 现象
```
Error: watch /conductor/ui/dist/public/fonts ENOSPC
    at exports._errnoException (util.js:1026:11)
    at FSWatcher.start (fs.js:1429:19)
    at Object.fs.watch (fs.js:1456:11)
    at createFsWatchInstance
    ...
```
### 解决
```shell
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
```
### 参考
1. [gulp watch error (ENOSPC)](https://github.com/gulpjs/gulp/issues/217)
2. [gulp watch fails with error: Error: watch ... ENOSPC](https://gist.github.com/brunoleles/ee689cac84599ab78e415748c241ccfc)
