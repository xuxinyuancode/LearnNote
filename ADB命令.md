# adb命令

### 查看当前连接设备：

- 查看当前连接设备

```shell
adb devices
```

- 如果发现多个设备

```shell
adb -s 设备号 其他指令
```

### 查看日志：

```shell
adb logcat
```

### 安装apk文件

- 普通安装

```shell
adb install xx.apk
```

- 覆盖安装

```shell
adb install -r xxx.apk
```

### 卸载App

- 普通卸载

```shell
adb uninstall com.android.myapplication
```

- 保留数据

```shell
adb uninstall -k com.android.myapplication
```

### 传递文件

- 往手机SDcard传递文件

```shell
adb push 文件名 /sdcard/
```

- 从手机下载文件

```shell
adb pull /sdcard/xxx.txt
```

### 查看手机端安装的所有app包名

```shell
adb shell pm list packages
```

### 启动Activity

```shell
adb shell am start 包名/完整activity路径
```

### 使用root权限

```shell
adb root
adb remount
```

### 截取屏幕

```shell
adb shell screencap /sdcard/screen.png
adb pull /sdcard/screen.png
```

