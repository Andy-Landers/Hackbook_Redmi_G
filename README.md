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
| 睡眠 | 未测试 |

## 键位映射

`Windows 徽标键` -> `Command`
`Alt` -> `Option`

## 已知问题

- 无外放、麦克风，耳机有爆音，也许会在不久的将来修复
- 小键盘锁不可用，小键盘只能作为数字键盘使用
- 从 Windows 热重启到 macOS 会导致蓝牙不可用
- **笔记本后面的 HDMI、 mini-DP 在 macOS 下无法外接显示器**，因为它们连接到已被禁用且无法驱动的 NVIDIA 图形卡，唯一可用的显示接口是 USB Type-C

## 鸣谢

- Apple 开发的 macOS
- Acidanthera 维护的 OpenCore 以及众多内核扩展驱动
- Daliansky 的 OC-little 热补丁库