# linux 引脚管理

## C

### consumer
+ Linux GPIO 子系统中标记的「占用 GPIO 引脚的设备/驱动/功能模块」，用于避免 GPIO 冲突、快速识别引脚用途

#### camX_reg
+ 控制摄像头模块的 GPIO 引脚
+ 通过控制该 GPIO 引脚的电平（高 / 低）来管理摄像头模块的硬件状态
    + 摄像头电源管理
    + 硬件复位
    + 使能 / 禁用摄像头功能

#### lg
+ 单板机（如树莓派）的 GPIO 控制工具集（lg archive）[参考链接](https://lg.raspberrybasic.org/index.html)
    + 包含 lgpio 库、rgpiod 守护进程等
    + 用于 GPIO 读写、PWM、I2C/SPI 封装等功能

#### phy-reset
+ `phy`: Physical Layer（物理层）芯片
+ 网口（RJ45 接口）的「底层硬件核心」，负责将主板上的数字信号（如 MCU/CPU 发出的以太网数据）转换成物理层电信号（通过网线传输），反之亦然
+ phy-reset 是 PHY 芯片的复位功能标识，对应嵌入式系统中专门用于「复位网口 PHY 芯片」的 GPIO 引脚（即 consumer: phy-reset 表示该 GPIO 被用于控制 PHY 芯片的复位）

---

## L

### libgpiod

+ `gpiodetect`: 检测系统中的 GPIO 芯片（gpiochipX）
+ `gpioinfo`: 查看 GPIO 芯片 / 引脚的详细信息
+ `gpioget`: 读取指定 GPIO 引脚的电平值
    + 例如: `gpioget -c 0 16`，获取gpiochip0 16引脚的电平值
+ `gpioset`: 配置指定GPIO引脚的电平值
    + 例如: `gpioset -c 0 16=0`，设置gpiochip0 16引脚的为低电平
+ `gpiomon`: 实时监听 GPIO 引脚的电平变化
+ `gpionotify`: 监控 GPIO 事件并发送用户态通知
+ `gpiotest`: 自动化测试 GPIO 引脚的功能完整性

#### 针对树莓派系统中的 gpiochipX
+ gpiochip0
    + RP1 IO 芯片（Pi5 核心）/ SoC GPIO 控制器（前代）
    + 管理树莓派 40 针扩展头的绝大多数引脚（BCM 0-57）
+ gpiochip11~13
    + BCM2712 SoC 内部扩展 GPIO 控制器
    + 管理树莓派板载内部外设引脚（如摄像头 / 显示屏接口、板载 LED、电源管理引脚）

---

## P

### pinctrl
+ Pin Control Subsystem
+ Linux 内核的引脚管理核心子系统，负责配置硬件引脚的「复用功能」和「电气特性」，避免引脚冲突
+ 核心功能：
    1. 引脚复用：将引脚配置为指定功能（如 GPIO14 设为 UART0_TX/普通 GPIO/SPI_MOSI）；
    2. 电气配置：设置上拉/下拉、驱动能力、电平速率等；
    3. 冲突规避：与 GPIO consumer 联动，防止引脚被重复配置。
+ 配置方式：主要在设备树（DTS）中定义引脚组，绑定到具体设备（如 UART、SPI）；
+ 关联内容：
    - [gpiochip](#gpiochip)（pinctrl 管理的引脚归属于某个 gpiochip）
    - [consumer](#consumer)（pinctrl 确保引脚功能与 consumer 匹配）
树莓派中通过 pinctrl 将 GPIO14/15 配置为 UART0 模式，而非普通 GPIO。
