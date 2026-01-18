# 如何使用Exlink对树莓派进行串口调试

## 问题拆解

### 树莓派串口UART使用方法

1. 调试探针Debug-Probe
    1. USB 至 UART 桥接器
        1. 树莓派Pico的 UART 通信将由调试探针转发到计算机，并显示为 *CDC UART*
        2. 连接到树莓派5的Debug Probe 默认情况下，它在 /dev/ttyAMA0（别名为/dev/serial0）提供115,200波特率8数据位，1停止位，无校验位的连接
        3. 树莓派5在raspi-config启用串行控制台将在 `/dev/ttyAMA0` 设备对应的 *新UART口* 上启用串行控制台。而旧型号则在GPIO14和15上启用串行控制台



### Exlink串口使用方法

1. [ 项目GITHUB链接 ]( https://github.com/physicsexpert/Exlink_Tool )
    1.D:\Downloads\BaiduNetdiskDownload\Exlink
        1. `uart_helper_task`
2. [ 多功能调试器设计 ]( https://github.com/physicsexpert/felini-firmware )

