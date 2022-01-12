
### 5.1. Ubuntu Podを起動
`kubectl run -it  ubuntu --image ubuntu -n tidb-cluster -- bash`{{execute}}

例:

```
controlplane $ kubectl run -it  ubuntu --image ubuntu -n tidb-cluster -- bash
If you don't see a command prompt, try pressing enter.
root@ubuntu:/#
```

### 5.2. Ubuntu Podでapt updateを実施
`apt update`{{execute}}

例:

```
root@ubuntu:/# apt update
Get:1 http://archive.ubuntu.com/ubuntu focal InRelease [265 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]             
Get:3 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages [11.3 MB]
Get:6 http://archive.ubuntu.com/ubuntu focal/multiverse amd64 Packages [177 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages [1275 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal/restricted amd64 Packages [33.4 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [899 kB]
Get:10 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1844 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 Packages [33.7 kB]
Get:12 http://archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [1118 kB]
Get:13 http://archive.ubuntu.com/ubuntu focal-backports/main amd64 Packages [50.8 kB]
Get:14 http://archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [22.4 kB]
Get:15 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [837 kB]
Get:16 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [1417 kB]
Get:17 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 Packages [30.1 kB]
Get:18 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [833 kB]
Fetched 20.5 MB in 2s (9309 kB/s)                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

### 5.3. Ubuntu PodでMySQL Clientをインストール
`apt install mysql-client -y`{{execute}}

例:

```
root@ubuntu:/# apt install mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libbsd0 libedit2 libssl1.1 mysql-client-8.0 mysql-client-core-8.0 mysql-common
The following NEW packages will be installed:
  libbsd0 libedit2 libssl1.1 mysql-client mysql-client-8.0 mysql-client-core-8.0 mysql-common
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 5916 kB of archives.
After this operation, 71.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu focal/main amd64 libbsd0 amd64 0.10.0-1 [45.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 libssl1.1 amd64 1.1.1f-1ubuntu2.10 [1322 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal/main amd64 libedit2 amd64 3.1-20191231-1 [87.0 kB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 mysql-client-core-8.0 amd64 8.0.27-0ubuntu0.20.04.1 [4423 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal/main amd64 mysql-common all 5.8+1.0.5ubuntu2 [7496 B]
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 mysql-client-8.0 amd64 8.0.27-0ubuntu0.20.04.1 [22.0 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 mysql-client all 8.0.27-0ubuntu0.20.04.1 [9424 B]
Fetched 5916 kB in 0s (18.1 MB/s)            
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package libbsd0:amd64.
(Reading database ... 4127 files and directories currently installed.)
Preparing to unpack .../0-libbsd0_0.10.0-1_amd64.deb ...
Unpacking libbsd0:amd64 (0.10.0-1) ...
Selecting previously unselected package libssl1.1:amd64.
Preparing to unpack .../1-libssl1.1_1.1.1f-1ubuntu2.10_amd64.deb ...
Unpacking libssl1.1:amd64 (1.1.1f-1ubuntu2.10) ...
Selecting previously unselected package libedit2:amd64.
Preparing to unpack .../2-libedit2_3.1-20191231-1_amd64.deb ...
Unpacking libedit2:amd64 (3.1-20191231-1) ...
Selecting previously unselected package mysql-client-core-8.0.
Preparing to unpack .../3-mysql-client-core-8.0_8.0.27-0ubuntu0.20.04.1_amd64.deb ...
Unpacking mysql-client-core-8.0 (8.0.27-0ubuntu0.20.04.1) ...
Selecting previously unselected package mysql-common.
Preparing to unpack .../4-mysql-common_5.8+1.0.5ubuntu2_all.deb ...
Unpacking mysql-common (5.8+1.0.5ubuntu2) ...
Selecting previously unselected package mysql-client-8.0.
Preparing to unpack .../5-mysql-client-8.0_8.0.27-0ubuntu0.20.04.1_amd64.deb ...
Unpacking mysql-client-8.0 (8.0.27-0ubuntu0.20.04.1) ...
Selecting previously unselected package mysql-client.
Preparing to unpack .../6-mysql-client_8.0.27-0ubuntu0.20.04.1_all.deb ...
Unpacking mysql-client (8.0.27-0ubuntu0.20.04.1) ...
Setting up mysql-common (5.8+1.0.5ubuntu2) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Setting up libssl1.1:amd64 (1.1.1f-1ubuntu2.10) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (Can't locate Term/ReadLine.pm in @INC (you may need to install the Term::ReadLine module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.30.0 /usr/local/share/perl/5.30.0 /usr/lib/x86_64-linux-gnu/perl5/5.30 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.30 /usr/share/perl/5.30 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
debconf: falling back to frontend: Teletype
Setting up libbsd0:amd64 (0.10.0-1) ...
Setting up libedit2:amd64 (3.1-20191231-1) ...
Setting up mysql-client-core-8.0 (8.0.27-0ubuntu0.20.04.1) ...
Setting up mysql-client-8.0 (8.0.27-0ubuntu0.20.04.1) ...
Setting up mysql-client (8.0.27-0ubuntu0.20.04.1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
```

### 5.4. TiDBへアクセス
`mysql -h basic-tidb -uroot -P 4000`{{execute}}

例:

```
root@ubuntu:/# mysql -h basic-tidb -uroot -p -P 4000
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 123
Server version: 5.7.25-TiDB-v5.3.0 TiDB Server (Apache License 2.0) Community Edition, MySQL 5.7 compatible

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| INFORMATION_SCHEMA |
| METRICS_SCHEMA     |
| PERFORMANCE_SCHEMA |
| mysql              |
| test               |
+--------------------+
5 rows in set (0.01 sec)

mysql> exit
Bye
root@ubuntu:/#
```