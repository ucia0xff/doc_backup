# adb通过局域网连接设备

---
## Android端

获取root权限，然后安装一个终端模拟器，在终端输入：
```bash
$ su
# setprop service.adb.tcp.port 5555
# stop adbd
# start adbd
```

之后在 `设置`->`WLAN`，点进连的热点，在`网络详情`看到手机的`IP地址`是`x.x.x.x`

---
## PC端

可以将`adb.exe`所在路径加到`Path`中，然后在任意位置打开`cmd`或`PowerShell`，输入：
```text
adb connect x.x.x.x:5555
```

连接成功会显示
```text
connected to x.x.x.x:5555
```