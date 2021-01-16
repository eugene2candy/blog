---
layout: post
title: "AWS下部署Ubuntu搭建WordPress完整环境与ftp配置详解"
date: 2014-08-22 09:41
author: CHENGJIE XU
comments: true
categories: []
tags: []
---

**转发请注明出处：<a title="https://blog.sonjasper.com/2014/08/22/aws-ubuntu.html" href="https://blog.sonjasper.com/2014/08/22/aws-ubuntu.html" target="_blank"><span style="color: #666666;">https://blog.sonjasper.com/2014/08/22/aws-ubuntu.html</span></a>**

putty 的使用就不解释了。  
Ubuntu 下搭建 wordpress 环境：

**1.安装apache2**

```bash
sudo apt-get install apache2
```

(重启 apache2

```bash
sudo /etc/init.d/apache2 restart
```

**2.安装php**

```bash
sudo apt-get install php5 # 安装 PHP5
sudo apt-get install libapache2-mod-php5 # 配置 APACHE+PHP
sudo /etc/init.d/apache2 restart # 重启 apache
```

**3.安装mysql**

```bash
sudo apt-get install mysql-server
```

**4.让apache、php支持mysql**

```bash
sudo apt-get install libapache2-mod-auth-mysql
sudo apt-get install php5-mysql
sudo /etc/init.d/apache2 restart
```

至此apache2+php5+mysql5环境建好

**5.安装phpmyadmin**

```bash
sudo apt-get install phpmyadmin
```

此时phpmyadmin被安装到/usr/share/phpmyadmin  
需要去/var/www/html做一个phpmyadmin的超链接

```bash
sudo ln -s /usr/share/phpmyadmin
```

**6.建数据库，可以用phpmyadmin**

```bash
sudo start mysql # 启动
pgrep mysqld # 是否开启 
show databases; # 查看 
mysql -u root -p # 进入 
create database name # 创建 
drop database name # 删除 
```

**7.解压wordpress**

```bash
sudo tar -zxvf wordpress-3.8-zh_CN.tar.gz
```

**8.移动**

```bash
sudo cp -a ./wordpress /var/www
```

**修改文件权限，在某个目录下，可以把当前目录与子目录文件全部改成777权限：**

```bash
chmod 777 -R *
```

修改某一个文件的权限：

```bash
chmod 644 name
```

**wordpress 无更新下载权限：**

```bash
ps -aux # 可以查看到apache2的用户是www-data
```

因此 sudo chown -R www-data /var/www/html/你的博客位置

**架设 FTP：**

```bash
sudo apt-get install vsftpd # 安装 
/etc/vsftpd.conf # 中修改
```

```bash
listen=YES
anonymous_enable=NO #一定要是no，然后别人就不能用ftp匿名账户登录了#
lacal_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ascii_upload_enable=YES
ascii_download_enable=YES
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd/chroot_list
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
ras_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
ras_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
pasv_enable=YES
pasv_min_port=1024
pasv_max_port=1048
pasv_addr_resolve=YES
pasv_address="PUBLIC DNS"
userlist_enable=YES
userlist_deny=NO
userlist_file=/etc/vsftpd/user_list
local_root=/var/www
chroot_local_user=YES
anon_root=/var/www **此三行是目录修改**
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
anon_upload_enable=YES
```

同时需要在/etc中建立一个vsftpd文件夹  
文件夹中创建两个文件chroot_list和user_list，  
其中chroot_list不需要填写内容，  
在user_list里写上你在下面步骤中创建的user名字。

**创建ftp用户(此步骤很重要)：**

```bash
sudo useradd -s /sbin/nologin -d /var/www -g ftp user  # user改成你想要的名字
sudo passwd user # 上面你写的名字，回车后输入两次密码
sudo chmod 755 /var/www # 修改www/文件夹权限为755
```

**重启 vsftpd：**

```bash
service vsftpd restart
```

如果你发现做完上述步骤 FTP 登陆不了，去删除/etc/pam.d/vsftpd 这个文件，重启服务

**开启端口：**

```bash
20-21
1024-1048
22
80
443
3306
3389
```

**绑定域名，去/etc/apache2/sites-available 中修改 000-default.conf**

新增：

```bash
<VirtualHost 主机的地址或者 DNS>
ServerName 域名或者子域名
DocumentRoot 具体路径如/var/www/html/
```

完了之后重启 apache： 

```bash  
sudo /etc/init.d/apache2 restart
```
