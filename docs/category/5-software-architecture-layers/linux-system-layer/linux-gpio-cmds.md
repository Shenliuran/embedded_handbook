# linux GPIO

## libgpiod

+ `gpiodetect`: 检测系统中的 GPIO 芯片（gpiochipX）
+ `gpioinfo`: 查看 GPIO 芯片 / 引脚的详细信息
+ `gpioget`: 读取指定 GPIO 引脚的电平值
+ `gpiomon`: 实时监听 GPIO 引脚的电平变化
+ `gpionotify`: 监控 GPIO 事件并发送用户态通知
+ `gpiotest`: 自动化测试 GPIO 引脚的功能完整性

## 针对树莓派系统中的 gpiochipX
+ gpiochip0
    + RP1 IO 芯片（Pi5 核心）/ SoC GPIO 控制器（前代）
    + 管理树莓派 40 针扩展头的绝大多数引脚（BCM 0-57）
+ gpiochip11~13
    + BCM2712 SoC 内部扩展 GPIO 控制器
    + 管理树莓派板载内部外设引脚（如摄像头 / 显示屏接口、板载 LED、电源管理引脚）
