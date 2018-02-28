1. change nohup output name [[Ref]](https://stackoverflow.com/questions/4549489/can-i-change-the-name-of-nohup-out)

```Shell
nohup some_command &> nohup2.out&
```

2. Service manager
`sysv-rc-conf`

3. write a start up shell
* put script in init.d/
* put variable in /etc/default/
* run update-rc.d to enable service

4. write a service
[ref](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/sect-managing_services_with_systemd-unit_files)