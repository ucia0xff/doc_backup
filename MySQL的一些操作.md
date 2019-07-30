# MySQL 的一些操作

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