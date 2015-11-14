#mysql
##安装

##字符集 [ref](http://stackoverflow.com/questions/3513773/change-mysql-default-character-set-to-utf-8-in-my-cnf)
```
[mysqld]
collation-server = utf8_unicode_ci
init-connect='SET NAMES utf8'
character-set-server = utf8
```
##创建新数据库
creata database _databasename_

##创建用户并赋予权限 [ref](http://stackoverflow.com/questions/5016505/mysql-grant-all-privileges-on-database)
`grant all privileges on` _databasename_ `to 'username'@'localhost' identified by 'password';`

##权限相关操作[ref](http://serverfault.com/questions/263868/how-to-know-all-users-that-can-access-certain-database-mysql)
```
show processlist;
show grants;
show privileges
```
