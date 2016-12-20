
Example arch-bootstrap playbook
=========

Example playbook utilizing the arch-bootstrap role 




Preparation
------------
To install a new arch box do the following:

- boot the arch installation iso
- Perform the following actions in the console:
 - start sshd
 - set root password
 - install python2
```bash
root@archiso ~ # systemctl start sshd
root@archiso ~ # passwd 
New password: 
Retype new password: 
passwd: password updated successfully
root@archiso ~ # pacman -Sy python2
:: Synchronizing package databases...
 core                                                                122.8 KiB  1949K/s 00:00 [######################################################] 100%
 extra                                                              1746.3 KiB  4.70M/s 00:00 [######################################################] 100%
 community                                                             3.7 MiB  2.89M/s 00:01 [######################################################] 100%
resolving dependencies...
looking for conflicting packages...

Packages (1) python2-2.7.12-2

Total Download Size:   10.75 MiB
Total Installed Size:  71.47 MiB
Net Upgrade Size:       0.00 MiB

:: Proceed with installation? [Y/n] y
:: Retrieving packages...
 python2-2.7.12-2-x86_64                                              10.8 MiB  3.07M/s 00:04 [######################################################] 100%
(1/1) checking keys in keyring                                                                [######################################################] 100%
(1/1) checking package integrity                                                              [######################################################] 100%
(1/1) loading package files                                                                   [######################################################] 100%
(1/1) checking for file conflicts                                                             [######################################################] 100%
(1/1) checking available disk space                                                           [######################################################] 100%
:: Processing package changes...
(1/1) upgrading python2                                                                       [######################################################] 100%
```
- check the ipaddress of the new box

```bash
root@archiso ~ # ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:72:01:c4 brd ff:ff:ff:ff:ff:ff
    inet 1.2.3.4/24 brd 1.2.3.4 scope global enp0s3
       valid_lft forever preferred_lft forever
    inet6 1234:567:89a:1:1245:6789:0abc:def/64 scope global mngtmpaddr noprefixroute dynamic 
       valid_lft 3993sec preferred_lft 3301sec
    inet6 fe80::4816:71c6:8719:9a20/64 scope link 
       valid_lft forever preferred_lft forever
```


Run the playbook
------------
```bash
ansible-playbook -i 1.2.3.4, bootstrap.yml -ku root
```
- enter the root password to connect to the iso boot

- During the playbook run you will be prompted for the root password of the new installation

- After the run  is finished you can reboot the new installation and log in with the given root password.


Author Information
------------------
20-12-2016: Johan Bakker
