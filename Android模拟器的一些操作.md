# Android模拟器的一些操作

---
## 命令行启动模拟器

需要将`android-sdk`下的`emulator`文件夹所在路径加入`Path`中

### 显示已创建的模拟器

```text
emulator -list-avds
```
### 启动模拟器

```text
emulator -avd Nexus_5X_API_29_x86
```

这里的`Nexus_5X_API_29_x86`是之前显示的模拟器名称。
模拟器启动后，不能关闭命令行窗口，否则模拟器也会关闭。

---
## 关闭和启动adb服务

需要将`android-sdk`下的`platform-tools`文件夹所在路径加入`Path`中

### 关闭adb服务

```text
adb kill-server
```
### 启动adb服务

```text
adb start-server
```

---
## 安装卸载apk

### 安装apk
```text
adb install filename.apk
```

### 卸载apk
```text
adb uninstall packagename
```
卸载时只要包名，不需要加`.apk`后缀

### 重装apk
```text
adb install -r filename.apk
```
---
## 多个设备的操作
如果adb连接了多个设备，比如模拟器和真机，进行操作时就要指定操作哪个设备。


### 显示已连接的设备

```text
adb devices
```

### 安装apk到指定设备

用`-s 设备名称`指定要安装的设备：
```text
adb -s emulator-5554 install filename.apk
```
### 卸载指定设备上的apk

```text
adb -s emulator-5554 uninstall packagename
```

### 重装apk到指定设备

```text
adb -s emulator-5554 install -r filename.apk
```

---
## 文件传输

### push：从PC传输到Android设备

将`PC`上的文件传输到`Android设备`
```text
adb push .\filename.apk /sdcard/Download
```

将`PC`上的文件传输到`Android设备`，并重命名
```text
adb push .\filename.apk /sdcard/Download/1.apk
```

### pull：从Android设备传输到PC

把`Android设备`上的文件传输到`PC`
```text
adb pull /sdcard/Download/filename.apk .
```

把`Android设备`上的文件传输到`PC`，并重命名
```text
adb pull /sdcard/Download/filename.apk .\1.apk 
```

### 指定设备传输

如果adb连接了多个设备，用`-s 设备名称`指定传输哪个设备。
```text
adb -s emulator-5554 push .\filename.apk /sdcard/Download/1.apk
adb -s emulator-5554 pull /sdcard/Download/filename.apk .\1.apk 
```