# 软件工具

## O

### OpenOCD
+ 开源片上调试器(On-Chip Debugger)
    + 通过JTAG/SWD实现

---

## T

### tty
+ TeleTYpewriter
+ 系统接口 / 设备文件
+ Linux/Unix 系统中对终端设备的抽象表示，用于访问串口、虚拟终端等输入输出设备。在嵌入式开发中常用于通过 UART 与 MCU 通信、查看调试信息或与 Bootloader 交互

```mermaid
flowchart TD
    id1(上位机软件 Host Software \n 如：minicom、screen、putty、串口助手)
    id2(操作系统提供的“终端设备抽象” \n Linux: /dev/ttyUSB0、/dev/ttyACM0、tty1 \n Windows: COM1、COM2)
    id3(硬件层：UART 控制器 + 物理串口 \n 如：USB 转串口模块、MCU 的 UART 外设)
    id4(目标设备 Target Device \n MCU、开发板、传感器模块等)
        
    id1 --使用--> id2 --对应--> id3 --连接--> id4
```
