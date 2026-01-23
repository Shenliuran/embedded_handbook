# 通讯协议

## U

### UART
+ Universal Asynchronous Receiver/Transmitte( 通用异步收发器 )
+ 也就是 *串口*

#### UART-PL011
+ PL011是一款*UART控制器*，是英国ARM公司推出的，用于与外设进行串行通讯。

#### TTL UART
+ 采用 TTL 电平的 UART 通信接口

### USB
+ Universal Serial Bus(通用串行总线)

#### HID (USB HID)
+ USB Human Interface Deivce(USB人机接口设备)
+ 用于规范人机交互设备与主机的通信方式，用于规范人机交互设备与主机的通信方式
+ HID设备:
    + 标准设备：键盘、鼠标、触摸板、游戏手柄、轨迹球
    + 嵌入式常用设备：条码扫描枪、指纹识别器、自定义调试器（如 HID 协议的烧录工具）、工业触控屏
#### OTG
+ USB On-The-Go(USB 协议的扩展标准)
+ 打破普通 USB 主从设备的固定角色限制，让 USB 设备可以动态切换主机（Host） 和外设（Slave） 模式，实现两台设备直接连接通信，无需经过 PC 等中间主机
