# CentOS7

ref : https://velog.io/@gclee/CentOS-7-MySQL-%EC%84%A4%EC%B9%98

### MySQL 설치
```
# yum update
# yum install mysql-server
```

### MySQL 포트 변경
```
# vi /etc/my.cnf

[mysqld]
port=3306
```

### MySQL 방화벽 추가
```
# firewall-cmd --permanent --zone=public --add-port=3306/tcp
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
  ports: 3306/tcp
'''
```

### MySQL 서비스 시작
```
# service mysqld start
# systemctl enable mysqld
```

### MySQL 초기 비밀번호
```
# cat /var/log/mysqld.log

'''
2022-04-09T13:18:34.486429Z 6 [Note] [MY-010454] [Server] A temporary password is 
generated for root@localhost: eCWk*MbfH5Wp <- 임시비밀번호
'''
```

### 로그인
```
# mysql -u root -p
Enter password: <임시비밀번호>
```

### MySQL 비밀번호 변경
```
mysql> alter user 'root'@'localhost' identified by '[비밀번호]';
```

### MySQL DataBase 생성
```
mysql> CREATE DATABASE [DB이름] default CHARACTER SET UTF8;
Query OK, 1 row affected, 1 warning (0.10 sec)

mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| [name]             |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)
```

### MySQL 유저 생성
```
mysql> create user '[아아디]'@'%' identified by '[비밀번호]';
```
`'[아이디]'@ 뒷 부분에 '%'를 입력하면 외부 / 'localhost'를 입력하면 로컬에서만 사용이 가능하다.`

### MySQL 권한 부여
```
mysql> grant all privileges on [DB이름].* to '[아이디]'@'%';
```


