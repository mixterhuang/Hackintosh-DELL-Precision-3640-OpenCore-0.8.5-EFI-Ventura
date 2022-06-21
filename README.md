# Hackintosh-DELL-Precision-3640-OpenCore-0.8.1-EFI-Monterey
## 配置：DELL 3640 CPU 10700, UHD 630 GPU, BIOS 1.14.X, Monterey 12.4 <br/>
## 启动按 F2 <b>设置BIOS</b><br/>

| 项目             | 值            |
| ----------------- | ----------------- |
| Intergrated NIC   | Enabled           |
| SATA Operation    | AHCI              |
| Primary Display   | Intel HD Graphics |
| TPM               | Disabled          |
| Secure Boot       | Disabled          |
| Intel SGX         | Disabled          |
| VT for Direct I/O | Disabled          |


## 修改BIOS
很很重要，不然4K HIDPI无法驱动
| 项目 | Offset | Value | Comment       |
| ------------- | ------ | ----- | ------------- |
| SaSetup       | 0xF5   | 0x2   | DVMT: 64M     |
| CpuSetup      | 0x3E   | 0x0   | CFG Lock: OFF |

- 使用将EFI-RU改名字 EFI 放入U盘 EFI分区 ，启动按F12 从U盘启动
- Alt + = 打开列表 （列表是A-Z)排序
- 用方向键下键头 找到 CpuSetup 然后回车 （关闭CFG锁）
- 用方向键找到第3行第E个，注意左上角值为0x3E，回车，选择的位置黄色闪烁输入00，回车，没有黄色显示时按Ctrl+W保存，会提示保存成功
- Alt + = 打开列表
- 用方向键下键头 找到 SaSetup 然后回车 （DVMT）
- 用方向键找到第F行第5个，注意左上角值为0xF5，回车，选择的位置黄色闪烁输入2，回车，没有黄色显示时按Ctrl+W保存，会提示保存成功
- 值此 SaSetup和CpuSetup BIOS已经修改完毕

## 修改注入机型，并OpenCore引导
- 用OpenCore Configurator 打开 EFI/OC/Config.plist 
- 在PlatformInfo - DataHub 中选择机型iMac 20,1, Command+S 保存
- 将EFI放入EFI分区，启动系统 F12或F2在Boot选项中设置用此EFI引导


## 可参考

https://bbs.pcbeta.com/viewthread-1935611-1-1.html

## [RU](http://ruexe.blogspot.com) 为台湾老兄开发，有需要可以去他的网站下载最新版