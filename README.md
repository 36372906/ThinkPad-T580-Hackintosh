# 联想ThinkPad T580上的macOS（本指南也适用于T480 i7-8550u，8250u和8650u理论上应该通用，不适用T480s）

--------------------------------------------------------------------------
此存储库包含10.14在Lenovo ThinkPad T580上运行macOS（目前为Mojave ）的示例配置
--------------------------------------------------------------------------

机器配置表
---------
* 联想ThinkPad T580 【4k的UHD显示屏：3840x2160（京东方BOE NV156QUM-N44，非触摸）】

* 英特尔i7-8550U CPU

* 内存16GB RAM DDR4 2400-SODIMM

* 东芝Q200EX SSD+128G 东芝nvme联想跟机带

* 英特尔以太网I219-V4 有线网卡

* Mac原装无线网卡bcm94360cs2（原装英特尔AC8265无法正常工作）

* Wi-Fi设备芯片组为(0x14E4, 0x117) 显示Airport Extreme 使用AirportBrcmFixup.kext

* 蓝牙设备芯片组20702B0,固件版本:v150 c9318 免驱动

* 瑞昱Realtek ALC3287（“ALC257”）通过AppleALC.kext与layout-id：11，支持耳机和自带喇叭之间插拔自动切换。

* Intel UHD Graphics 620（禁用Nvidia MX150，macOS不支持Optimus）

* ACPI热修补电源管理和双电池状态

* SD卡读卡器走usb3.0通道，需要打开此USB端口即可使用

* Thunderbolt 3【BIOS里需要设置“Thunderbolt BIOS Assist”：Disable，即可使前端类型USB type-c端口在macOS中工作，可以热插拔， DP / HDMI通过USB type-C：视频工作正常，连接扩展坞正常】

* 机器自带独立的HDMI端口：可以输出4k@30HZ到显示器。连接时会显示音频设备HDMI，并正常使用。

* 键盘Synaptics触摸板（PS / 2）使用ApplePS2SmartTouchPad.kext，EMlyDinEsH的v4.7b5，支持多点触控手势。
* 睡眠和唤醒正常

已禁用的设备和BIOS设置
-----------
* WWAN（无模块）
* TrackPad Synaptics指纹识别器无法驱动
* BIOS里设置Thunderbolt BIOS Assist为Disable，否则USB type-c无法正常工作。
* 设置BIOS里usb电源管理enable（这样雷电口type-c就可以热插拔type-c外设）
* 关闭安全启动

UEFI固件修订
-----------
* BIOS版本 1.20


目前存在的问题
-------------
* 无

备注
--------
* （重要）您需要config.plist使用唯一的序列号生成一个正确的：
* 运行./tools/gen.sh（macOS）或tools\gen.bat（Windows）生成config.plist。
* 添加-f或--force标记以config.plist使用新序列号强制重新生成。
* 所有SSDT热补丁都位于EFI/CLOVER/ACPI/dsl。您可以.aml通过运行update.sh（macOS）或update.bat（Windows）来更新已编译的二进制文件。
* 经过SSDT-KBD.aml调整ApplePS2SmartTouchPad.kext。如果你想切换到VoodooPS2Controller.kext，使用SSDT-KBD.aml的backup文件夹来代替。
