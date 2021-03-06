# Hackbook_Redmi_G

红米 G 游戏本通用 EFI

支持除 `i5-10200H` 以外的所有 CPU 版本的红米 G 游戏本

- 引导器基于 `OpenCore 0.6.6`
- 最后测试版本 `MacOS 11.2.1 Big Sur `

请于 Release 页面下载打包好的 EFI 文件夹

## BIOS 设置

`安全启动` -> `关闭`

## 目前进展

| 项目 | 状态 |
| ---- | ---- |
| 显卡加速 | 支持 |
| 以太网 | 支持 |
| Wi-Fi（原厂自带 Intel AX201） | 支持 |
| 蓝牙（原厂自带 Intel AX201） | 支持 |
| HDMI (Type-C) 输出 | 未测试 |
| 音频 | 暂时只有耳机输出 |
| 触控板 | 支持 |
| 电量显示 | 支持 |
| 亮度调节 | 支持 |
| FN 键盘灯开关 | 支持 |
| 睡眠 | 未测试 |

## 键位映射

`Windows 徽标键` -> `Command`

`Alt` -> `Option`

`右 Ctrl` -> `Command`

`CapsLock` -> `中/英切换`

## 已知问题

- 无外放、麦克风，耳机有爆音，也许会在不久的将来修复
- 小键盘锁不可用，小键盘只能作为数字键盘使用
- 从 Windows 热重启到 macOS 会导致蓝牙不可用
- **笔记本后面的 HDMI、 mini-DP 在 macOS 下无法外接显示器**，因为它们连接到已被禁用且无法驱动的 NVIDIA 图形卡，唯一可用的显示接口是位于电脑右侧的 USB Type-C
- **i5-10200H 的核显在驱动后会出现严重的花屏和闪屏**，无法正常使用

## 关于 i5-10200H

核显的 device-id 是 0x9BA4

目前可以确定 i5-10200H 的核显是 UHD610，属于 GT1.5F 级别。经过测试，当通过仿冒为 0x3E9B 来驱动此核显后，显示会出现花屏、图形闪烁等现象，无法正常使用。但是 Metal 加速正常（通过 Xcode 运行 Sample 测试），Type-C HDMI 也可以输出（但还是花屏）

然而，IceLake GT1 级别的核显可以被正常驱动，并不会出现显示问题，经过查看 01.org 的文档，IceLake 所有的核显都是具有 8 个 Slice，而 CometLake/CoffeeLake 只有 GT2 以上的核显才具有 8 个 Slice，GT1 只有 6 个 Slice。目前的得到的信息只有这些，个人能力有限，应该不会再研究下去了

预计所有搭载 10200H 的笔记本都受影响

## 关于麦克风和外放

一些笔记本（如：联想小新Pro13）采用了新的音频技术，声音设备直连 PCH 而不是通过传统的 HDAudio 来实现

目前 AppleALC 和 VoodooHDA（是的，万能声卡也不行）尚不支持此使用技术的声音设备，经过对已有的 id 进行测试，**只有耳机输出可以使用**

## Credit

- Apple 开发的 macOS
- Acidanthera 维护的 OpenCorePkg 以及众多内核扩展驱动
- OC-little 热补丁库
- DalianSky 更新的 USBInjectAll 与提供镜像下载
- OpenIntelWireless 维护的 itlwm 和 IntelBluetooth
