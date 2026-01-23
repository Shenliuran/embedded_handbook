# 调试协议

## C

### CMSIS-DAP
+ Cortex Microcontroller Software Interface Standard - Debug Access Port
+ ARM 公司制定的开源调试接口协议标准，专门用于 ARM Cortex 系列 MCU 的在线调试与编程

---
## J

### JTAG
+ Joint Test Action Group(联合测试工作组)
+ 用于芯片内部测试
---

## R

### RTT
+ Real-Time Transfer(实时传输技术)
+ Segger 公司推出的嵌入式调试协议
+ 依托 SWD/JTAG 调试接口和 MCU 片内 RAM 缓冲区，实现主机与 MCU 的高速双向数据传输
+ 特点是速率高、无实时性干扰、不占用额外硬件资源，是替代传统串口打印的高效调试方案
+ 需配套支持 RTT 的调试器（如 [J-Link](../4.software_development_toolchain/hardware_tool.md###J-Link)）和 RTT 库使用

---
## S

### SWD
+ Serial Wire Debug(串行线调试)

