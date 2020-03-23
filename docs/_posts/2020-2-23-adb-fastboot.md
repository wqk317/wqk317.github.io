---
title: "adb & fastboot"

categories:
  - Command
tags:
    - adb
    - fastboot
	- Android
last_modified_at: 2020-03-23T14:28:50
---

# adb
1. [Google官方下载地址](https://developer.android.com/studio/releases/platform-tools)

2. 批量pull某一类文件

	`adb shell ls data/media/0/app*.txt | tr "\n\r" " " | xargs -n1 adb pull`
	
3. 保留数据卸载app

	```
	保留数据卸载app: adb uninstall -k <package>
	
	高版本adb(在1.0.40测试pass)请替换为: adb shell cmd package uninstall -k
	
	如果上述命令提示cmd: Can't find service: xxx
	
	请尝试adb shell pm uninstall -k
	```
	
4. WSL下使用win adb

	`sudo ln -s /mnt/d/Android/sdk/platform-tools/adb.exe /usr/bin/adb && sudo ln -s /mnt/d/Android/sdk/platform-tools/fastboot.exe /usr/bin/fastboot`
	/usr/bin/adb和fastboot需要提前删除
	
5. Android原生跳过开机引导

	```
	adb shell settings put secure user_setup_complete 1
	adb shell settings put global device_provisioned 1
	adb reboot

	无返回值即为成功
	```
	
6. adb截图
	
	```
	adb shell /system/bin/screencap -p /sdcard/screenshot.png
	adb pull /sdcard/screenshot.png
	```
	
7. 网络连接adb(网络调试)

	```
	adb tcpip 5555
	adb connect 10.237.201.104:5555    //手机端IP
	```
	
8. 取出手机里的apk

	```
    ① pm列出所有包: adb shell pm list packages
    ② 找到apk位置: adb shell pm path com
    ③ adb pull 导出 
	```