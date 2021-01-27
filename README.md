# OpenCore Hackintosh for Dell G3 3579(DW1820A)
macOS版本: 11.0.1
OpenCore版本: 0.6.3
This OpenCore hackintosh repo is made for i5-8300H, GTX1050Ti, no USB Type-C version of Dell G3 3579.

## 特别感谢
> 本项目基于[tonyleelyy](https://github.com/tonyleelyy/OpenCore-Hackintosh-Dell-G3-3579)修改而来，主要目的在于适配DW1820A网卡

## 说明
本项目不会持续更新，暂时处于养老阶段。大三考研党，没时间随着[tonyleelyy](https://github.com/tonyleelyy/OpenCore-Hackintosh-Dell-G3-3579)的版本更新而更新EFI,还请担待！

## 电脑配置

|   配件   |             规格              | 工作状态 |
| :------: | :---------------------------: | :------: |
|   模组   |         Dell G3 3579          |    ✅     |
|  处理器  | Intel Core i5-8300H @ 2.30Ghz |    ✅     |
|   内存   |    8GB Micron DDR4 2666Mhz/8GB Kingston DDR4 2666Mhz    |    ✅     |
| 固态硬盘 |   Hikvision C2000Pro 512GB    |    ✅     |
| 机械硬盘 |         希捷 1TB          |    ✅     |
| 核芯显卡 |    Intel UHD Graphics 630    |    ✅     |
| 独立显卡 |  NVIDIA GeForce GTX 1050 4G   |    🚫     |
|   声卡   |        Realtek ALC236         |    ✅     |
| 有线网卡 |        Realtek RTL8111        |    ✅    |
| 无线网卡 |     DW1820A CN-08PKF4     |  ✅  |

## BIOS设置

| **System Configuration** |      |
| --- | --- |
| SATA Operation       | AHCI |
|                      |      |
| **Intel Software Guard Extensions** |                    |
| Intel SGX Enable | Disabled           |
|  |                    |
| **POST Behavior** |                    |
| Fastboot | Thorough           |
|  |                    |

请更新 BIOS 至最新版本！
其他保持默认设置。

## 工作的部分

- macOS 11.0.1
- CPU（睿频4.0Ghz）
- 核芯显卡
- 有线网卡
- 音频（Layout=15）
- USB（定制USBPorts.kext）
- 触摸板
- 摄像头
- 蓝牙（带有蓝牙开关）
- Wi-Fi

## 不工作的部分

- 独立显卡（已使用SSDT屏蔽）
- HDMI（直接连接到独立显卡）
- 内置读卡器

## 重要提醒
1.本项目删除了所有关于intel网卡的kext，并附带添加了支持dw1820a的驱动文件。  
2.删除了所有关于intel网卡的kernel项，添加了brcm网卡对应wifi与蓝牙的启动项。  
3.**特别注意的是：** 对于kext的启动项顺序，必须如下排序：AirportBrcmFixup.kext-》BrcmBluetoothInjector.kext-》BrcmFirmwareData.kext-》BrcmPatchRAM3.kext，否则，将报错。  
4.**特别注意的是：** 对于网卡本身的针脚而言，我没有屏蔽针脚。屏蔽针脚以后，反而无法正常使用（可能是我的机型原因，可能是dw1820a本身的版本原因）。  
5.**特别注意的是：** 对于修改config.list而言，参考最新的[黑果小兵](https://blog.daliansky.net/DW1820A_BCM94350ZAE-driver-inserts-the-correct-posture.html)文章,不再需要注册pci地址号，详细请查看小兵的文章。但凡划去的都是过时的配置。  
6.**特别注意的是：** 在bios里面的wireless选项中，我们可以控制wifi/蓝牙的开启与关闭，**如果有任何人想要自行修改配置文件，**建议大家在调整配置的时候如下顺序尝试：1）不屏蔽针脚插上网卡 2）进入bios关闭wifi和蓝牙 3）oc引导进入系统（此时无wifi蓝牙） 4）备份当前efi，参考黑果小兵所述、我的配置文件等参考性资料，修改efi以及配置文件 5）保存修改，重启进入bios，只开启wifi不开启蓝牙 6）尝试能否进入系统，尝试wifi能否正常连接 7）若能，则再次重启进入bios，开启蓝牙选项；若不能，检查前面的配置文件是否有误，无误则尝试屏蔽针脚，重复上述某些操作 8）bios开启蓝牙后看是否正常进入系统，若能，查看蓝牙功能是否正常；若不能，检查配置是否正确。祝各位成功～  
7.**个人建议的是：**检查是否需要屏蔽针脚的办法是屏蔽前与屏蔽后windows上是否能够检测出正确的无线网卡设备并正常驱动。（设备管理器）  


