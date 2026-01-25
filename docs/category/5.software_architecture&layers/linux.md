# Linux系统层

## F

### File Types
+ 普通文件（ - ）：存储数据、文本或可执行程序的基本文件类型。
+ 目录文件（ d ）：用于组织文件和子目录的特殊文件。
+ 链接文件（ l ）：指向其他文件或目录的快捷方式，分为硬链接和软链接。
+ 字符设备文件（ c ）：提供对系统中字符设备（如串行端口、键盘）的访问。
+ 块设备文件（ b ）：用于访问系统中的块设备（如硬盘、光驱）。
+ 套接字文件（ s ）：用于本地或跨主机进程间通信（IPC）的特殊文件。
+ 管道文件（ p ）：用于进程间通信的先进先出（FIFO）机制。

### Filesystem
+ [参考文档](https://www.cnblogs.com/it-coder/p/19082023)
+ 使用`man 5 fs`查看Linux 文件系统类型

```plaintext
/                  Root Directory
├── /boot          Boot Loader Files
├── /etc           Configuration Files
├── /home          User Home Directories
├── /root          Root Home Directories
├── /opt           Third-Party Applications
├── /dev           Device Files
├── /var           Variable Files
├── /bin           User Binaries
├── /sbin          System Binaries
├── /usr           User Applications
├── /proc          Process Information
├── /mnt           Mount Dirctory
├── /sys           Virtual File System
├── /media         Removable Devices
├── /run           Temporaray File System
├── /tmp           Temporaray Files
├── /lost+found    Recover Broken Files
├── /lib           System Libraries
└── /srv           Service Data Directory
```

#### FHS
+ Filesystem Hierarchy Standard
+ Linux目录结构的行业标准

#### mmcblk0p1
+ Linux 系统中对 MMC/SD 卡或 eMMC 存储设备的第一个分区的块设备文件名称
    1. `mmc`: 设备类型前缀，代表 MMC/SD 卡、eMMC 存储这类多媒体存储设备
    2. `blk`: 缩写自 block，代表这是一个块设备（按固定大小的数据块读写，区别于字符设备）
    3. `0`: 设备编号，代表系统中识别到的第 1 个 MMC 类设备
    4. `p1`: 分区编号，代表该设备上的第 1 个分区
+ FAT32 格式的 boot 分区，存放启动文件（bootloader、dtb 设备树文件、内核镜像 zImage）

#### mmcblk0p2
+ EXT4 格式的根分区，存放 Linux 系统、应用程序、用户数据等，是系统运行的核心分区

#### tmpfs
+ temporary filesystem(临时文件系统)
+ 基于内存（RAM）的文件系统，由 Linux 内核提供，用于存储临时数据

#### udev
+ userspace device manager（用户空间设备管理器）
+ Linux 系统中**用于动态管理设备**的核心机制
+ Linux 的 “即插即用” 系统

#### sysfs
+ Linux 内核提供的一种**虚拟文件系统**，用于以文件的形式暴露内核数据结构，特别是设备和驱动信息

#### proc
+ process filesystem
+ 用于访问进程和内核信息的虚拟文件系统

---

## G

### GPIO Device

#### libgpiod

+ `gpiodetect`: 检测系统中的 GPIO 芯片（gpiochipX）
+ `gpioinfo`: 查看 GPIO 芯片 / 引脚的详细信息
+ `gpioget`: 读取指定 GPIO 引脚的电平值
+ `gpiomon`: 实时监听 GPIO 引脚的电平变化
+ `gpionotify`: 监控 GPIO 事件并发送用户态通知
+ `gpiotest`: 自动化测试 GPIO 引脚的功能完整性
