# MySQL 的一些操作

### 登录

```text
mysql -uroot -p
```

---
### 查看运行状态

```text
service mysqld status

或

service mysql status
```

---
### 查看端口是否在使用

```text
netstat -ntlp | grep 3306
```

---
### 连接字符串

```text
jdbc:mysql://localhost:3306/manager?useSSL=false&useUnicode=true&characterEncoding=utf8&serverTimezone=Asia/Shanghai&useLocalSessionState=true
```
---
### 创建数据库，字符集UTF-8

```sql
create database `dbname` character set utf8 collate utf8_general_ci;
```

---
### 授权

将`全部数据库`的`全部权限`赋给`root`用户（本地）
```sql
grant all privileges on *.* to 'root'@'localhost' identified by 'toor';
```

将`全部数据库`的`全部权限`赋给`root`用户（远程）
```sql
grant all privileges on *.* to 'root'@'%' identified by 'toor';
```

将`dbname`的`全部权限`赋给`tong`用户（远程）
```sql
grant all privileges on dbname.* to 'tong'@'%' identified by 'tong';
```

### 查看权限

查看授权语句
```sql
show grants for 'root'@'%';
```

查看授予的权限
```sql
select * from mysql.user where user='erp_standard';
```