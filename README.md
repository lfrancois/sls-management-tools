# sls-management-tools
ipmitool &amp; cxmanage for SLS (SilverLining Systems) product line

## This step-by-step guide will work on ubuntu but also on any linux or unix (tested on OS X)
```
root@ubuntu:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty
root@ubuntu:~#
```

## clone the SLS management tool git repository
```
root@ubuntu:~# git clone https://github.com/lfrancois/sls-management-tools.git
```

## check all the files are cloned from git
```
root@ubuntu:~# cd sls-management-tools/
root@ubuntu:~/sls-management-tools# ls
cxmanage  ipmitool  pyipmi  README.md
root@ubuntu:~/sls-management-tools#
```

## configure and install ipmitool 

This is a specific version of ipmitool for the SLS platform.

```
root@ubuntu:~/sls-management-tools# cd pyipmi/
root@ubuntu:~/sls-management-tools/pyipmi# python setup.py install
root@ubuntu:~/sls-management-tools/pyipmi# cd ../ipmitool/
root@ubuntu:~/sls-management-tools/ipmitool# ./configure
root@ubuntu:~/sls-management-tools/ipmitool# make clean
root@ubuntu:~/sls-management-tools/ipmitool# make all
root@ubuntu:~/sls-management-tools/ipmitool# make install
root@ubuntu:~/sls-management-tools/ipmitool# cd ../cxmanage/
```

## configure and install cxmanage 
```
root@ubuntu:~/sls-management-tools/cxmanage# python setup.py install
```

## confirm both tools are available on your system
```
root@ubuntu:~# which ipmitool
/usr/local/bin/ipmitool
root@ubuntu:~# which cxmanage
/usr/local/bin/cxmanage
root@ubuntu:~#
```

## check they work correctly
```
root@ubuntu:~# cxmanage -a macaddrs 172.30.1.51 | head
Getting MAC addresses...
1 successes  |  0 errors  |  0 nodes left  |  . 

MAC addresses from 172.30.1.51
Node 0, Port 0: 30:0e:d5:c7:51:d3
Node 0, Port 1: 30:0e:d5:c7:51:d4
Node 0, Port 2: 30:0e:d5:c7:51:d5
Node 1, Port 0: 30:0e:d5:c7:51:d6
Node 1, Port 1: 30:0e:d5:c7:51:d7
Node 1, Port 2: 30:0e:d5:c7:51:d8
root@ubuntu:~#
```
