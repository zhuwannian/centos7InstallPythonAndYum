# centos7卸载Python2.7.5和yum,安装Python2.7.5和yum log[另免责 后果与本人无关 haha]

 ## 这是没python了

```
[root@xiaoming ~]# yum
-bash: /usr/bin/yum: /usr/bin/python: bad interpreter: No such file or directory
[root@xiaoming ~]# python -V
-bash: /usr/bin/python: No such file or directory
```

 ## 这是没yum了

 ```
 [root@xiaoming ~]# yum
 -bash: /usr/bin/yum: No such file or directory
 ```

# 查看centos版本

## 看64位还是32位
```sh
[root@xiaoming ~]# file /bin/cat
/bin/cat: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.32
[root@xiaoming ~]# uname -m
x86_64
[root@xiaoming ~]# uname -a
Linux VM_0_14_centos 3.10.0-1127.8.2.el7.x86_64 #1 SMP Tue May 12 16:57:42 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
[root@xiaoming ~]# echo $HOSTTYPE
x86_64
[root@xiaoming ~]# getconf LONG_BIT
64
[root@xiaoming ~]# getconf WORD_BIT
32
```

## 看版本号

```sh

[root@xiaoming ~]# rpm -q centos-release
centos-release-7-8.2003.0.el7.centos.x86_64
[root@xiaoming ~]# cat /etc/redhat-release
CentOS Linux release 7.8.2003 (Core)
[root@xiaoming ~]# uname -r
3.10.0-1127.8.2.el7.x86_64
[root@xiaoming ~]# cat /etc/centos-release
CentOS Linux release 7.8.2003 (Core)
[root@xiaoming ~]# cat /proc/version
Linux version 3.10.0-1127.8.2.el7.x86_64 (mockbuild@kbuilder.bsys.centos.org) (gcc version 4.8.5 20150623 (Red Hat 4.8.5-39) (GCC) ) #1 SMP Tue May 12 16:57:42 UTC 2020


```



# 卸载Python[谨慎操作]

```sh

[root@xiaoming ~]# whereis python
	python: /usr/bin/python /usr/bin/python2.7-config /usr/bin/python2.7 /usr/lib/python2.7 /usr/lib64/python2.7 /etc/python /usr/include/python2.7 /usr/share/man/man1/python.1.gz
[root@xiaoming ~]# which python
	/usr/bin/python
[root@xiaoming ~]# rpm -qa|grep python
	python-chardet-2.2.1-3.el7.noarch
	libxml2-python-2.9.1-6.el7.4.x86_64
	python-kitchen-1.1.1-5.el7.noarch
	python-rpm-macros-3-32.el7.noarch
	python-libs-2.7.5-88.el7.x86_64
	python-urlgrabber-3.10-10.el7.noarch
	python-srpm-macros-3-32.el7.noarch
	python-pillow-2.0.0-20.gitd1c6db8.el7_7.x86_64
	python-pycurl-7.19.0-19.el7.x86_64
	rpm-python-4.11.3-43.el7.x86_64
	python2-rpm-macros-3-32.el7.noarch
	libxslt-python-1.1.28-5.el7.x86_64
	python-iniparse-0.4-9.el7.noarch
	python-devel-2.7.5-88.el7.x86_64
	python-2.7.5-88.el7.x86_64
[root@xiaoming ~]# rpm -qa|grep python|xargs rpm -e --allmatches --nodeps
[root@xiaoming ~]# whereis python|xargs rm -fr
[root@xiaoming ~]# whereis python
[root@xiaoming ~]# 


```


# 卸载yum[谨慎操作]

```sh

[root@xiaoming ~]# whereis yum
	yum: /usr/bin/yum /etc/yum /etc/yum.conf /usr/share/man/man8/yum.8
[root@xiaoming ~]# which yum
	/usr/bin/yum
[root@xiaoming ~]# rpm -qa|grep yum
	yum-metadata-parser-1.1.4-10.el7.x86_64
	yum-utils-1.1.31-54.el7_8.noarch
	yum-3.4.3-161.el7.centos.noarch
	yum-plugin-fastestmirror-1.1.31-54.el7_8.noarch
	yum-plugin-fastestmirror-1.1.31-50.el7.noarch
	yum-3.4.3-167.el7.centos.noarch
[root@xiaoming ~]# rpm -qa|grep yum|xargs rpm -e --allmatches --nodeps
[root@xiaoming ~]# whereis yum|xargs rm -fr
[root@xiaoming ~]# whereis yum
[root@xiaoming ~]# 

```


