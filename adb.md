# ADB

ADB作为Android开发最常用的工具之一，经常用于设备输出、查看某些文件和参数，此篇wiki主要参考了[官方文档](https://developer.android.google.cn/studio/command-line/adb?hl=zh-cn)，另外一部分来自于个人的工作笔记。



adb用法参考[^1]

adb用法参考[^2]

adb工具用法[^3]

# 剩余任务

- [x] ~~远程连接用法~~
- [x] ~~关闭app的用法~~
- [x] ~~调试APP用法~~

# 安装类

| 用途        | 用法                        |
| ----------- | --------------------------- |
| 强制安装app | adb install -r -t -d xx.apk |
| 普通安装app | adb install xxx.apk         |



# 卸载类

| 用途           | 用法                  |
| -------------- | --------------------- |
| 卸载指定APP    | adb uninstall 包名    |
| 卸载但保存缓存 | adb uninstall -k 包名 |



# 启动类

| 用途               | 用法                                                         |
| ------------------ | ------------------------------------------------------------ |
| 启动Activity       | adb shell am start -n packagename/activity全路径             |
| 启动广播           | adb shell am broadcast -a "actionname" -es key value         |
| 启动系统设置页     | adb shell am start com.android.settings/com.android.settings.Settings |
| 启动指定设备       | adb devices<br>adb -s emulator-5556 shell command<br>        |
| 启动亮屏或灭屏事件 | adb shell input keyevent 26                                  |
| 启动服务           | adb shell am startservice packagename/service全路径          |



# 关闭类

| 用途                    | 用法                                                         |
| ----------------------- | ------------------------------------------------------------ |
| 关闭指定APP             | adb shell am force-stop  包名                                |
| 关闭指定Activity        | adb shell am start -n app包名/app启动activity名称            |
| 先关闭Activity后关闭APP | adb shell am start -n com.test/com.test.MainActivity;<br>adb shell am force-stop com.test |



# 输出类

| 用途             | 用法                                                         |
| ---------------- | ------------------------------------------------------------ |
| 导出指定文件     | adb pull 源路径 目的路径                                     |
| 导出包内文件     | adb pull /data/data/packagename/shared_prefs                 |
| 导出包内文件     | adb pull /data/data/packagename/databases                    |
| 实时记录日志     | adb logcat -v time > d:\logcat202103006.log                  |
| 截图当前屏幕     | adb shell screencap -p /sdcard/存放图片的路径                |
| 录制当前屏幕视频 | adb shell screenrecord -p /sdcard/存放视频的路径             |
| 输出mtklog       | adb root<br>adb shell "echo dbg_debug > /proc/ilitek_ctrl"  /* 将tp log放开 */ <br>adb shell "echo dbg_info > /proc/ilitek_ctrl" /*　将tp log级别恢复默认值　*/<br>adb shell setprop persist.log.tag V<br>adb shell am broadcast -a com.mediatek.mtklogger.ADB_CMD -e cmd_name start --ei cmd_target<br>adb pull sdcard/mtklog 目的路径导出log |

# Log类

其他高级log工具[^3]

其他高级log工具[^4]

| 用途                | 用法                          |
| ------------------- | ----------------------------- |
| 阻止带有此标记的log | adb logcat MainActivity:D *:S |
|                     |                               |
|                     |                               |
|                     |                               |



# 导入类

| 用途                                             | 用法                  |
| ------------------------------------------------ | --------------------- |
| 将文件文件或目录（及其子目录）复制到模拟器或设备 | adb push local remote |



# 查看类

| 用途                                            | 用法                                       |
| ----------------------------------------------- | ------------------------------------------ |
| 查看屏幕当前Activity                            | adb shell "dumpsys window"                 |
| 查看AMS相关的ACtivity                           | adb shell dumpsys activity                 |
| 查看AMS相关的ACtivity-指定APP                   | adb shell dumpsys activity 包名            |
| 查看CPU情况                                     | adb shell dumpsys cpuinfo                  |
| 查看内存情况                                    | adb shell dumpsys meminfo                  |
| 查看WMS服务                                     | adb shell dumpsys window                   |
| 查看系统版本                                    | adb shell getprop ro.build.version.release |
| 查看系统api版本                                 | adb shell getprop ro.build.version.sdk     |
| 查看包含a.ww的包名列表                          | adb shell pm list packages a.ww            |
| 查看设备IP-手机必须连上adb\连上wifi             | `adb shell ifconfig|findstr Bcast`         |
| 查看设备IP-手机必须连上adb\连上wifi             | `adb shell ip -f inet addr`                |
| 查看设备IP-手机必须连上adb\连上wifi\ROM有该驱动 | adb shell netcfg                           |

# 调试类

| 用途           | 用法                                                         |
| -------------- | ------------------------------------------------------------ |
| 链接指定ip设备 | adb connect 192.168.123.122                                  |
| 重启ip端口     | adb tcpip 5555                                               |
| 停止服务       | adb kill-server                                              |
| 启动服务       | 任意adb命令                                                  |
| 调试指定设备   | -s选型后面紧跟设备序列号<br>adb -s emulator-5555 install helloWorld.apk |



[^1]:[awesome-adb: ADB Usage Complete / ADB 用法大全](https://github.com/mzlogin/awesome-adb)
[^2]:[adb-idea](https://github.com/pbreault/adb-idea)
[^3]:[JakeWharton/pidcat: Colored logcat script which only shows log entries for a specific application package](https://github.com/JakeWharton/pidcat)

[^4]:settings->plugins->Browse repositories->ADB WIFI
[^5]:[AndroidWiFiADB](https://github.com/pedrovgs/AndroidWiFiADB)
[^6]:[Android 调试桥 (adb)  | Android 开发者  | Android Developers ](https://developer.android.google.cn/studio/command-line/adb?hl=zh-cn)

