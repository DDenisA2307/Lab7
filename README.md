```

Домашнее задание 7

Пакеты RPM

Все выполняется на стенде Centos 7

denis@DDA-VirtualBox:~/Lab7_rpm$ vagrant ssh
[vagrant@nginx ~]$ sudo -i
[root@nginx ~]# yum install -y \
> redhat-lsb-core \
> wget \
> rpmdevtools \
> rpm-build \
> createrepo \
> yum-utils \
> gcc
Failed to set locale, defaulting to C
Loaded plugins: fastestmirror
Determining fastest mirrors
 * base: centos.mirror.liteserver.nl
 * extras: centos.mirror.liteserver.nl
 * updates: centos.mirror.triple-it.nl
base                                                     | 3.6 kB     00:00     
extras                                                   | 2.9 kB     00:00     
updates                                                  | 2.9 kB     00:00     
(1/4): base/7/x86_64/group_gz                              | 153 kB   00:01     
(2/4): extras/7/x86_64/primary_db                          | 250 kB   00:01     
(3/4): base/7/x86_64/primary_db                            | 6.1 MB   00:02     
(4/4): updates/7/x86_64/primary_db                         |  24 MB   00:04     
Resolving Dependencies
--> Running transaction check
....
unzip.x86_64 0:6.0-24.el7_9                                                   
  zip.x86_64 0:3.0-11.el7                                                       

Updated:
  yum-utils.noarch 0:1.1.31-54.el7_8                                            

Dependency Updated:
  cups-libs.x86_64 1:1.6.3-52.el7_9        elfutils-libelf.x86_64 0:0.176-5.el7 
  elfutils-libs.x86_64 0:0.176-5.el7       glibc.x86_64 0:2.17-326.el7_9        
  glibc-common.x86_64 0:2.17-326.el7_9     libgcc.x86_64 0:4.8.5-44.el7         
  libgomp.x86_64 0:4.8.5-44.el7            rpm.x86_64 0:4.11.3-48.el7_9         
  rpm-build-libs.x86_64 0:4.11.3-48.el7_9  rpm-libs.x86_64 0:4.11.3-48.el7_9    
  rpm-python.x86_64 0:4.11.3-48.el7_9     

Complete!
[root@nginx ~]# wget https://nginx.org/packages/centos/7/SRPMS/nginx-1.20.2-1.el7.ngx.src.rpm
--2023-12-08 05:48:37--  https://nginx.org/packages/centos/7/SRPMS/nginx-1.20.2-1.el7.ngx.src.rpm
Распознаётся nginx.org (nginx.org)... 3.125.197.172, 52.58.199.22, 2a05:d014:edb:5704::6, ...
Подключение к nginx.org (nginx.org)|3.125.197.172|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа... 200 OK
Длина: 1082461 (1,0M) [application/x-redhat-package-manager]
Сохранение в: «nginx-1.20.2-1.el7.ngx.src.rpm»

100%[======================================>] 1 082 461   1,89MB/s   за 0,5s   

2023-12-08 05:48:38 (1,89 MB/s) - «nginx-1.20.2-1.el7.ngx.src.rpm» сохранён [1082461/1082461]
[root@nginx ~]# rpm -i nginx-1.*
предупреждение: nginx-1.20.2-1.el7.ngx.src.rpm: Заголовок V4 RSA/SHA1 Signature, key ID 7bd9bf62: NOKEY
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
предупреждение: пользователь builder не существует - используется root
предупреждение: группа builder не существует - используется root
[root@nginx ~]# wget https://github.com/openssl/openssl/archive/refs/heads/OpenSSL_1_1_1-stable.zip 
--2023-12-08 05:56:04--  https://github.com/openssl/openssl/archive/refs/heads/OpenSSL_1_1_1-stable.zip
Распознаётся github.com (github.com)... 140.82.121.3
Подключение к github.com (github.com)|140.82.121.3|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа... 302 Found
Адрес: https://codeload.github.com/openssl/openssl/zip/refs/heads/OpenSSL_1_1_1-stable [переход]
--2023-12-08 05:56:05--  https://codeload.github.com/openssl/openssl/zip/refs/heads/OpenSSL_1_1_1-stable
Распознаётся codeload.github.com (codeload.github.com)... 140.82.121.10
Подключение к codeload.github.com (codeload.github.com)|140.82.121.10|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа... 200 OK
Длина: нет данных [application/zip]
Сохранение в: «OpenSSL_1_1_1-stable.zip»

    [         <=>                                     ] 11 924 330  6,66MB/s   за 1,7s   

2023-12-08 05:56:07 (6,66 MB/s) - «OpenSSL_1_1_1-stable.zip» сохранён [11924330]
[root@nginx ~]# unzip OpenSSL_1_1_1-stable.zip
Archive:  OpenSSL_1_1_1-stable.zip
b372b1f76450acdfed1e2301a39810146e28b02c
   creating: openssl-OpenSSL_1_1_1-stable/
  inflating: openssl-OpenSSL_1_1_1-stable/ACKNOWLEDGEMENTS  
...
  inflating: openssl-OpenSSL_1_1_1-stable/util/su-filter.pl  
  inflating: openssl-OpenSSL_1_1_1-stable/util/unlocal_shlib.com.in  
   creating: openssl-OpenSSL_1_1_1-stable/wycheproof/

[root@nginx ~]# yum-builddep rpmbuild/SPECS/nginx.spec
Loaded plugins: fastestmirror
Enabling base-source repository
Enabling extras-source repository
Enabling updates-source repository
Loading mirror speeds from cached hostfile
 * base: centos.mirror.liteserver.nl
 * extras: centos.mirror.liteserver.nl
 * updates: centos.mirror.triple-it.nl
base-source                                                        | 2.9 kB  00:00:00     
extras-source                                                      | 2.9 kB  00:00:00     
updates-source                                                     | 2.9 kB  00:00:00     
(1/3): extras-source/7/primary_db                                  |  32 kB  00:00:01     
(2/3): updates-source/7/primary_db                                 | 346 kB  00:00:01     
(3/3): base-source/7/primary_db                                    | 974 kB  00:00:01     
Checking for new repos for mirrors
...
Installed:
  openssl-devel.x86_64 1:1.0.2k-26.el7_9          pcre-devel.x86_64 0:8.32-17.el7         
  zlib-devel.x86_64 0:1.2.7-21.el7_9             

Dependency Installed:
  keyutils-libs-devel.x86_64 0:1.5.8-3.el7       krb5-devel.x86_64 0:1.15.1-55.el7_9      
  libcom_err-devel.x86_64 0:1.42.9-19.el7        libkadm5.x86_64 0:1.15.1-55.el7_9        
  libselinux-devel.x86_64 0:2.5-15.el7           libsepol-devel.x86_64 0:2.5-10.el7       
  libverto-devel.x86_64 0:0.2.5-4.el7           

Dependency Updated:
  e2fsprogs.x86_64 0:1.42.9-19.el7            e2fsprogs-libs.x86_64 0:1.42.9-19.el7      
  krb5-libs.x86_64 0:1.15.1-55.el7_9          libcom_err.x86_64 0:1.42.9-19.el7          
  libss.x86_64 0:1.42.9-19.el7                openssl.x86_64 1:1.0.2k-26.el7_9           
  openssl-libs.x86_64 1:1.0.2k-26.el7_9       zlib.x86_64 0:1.2.7-21.el7_9               

Complete!

В полученном файле  nginx.spec  вносим изменение в секцию %biuld

--with-openssl=/root/openssl-OpenSSL_1_1_1-stable


[root@nginx ~]# rpmbuild -bb rpmbuild/SPECS/nginx.spec
...
Requires(rpmlib): rpmlib(FileDigests) <= 4.6.0-1 rpmlib(PayloadFilesHavePrefix) <= 4.0-1 rpmlib(CompressedFileNames) <= 3.0.4-1
Проверка на неупакованный(е) файл(ы): /usr/lib/rpm/check-files /root/rpmbuild/BUILDROOT/nginx-1.20.2-1.el7.ngx.x86_64
Записан: /root/rpmbuild/RPMS/x86_64/nginx-1.20.2-1.el7.ngx.x86_64.rpm
Записан: /root/rpmbuild/RPMS/x86_64/nginx-debuginfo-1.20.2-1.el7.ngx.x86_64.rpm
Выполняется(%clean): /bin/sh -e /var/tmp/rpm-tmp.6N6YQ3
+ umask 022
+ cd /root/rpmbuild/BUILD
+ cd nginx-1.20.2
+ /usr/bin/rm -rf /root/rpmbuild/BUILDROOT/nginx-1.20.2-1.el7.ngx.x86_64
+ exit 0
[root@nginx ~]# ll rpmbuild/RPMS/x86_64/
total 4300
-rw-r--r--. 1 root root 2399556 дек  8 06:41 nginx-1.20.2-1.el7.ngx.x86_64.rpm
-rw-r--r--. 1 root root 2000568 дек  8 06:41 nginx-debuginfo-1.20.2-1.el7.ngx.x86_64.rpm
[root@nginx ~]# yum localinstall -y \
> rpmbuild/RPMS/x86_64/nginx-1.20.2-1.el7.ngx.x86_64.rpm
Loaded plugins: fastestmirror
Examining rpmbuild/RPMS/x86_64/nginx-1.20.2-1.el7.ngx.x86_64.rpm: 1:nginx-1.20.2-1.el7.ngx.x86_64
Marking rpmbuild/RPMS/x86_64/nginx-1.20.2-1.el7.ngx.x86_64.rpm to be installed
Resolving Dependencies
--> Running transaction check
---> Package nginx.x86_64 1:1.20.2-1.el7.ngx will be installed
--> Finished Dependency Resolution

Dependencies Resolved

==========================================================================================
 Package    Arch        Version                 Repository                           Size
==========================================================================================
Installing:
 nginx      x86_64      1:1.20.2-1.el7.ngx      /nginx-1.20.2-1.el7.ngx.x86_64      6.0 M

Transaction Summary
==========================================================================================
Install  1 Package

Total size: 6.0 M
Installed size: 6.0 M
Downloading packages:
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : 1:nginx-1.20.2-1.el7.ngx.x86_64                                        1/1 
----------------------------------------------------------------------

Thanks for using nginx!

Please find the official documentation for nginx here:
* https://nginx.org/en/docs/

Please subscribe to nginx-announce mailing list to get
the most important news about nginx:
* https://nginx.org/en/support.html

Commercial subscriptions for nginx are available on:
* https://nginx.com/products/

----------------------------------------------------------------------
  Verifying  : 1:nginx-1.20.2-1.el7.ngx.x86_64                                        1/1 

Installed:
  nginx.x86_64 1:1.20.2-1.el7.ngx                                                         

Complete!
[root@nginx ~]# systemctl start nginx
[root@nginx ~]# systemctl status nginx
● nginx.service - nginx - high performance web server
   Loaded: loaded (/usr/lib/systemd/system/nginx.service; disabled; vendor preset: disabled)
   Active: active (running) since Пт 2023-12-08 06:48:41 UTC; 16s ago
     Docs: http://nginx.org/en/docs/
  Process: 17813 ExecStart=/usr/sbin/nginx -c /etc/nginx/nginx.conf (code=exited, status=0/SUCCESS)
 Main PID: 17814 (nginx)
   CGroup: /system.slice/nginx.service
           ├─17814 nginx: master process /usr/sbin/nginx -c /etc/nginx/nginx.conf
           └─17815 nginx: worker process

дек 08 06:48:41 nginx systemd[1]: Starting nginx - high performance web server...
дек 08 06:48:41 nginx systemd[1]: Can't open PID file /var/run/nginx.pid (yet?) a...ory
дек 08 06:48:41 nginx systemd[1]: Started nginx - high performance web server.
Hint: Some lines were ellipsized, use -l to show in full.
[root@nginx ~]# mkdir /usr/share/nginx/html/repo
[root@nginx ~]# cp rpmbuild/RPMS/x86_64/nginx-1.20.2-1.el7.ngx.x86_64.rpm /usr/share/nginx/html/repo/
[root@nginx ~]# wget https://downloads.percona.com/downloads/percona-distribution-mysql-ps/percona-distribution-mysql-ps-8.0.28/binary/redhat/8/x86_64/percona-orchestrator-3.2.6-2.el8.x86_64.rpm -O /usr/share/nginx/html/repo/percona-orchestrator-3.2.6-2.el8.x86_64.rpm
--2023-12-08 07:08:41--  https://downloads.percona.com/downloads/percona-distribution-mysql-ps/percona-distribution-mysql-ps-8.0.28/binary/redhat/8/x86_64/percona-orchestrator-3.2.6-2.el8.x86_64.rpm
Распознаётся downloads.percona.com (downloads.percona.com)... 49.12.125.205, 2a01:4f8:242:5792::2
Подключение к downloads.percona.com (downloads.percona.com)|49.12.125.205|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа... 200 OK
Длина: 5222976 (5,0M) [application/x-redhat-package-manager]
Сохранение в: «/usr/share/nginx/html/repo/percona-orchestrator-3.2.6-2.el8.x86_64.rpm»

100%[================================================>] 5 222 976   5,31MB/s   за 0,9s   

2023-12-08 07:08:42 (5,31 MB/s) - «/usr/share/nginx/html/repo/percona-orchestrator-3.2.6-2.el8.x86_64.rpm» сохранён [5222976/5222976]
[root@nginx ~]# createrepo /usr/share/nginx/html/repo/
Spawning worker 0 with 2 pkgs
Workers Finished
Saving Primary metadata
Saving file lists metadata
Saving other metadata
Generating sqlite DBs
Sqlite DBs complete

Изменяем  conf 

[root@nginx ~]# vi /etc/nginx/conf.d/default.conf

...
  location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
        autoindex on;
    }
....

[root@nginx ~]# nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
[root@nginx ~]# curl -a http://localhost/repo/
<html>
<head><title>Index of /repo/</title></head>
<body>
<h1>Index of /repo/</h1><hr><pre><a href="../">../</a>
<a href="repodata/">repodata/</a>                                          08-Dec-2023 07:09                   -
<a href="nginx-1.20.2-1.el7.ngx.x86_64.rpm">nginx-1.20.2-1.el7.ngx.x86_64.rpm</a>                  08-Dec-2023 06:53             2399556
<a href="percona-orchestrator-3.2.6-2.el8.x86_64.rpm">percona-orchestrator-3.2.6-2.el8.x86_64.rpm</a>        16-Feb-2022 15:57             5222976
</pre><hr></body>
</html>
[root@nginx ~]# cat >> /etc/yum.repos.d/otus.repo << EOF
> [otus]
> name=otus-linux
> baseurl=http://localhost/repo
> gpgcheck=0
> enabled=1
> EOF
[root@nginx ~]# ls -l /etc/yum.repos.d
total 40
-rw-r--r--. 1 root root 1664 апр  7  2020 CentOS-Base.repo
-rw-r--r--. 1 root root 1309 апр  7  2020 CentOS-CR.repo
-rw-r--r--. 1 root root  649 апр  7  2020 CentOS-Debuginfo.repo
-rw-r--r--. 1 root root  314 апр  7  2020 CentOS-fasttrack.repo
-rw-r--r--. 1 root root  630 апр  7  2020 CentOS-Media.repo
-rw-r--r--. 1 root root 1331 апр  7  2020 CentOS-Sources.repo
-rw-r--r--. 1 root root 7577 апр  7  2020 CentOS-Vault.repo
-rw-r--r--. 1 root root  616 апр  7  2020 CentOS-x86_64-kernel.repo
-rw-r--r--. 1 root root   74 дек  8 07:17 otus.repo
[root@nginx ~]# yum repolist enabled | grep otus
otus                                otus-linux                                 2
[root@nginx ~]# yum list | grep otus
percona-orchestrator.x86_64                 2:3.2.6-2.el8              otus     