# 下载

[python与yum的rpm包下载源二选一即可](http://mirrors.aliyun.com/centos)
[python与yum的rpm包下载源二选一即可](http://mirrors.163.com/centos)

```html

由上得知本服务器为 centos7 64位的7.8.2003版本 其RPM包具体位置如下
http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages

```

# 需要下载的RPM包[由于源中版本会更新，下载时具体请查看版本再下载下来]

```html
python-2.7.5-88.el7.x86_64.rpm         python-iniparse-0.4-9.el7.noarch.rpm   python-pycurl-7.19.0-19.el7.x86_64.rpm
python-chardet-2.2.1-3.el7.noarch.rpm  python-kitchen-1.1.1-5.el7.noarch.rpm
python-libs-2.7.5-88.el7.x86_64.rpm    python-urlgrabber-3.10-10.el7.noarch.rpm
python-devel-2.7.5-88.el7.x86_64.rpm   python-setuptools-0.9.8-7.el7.noarch.rpm


rpm-python-4.11.3-43.el7.x86_64.rpm


yum-3.4.3-167.el7.centos.noarch.rpm          yum-plugin-aliases-1.1.31-53.el7.noarch.rpm        yum-plugin-protectbase-1.1.31-53.el7.noarch.rpm
yum-metadata-parser-1.1.4-10.el7.x86_64.rpm  yum-plugin-fastestmirror-1.1.31-53.el7.noarch.rpm  yum-utils-1.1.31-53.el7.noarch.rpm

[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-2.7.5-88.el7.x86_64.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-iniparse-0.4-9.el7.noarch.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-pycurl-7.19.0-19.el7.x86_64.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-chardet-2.2.1-3.el7.noarch.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-kitchen-1.1.1-5.el7.noarch.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-libs-2.7.5-88.el7.x86_64.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-urlgrabber-3.10-10.el7.noarch.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-devel-2.7.5-88.el7.x86_64.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/python-setuptools-0.9.8-7.el7.noarch.rpm

[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/rpm-python-4.11.3-43.el7.x86_64.rpm

[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-3.4.3-167.el7.centos.noarch.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-plugin-aliases-1.1.31-53.el7.noarch.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-plugin-protectbase-1.1.31-53.el7.noarch.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-metadata-parser-1.1.4-10.el7.x86_64.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-plugin-fastestmirror-1.1.31-53.el7.noarch.rpm
[root@xiaoming ~]# wget http://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-utils-1.1.31-53.el7.noarch.rpm


```

#修改名称

```sh

[root@xiaoming ~]# mv python-devel-2.7.5-88.el7.x86_64.rpm      python-devel-2.7.5-88.el7.x86_64

[root@xiaoming ~]# mv python-setuptools-0.9.8-7.el7.noarch.rpm      python-setuptools-0.9.8-7.el7.noarch

[root@xiaoming ~]# mv yum-utils-1.1.31-53.el7.noarch.rpm            yum-utils-1.1.31-53.el7.noarch

[root@xiaoming ~]# mv yum-plugin-aliases-1.1.31-53.el7.noarch.rpm   yum-plugin-aliases-1.1.31-53.el7.noarch

```

# 安装Python

```sh

[root@xiaoming ~]# rpm -Uvh --replacepkgs python*.rpm


```

# 安装rpm-python

```sh

[root@xiaoming ~]# rpm -Uvh --replacepkgs rpm-python*.rpm

```

# 安装yum

```sh

[root@xiaoming ~]# rpm -Uvh --replacepkgs yum*.rpm

```

# 以下为部分记录

```sh
#!/bin/bash

## 安装卸载教程地址
##    https://blog.51cto.com/welcomeweb/2132654                        
##    http://www.manongjc.com/article/35785.html
##    https://blog.csdn.net/chengpeng1996/article/details/81216230
##    https://www.cnblogs.com/wangjunjiehome/p/9239005.html
##    https://www.cnblogs.com/lclq/p/5620196.html
##    https://blog.csdn.net/jia_7m/article/details/87940032
##    https://jingyan.baidu.com/article/48b558e3f0d06b7f39c09a66.html
##    
## 由于源中版本会更新，下载时具体请查看版本再下载下来！
## https://www.python.org/ftp/python/3.8.3/
## http://vault.centos.org/7.8.2003/os/
## 
## 在centos7中安装python2和python3
## https://www.pythonf.cn/read/8190
#
# rpm包 下载地址
# http://mirrors.aliyun.com/centos
# http://mirrors.163.com/centos

 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/python-libs-2.7.5-88.el7.x86_64.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/python-iniparse-0.4-9.el7.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/python-pycurl-7.19.0-19.el7.x86_64.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/python-urlgrabber-3.10-10.el7.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/python-setuptools-0.9.8-7.el7.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/rpm-python-4.11.3-43.el7.x86_64.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/python-kitchen-1.1.1-5.el7.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/python-chardet-2.2.1-3.el7.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/python-devel-2.7.5-88.el7.x86_64.rpm

 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/yum-utils-1.1.31-53.el7.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/yum-3.4.3-167.el7.centos.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/yum-metadata-parser-1.1.4-10.el7.x86_64.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/yum-plugin-aliases-1.1.31-53.el7.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/yum-plugin-protectbase-1.1.31-53.el7.noarch.rpm
 wget http://mirrors.aliyun.com/centos/7.8.2003/os/x86_64/Packages/yum-plugin-fastestmirror-1.1.31-53.el7.noarch.rpm

## 
mv python-devel-2.7.5-88.el7.x86_64.rpm      python-devel-2.7.5-88.el7.x86_64

mv python-setuptools-0.9.8-7.el7.noarch.rpm      python-setuptools-0.9.8-7.el7.noarch

mv yum-utils-1.1.31-53.el7.noarch.rpm            yum-utils-1.1.31-53.el7.noarch

mv yum-plugin-aliases-1.1.31-53.el7.noarch.rpm   yum-plugin-aliases-1.1.31-53.el7.noarch

# rpm -ivh  python*.rpm
 rpm -Uvh --replacepkgs python*.rpm

[root@xiaoming ~]# yum install mysql
# There was a problem importing one of the Python modules
# required to run yum. The error leading to this problem was:
#    No module named rpm
# Please install a package which provides this module, or
# verify that the module is installed correctly.
# It's possible that the above module doesn't match the
# current version of Python, which is:
# 2.7.5 (default, Apr  2 2020, 13:16:51) 
# [GCC 4.8.5 20150623 (Red Hat 4.8.5-39)]
# If you cannot solve this problem yourself, please go to 
# the yum faq at:
#   http://yum.baseurl.org/wiki/Faq
#     解释 报这个错误是因为少安装了个 rpm-python- 开头的包 执行以下进行安装[如果已下载 rpm-python- 包]
# rpm -ivh  rpm-python*.rpm
rpm -Uvh --replacepkgs rpm-python*.rpm


# rpm -ivh  yum*.rpm
rpm -Uvh --replacepkgs yum*.rpm




[root@xiaoming ~]# yum install mysql
# Plugin "product-id" can't be imported
# Installed:
#   mariadb.x86_64 1:5.5.65-1.el7                                                                                                                                                             # Dependency Installed:
#   mariadb-libs.x86_64 1:5.5.65-1.el7                                                                                                                                                        
# Complete!

[root@xiaoming ~]# yum list | wc -l
# Repository epel is listed more than once in the configuration
# 23988
[root@xiaoming ~]# 
[root@xiaoming ~]# python --version
# Python 2.7.5
[root@xiaoming ~]# 
[root@xiaoming ~]# rpm -qa | wc -l
# 536
[root@xiaoming ~]# 
[root@xiaoming ~]# rpm -qa | grep mysql
[root@xiaoming ~]# yum install mysql -y



```