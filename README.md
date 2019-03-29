# 联想ThinkPad T580上的macOS

--------------------------------------------------------------------------
此存储库包含10.14在Lenovo ThinkPad T580上运行macOS（目前为Mojave ）的示例配置
--------------------------------------------------------------------------

  `使用的硬件配置`
  -------------------------------------  
  *  联想ThinkPad T580
    
  *  英特尔i7-8550U
    
  *  内存16GB RAM DDR4 2400-SODIMM
    
  *  东芝Q200EX SSD+128G 东芝nvme
    
  *  戴尔DW1830无线（原装英特尔AC8265无法正常工作）
  *  Wi-Fi设备显示为Apple Airport ExtremeAirportBrcmFixup.kext
  *  蓝牙设备芯片组20702A0使用BrcmPatchRAM2.kext
  *  瑞昱ALC257通过AppleALC.kext与layout-id11
  *  Intel UHD Graphics 620（禁用Nvidia MX150，macOS不支持Optimus）
  *  ACPI热修补电源管理和双电池状态
  *  键盘/ Elan触摸板（PS / 2）使用ApplePS2SmartTouchPad.kextEMlyDinEsH的v4.7b5，支持多点触控手势,需要在BIOS中禁用Trackpoint（否则触摸板将被断开）,需要修补ApplePS2SmartTouchPad已在此repo中修补的二进制文件（否则驱动程序报告不支持的模型）。
  *  Offset    Original  Patched 
    
    0000ABF5  72        EB
    0000AC2D  01        04

已禁用的设备
----------------------
  *  WWAN（无模块）
  *  Trackpoint（使用时可以启用VoodooPS2Controller.kext）
SD卡读卡器走usb3.0通道，开箱即用
  *  指纹扫描仪无法驱动
  *  Thunderbolt 3（USB type-c工作）
  *  固件修订
  *  BIOS版本 1.20
  
  `备注`
   ---
  *  （重要）您需要config.plist使用唯一的序列号生成一个正确的：
  *  运行./tools/gen.sh（macOS）或tools\gen.bat（Windows）生成config.plist。
  *  添加-f或--force标记以config.plist使用新序列号强制重新生成。
  *  所有SSDT热补丁都位于EFI/CLOVER/ACPI/dsl。您可以.aml通过运行update.sh（macOS）或update.bat（Windows）来更新已编译的二进制文件。
  *  经过SSDT-KBD.aml调整ApplePS2SmartTouchPad.kext。如果你想切换到VoodooPS2Controller.kext，使用SSDT-KBD.aml的backup文件夹来代替。
