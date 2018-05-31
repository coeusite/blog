+++
title = "LineageOS安装记录"
date = "2018-05-31T14:03:52+08:00"
Description = ""
draft = false
Tags = ["RedMi Note 4X", "LineageOS"]
Categories = []
+++

最近买了个红米Note4X作为备机。
鉴于小米早就因[偷偷传输用户数据到国内服务器而名传天下](https://www.solidot.org/story?sid=40674)，
我打算刷成LineageOS以减少隐私泄漏风险。

本次装机依照官网教程：https://wiki.lineageos.org/devices/mido/install

# 刷机流程
- 下载必备文件（platform-tools/miflash_unlock/TWRP/LinageOS)
- 开启工程模式
- 开启 USB debugging
- 解锁 bootloader 
- 从 fastboot 启动 TWRP
- 刷入 LinageOS
- 刷入 Google Apps (optional)
- 刷入 su (optional)

# 详细操作说明
## 下载必备文件（platform-tools/miflash_unlock/TWRP/LinageOS)
- platform-tools: https://developer.android.com/studio/releases/platform-tools
- miflash_unlock: https://miui.com/unlock/
- TWRP: https://dl.twrp.me/mido
- LinageOS: https://download.lineageos.org/mido
- Google Apps (arm64-8.1-nano): https://opengapps.org/?api=8.1&variant=nano
- LinageOS Extra: https://download.lineageos.org/extras
记得自己做 hash/asc 校验

## 开启开发者模式
google it by yourself

基本就是狂点某个版本号

## 开启 USB debugging
- 解压 platform-tools，打开 powershell 并进入文件夹
- 在 windows 上开启 adb 监听，e.g. ```./adb devices```
- 进入设置-更多设置-开发者选项
- 开启 USB debugging
- 永久允许该 PC 调试

## 解锁 bootloader 
- 在手机上登录小米帐号，等待72小时
- 到网站申请解锁 https://miui.com/unlock/
- 下载解压解锁程序
- 重启手机至 fastboot，e.g. ```./adb reboot fastboot```
- 运行解锁程序

## 从 fastboot 启动/刷入 TWRP
不刷 recovery 的话，也可以直接启动 TWRP ```fastboot boot twrp-3.2.1-0-mido.img```

也可以刷入 ```fastboot flash recovery twrp-3.2.1-0-mido.img``` 然后重启

## 刷入 LinageOS
- 拷贝zip&md5文件到 sdcard
- 进入 TWRP: ```./adb reboot recovery```
- 清除 “Cache, System and Data”
- 刷入 lineage-15.1-20180528-nightly-mido-signed.zip

## 刷入 Google Apps (optional)
同 LinageOS img

## 刷入 su (optional)
同 LinageOS img

