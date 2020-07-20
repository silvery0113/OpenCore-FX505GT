# OpenCore-FX505GT_FX95GT
## 华硕飞行堡垒7 Intel版OpenCore引导分享
### 基本配置：
CPU：Intel i7-9750H (12) @ 2.60GHz
GPU：Intel UHD Graphics 630 
GPU：Nvidia GeForce GTX 1650 (无法驱动，已屏蔽)
主板：FX505GT_FX95GT (HM370芯片组)
声卡：Realtek HDA 235
网卡：Intel Wireless-AC 9462 (实际是9560)
### OpenCore说明
OpenCore版本0.5.9，最高支持到Catalina 10.15.6，11暂不支持，基本完美(实测一个月没发现问题)  
声音调节(Fn+F1/F2/F3)/亮度调节快捷(Fn+F6/F7/F8)全部正常工作，Fn+F10可关闭触控板  
已加载原生电源管理，变频正常  
包含完整音频文件，故体积约115M  
触控板所有手势正常(如遇失灵请往下看)  
##### 使用前请将BIOS以下选项更改/关闭：
1.`Advanced`--`SATA Configuration`--`SATA Mode Selection`—-`AHCI`  
2.`Advanced`--`Graphics Configuration`--`DVMT Pre-Allocated`--`64M`  
3.`Security`--`Secure Boot`--`Secure Boot Control`--`Disable`  
##### 一些驱动说明
`itlwm.kext`：Intel WiFi网卡驱动，因为使用了以太网接口，故定位服务不可用  
`AppleALC.kext`：声卡仿冒驱动，注入ID是30，是我自己定制的，故该驱动请勿升级；官方可注入28(耳机有概率失灵)  
`Intel蓝牙驱动`：已做精简  
`USBPorts.kext`：USB定制驱动，如遇USB工作不正常请自行重新定制  
##### 常见问题说明
1.如果你遇到了触控板失灵/不可用，请首先检查`Fn+F10`是否禁用触控板；确定未禁用请在终端执行`sudo kextcache -i \`重建缓存，并重启电脑；如果仍然无效请长按关机键20s以上，然后开机尝试  
2.WiFi只能上网，隔空和投送不可用  
3.WiFi驱动客户端为Heliport，请安装并添加开机自启动，即可享用WiFi  
4.暂时想不到其它问题了，如果有再补充  
### 感谢名单
·[Apple](https://www.apple.com/) 的macOS  
·[zxystd](https://github.com/OpenIntelWireless) 开发维护的Intel WiFi、蓝牙驱动  
·[Acidanthera](https://github.com/acidanthera) 开发维护的AppleALC、Lilu、WhateverGreen、VirtualSMC等  
·[swkka](https://blog.skk.moe/post/from-clover-to-opencore/) 维护的从 Clover 到 OpenCore——Clover 迁移 OpenCore 指南  
·宪武整理的[OC-little](https://github.com/daliansky/OC-little)  