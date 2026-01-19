# 如何使用Exlink对树莓派进行串口调试

## 问题拆解

### 树莓派串口UART使用方法

1. 调试探针Debug-Probe
    1. USB 至 UART 桥接器
        1. 树莓派Pico的 UART 通信将由调试探针转发到计算机，并显示为 *CDC UART*
        2. 连接到树莓派5的Debug Probe 默认情况下，它在 /dev/ttyAMA0（别名为/dev/serial0）提供115,200波特率8数据位，1停止位，无校验位的连接
        3. 树莓派5在raspi-config启用串行控制台将在 `/dev/ttyAMA0` 设备对应的 *新UART口* 上启用串行控制台。而旧型号则在GPIO14和15上启用串行控制台
2. 使用GPIO 14/15(Pin 8/10)
    1. 使用`pinctrl`配置树莓派5的GPIO功能: `pinctrl set 10 op       Set GPIO 10 to be an output`
        1. 如果没有`pinctrl`命令，则需要先安装该工具。[`pinctrl`](https://blog.csdn.net/weixin_65147589/article/details/141595836)
    2. [参考方法1](https://forums.raspberrypi.com/viewtopic.php?t=359132)
3. 在树莓派5 上，主 UART(primary UART) 位于调试头(Debug header，也就是Debug Probe所连接的[3pin JST-SH](./category/1.core_hardware_components/hardware_connection.md###JST连接器)接口)
4. [ 修改文件 ](https://www.chenxublog.com/2024/05/10/raspberry-pi-5-uart-ssh-no-data.html)
    1. `/boot/firmware/cmdline.txt`
    2. `/boot/firmware/config.txt`


### Exlink串口使用方法

1. [ 项目GITHUB链接 ]( https://github.com/physicsexpert/Exlink_Tool )
    1.D:\Downloads\BaiduNetdiskDownload\Exlink
        1. `uart_helper_task`
2. [ 多功能调试器设计 ]( https://github.com/physicsexpert/felini-firmware )

