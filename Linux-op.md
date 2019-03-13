# バージョン確認

## ディストリビューションのバージョン確認

### EC2

$ cat /etc/cat system-release\
Amazon Linux AMI release 2018.03

### CentOS / RedHat Enterprise

$ cat /etc/redhat-release\
CentOS release 6.7 (Final)

### Ubuntu

$ cat /etc/lsb-release\
DISTRIB_ID=Ubuntu\
DISTRIB_RELEASE=12.04\
DISTRIB_CODENAME=precise\
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

## Linuxカーネルのバージョン確認

### Linuxカーネルのバージョンを確認

$ cat /proc/version\
Linux version 3.10.0-957.1.3.el7.x86_64 (mockbuild@kbuilder.bsys.centos.org) (gcc version 4.8.5 20150623 (Red Hat 4.8.5-36) (GCC) ) #1 SMP Thu Nov 29 14:49:43 UTC 2018

### カーネルのバージョンを確認

$ uname  -r\
3.10.0-957.1.3.el7.x86_64
