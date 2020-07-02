# 查看系统信息

## 1. 查看Linux发行版

### 命令：
```shell script
cat /etc/issue
```
### 输出：
```text
CentOS release 6.5 (Final)
Kernel \r on an \m
```

## 2. 查看内核版本

### 命令1：
```shell script
uname -a
```
### 输出：
```text
Linux test105 4.4.166-1.el6.elrepo.x86_64 #1 SMP Sat Dec 1 12:37:06 EST 2018 x86_64 x86_64 x86_64 GNU/Linux
```
### 命令2：
```shell script
cat /proc/version
```
### 输出：
```text
Linux version 4.4.166-1.el6.elrepo.x86_64 (mockbuild@Build64R6) (gcc version 4.4.7 20120313 (Red Hat 4.4.7-23) (GCC) ) #1 SMP Sat Dec 1 12:37:06 EST 2018
```
## 3. 查看CPU信息
### 命令：
```shell script
cat /proc/cpuinfo
```
### 结果：
```text
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 44
model name	: Intel(R) Xeon(R) CPU           X5675  @ 3.07GHz
stepping	: 2
microcode	: 0x15
cpu MHz		: 3059.069
cache size	: 12288 KB
……
```