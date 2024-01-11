# CentOS7

```
# yum update
# yum install mysql-server

# vi /etc/my.cnf
'''
[mysqld]
port=3307
'''

# firewall-cmd --permanent --zone=public --add-port=3307/tcp
'''
success
'''

# firewall-cmd --reload
'''
success
'''

# firewall-cmd --list-all
'''
public (active)
  ports: 3307/tcp
'''

# service mysqld start
# systemctl enable mysqld

# cat /var/log/mysqld.log

'''
2022-04-09T13:18:34.486429Z 6 [Note] [MY-010454] [Server] A temporary password is 
generated for root@localhost: eCWk*MbfH5Wp
'''

# mysql -u root -p
Enter password: <임시비밀번호>

mysql> alter user 'root'@'localhost' identified by '1Q2W3e4r!!';

```

