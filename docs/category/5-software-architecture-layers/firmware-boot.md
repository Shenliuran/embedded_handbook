# 启动阶段的固件

## B

### BIOS

+ Basic Input Output System（基本输入输出系统）
+ 固化在主板只读存储器（ROM/Flash）中的基础固件程序，是 x86 架构计算机上电后第一个运行的程序，承担硬件初始化、系统引导的核心职能

---

## P

### Partition table

+ 分区表
+ 也称为"disktable"

#### APM

+ Apple Partition Map

#### BSD disktable

+ FreeBSD、OpenBSD 等 UNIX 系统使用
+ 嵌套在 MBR 内，一个 MBR 分区里可以再分很多 BSD 分区
+ 嵌入式 NAS、路由偶尔会见到

#### DOS 3.3 分区表（非常早期）
+ 比 MBR 还古老
+ 现在只存在于模拟器 / 古董机

#### GPT
+ GUID Partition Table
+ UEFI 标配，无容量限制，现代系统默认。


#### MBR
+ Master Boot Record
+ 传统分区表，最大 2TB，最多 4 个主分区。

####  Raw Flash 分区（无分区表）
+ U-Boot、Linux 直接用地址划分分区
+ 没有 MBR/GPT，完全由设备树 /bootargs 定义
+ 树莓派、STM32、嵌入式 Linux 最常用

#### UBI / JFFS2 等闪存文件系统分区
+ 不是分区表，是闪存管理机制
+ 但功能上等价 “动态分区”

---

## U

### UEFI

+ Unified Extensible Firmware Interface（统一可扩展固件接口）
+ 是替代BIOS的新一代固件标准
