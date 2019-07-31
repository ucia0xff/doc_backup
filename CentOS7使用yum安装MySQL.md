# CentOS7使用yum安装MySQL

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

启动后可以查看一下 MySQL 运行状态

```bash  
# systemctl status mysqld.service
```

---

## 二、配置

待续……
