# 添加根证书

Given a CA certificate file `foo.crt`, follow these steps to install it on Ubuntu:

Create a directory for extra CA certificates in `/usr/share/ca-certificates`:

```shell
sudo mkdir /usr/share/ca-certificates/extra
```
Copy the CA .crt file to this directory:

```shell
sudo cp foo.crt /usr/share/ca-certificates/extra/foo.crt
```

Let Ubuntu add the .crt file's path relative to 
`/usr/share/ca-certificates` to `/etc/ca-certificates.conf`:

```shell
sudo dpkg-reconfigure ca-certificates
```

To do this non-interactively, run:
```shell
sudo update-ca-certificates
```

[参考资料](https://askubuntu.com/questions/73287/how-do-i-install-a-root-certificate)