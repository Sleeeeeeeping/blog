

```sh
# 下载mysql
wget -i -c https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
# 安装
yum -y install mysql80-community-release-el7-3.noarch.rpm
# 安装server
rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
yum -y install mysql-community-server
#启动server
systemctl start  mysqld.service
#检查状态
systemctl status  mysqld.service
#查看临时密码
grep "password" /var/log/mysqld.log

yAbkq)C+/0VJ
#登录MYSQL
mysql -uroot -p
#设置密码
ALTER USER 'root'@'localhost' IDENTIFIED BY 'Left@zuo123.';
#这时候我们将密码设置规范修改一下：
set global validate_password.policy=0;
set global validate_password.length=1;
#修改成简易的密码
ALTER USER 'root'@'localhost' IDENTIFIED BY 'rootroot';
CYN的密码：CYNCYN@cyncyn.!@#
#创建用户：
CREATE USER 'admin'@'%' IDENTIFIED BY '123456';
#允许远程连接：
GRANT ALL ON *.* TO 'admin'@'%';
#如果使用客户端连接提示了plugin caching_sha2_password错误，这是因为MySQL8.0的密码策略默认为caching_sha2_password使用命令修改策略
ALTER USER 'admin'@'%' IDENTIFIED WITH mysql_native_password BY '123456'; 


```

## 