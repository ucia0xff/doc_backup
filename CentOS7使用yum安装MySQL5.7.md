# CentOS7使用yum安装MySQL5.7

---

## 一、安装

### 1.下载 MySQL 官方的 Yum Repository
  
```bash
# wget -i http://dev.mysql.com/get/mysql57-community-release-el7-10.noarch.rpm
```
 
### 2.安装 Yum Repository

```bash
# yum -y install mysql57-community-release-el7-10.noarch.rpm
```

### 3.用 yum 安装 MySQL

```bash  
# yum -y install mysql-community-server
```

### 4.启动 MySQL

```bash  
# systemctl start  mysqld.service
```

或者使用：

```bash  
# service mysqld start
```

启动后可以查看一下`MySQL`运行状态

```bash  
# systemctl status mysqld.service
```

---

## 二、配置

### 1.连接 MySQL

```bash
# mysql -u root -p
```
如果直接回车不用输入密码就进入了`MySQL`就直接成功了。

否则，在终端输入：

```bash
# grep "password" /var/log/mysqld.log
```
然后在出来的结果中有这么一行：

```text
A temporary password is generated for root@localhost: MVZsf:A<Z2k<
```
这个`MVZsf:A<Z2k<`就是随机生成的密码，包含标点符号。

在终端输入：

```bash
# mysql -u root -p
```
然后再输入密码，即可进入`MySQL`。

### 2.修改密码

刚进入`MySQL`什么都不能做，只能修改密码，而因为密码规则的原因，需要设置非常复杂的密码才能修改成功。

在`MySQL`命令行中输入：

```sql
alter user 'root'@'localhost' identified by 'z?guwrBhH7p>';
```

修改密码后，可以修改密码规则，方便之后修改成一个简单密码。

在`MySQL`命令行中输入：

```sql
set global validate_password_policy=0;
set global validate_password_length=1;
```

此时可以将密码改成任意密码了。在`MySQL`命令行中输入：

```sql
alter user 'root'@'localhost' identified by 'toor';
```
