# 嵌入式学习路线图

参考路线图为Github项目[Embedded-Engineering-Roadmap](https://github.com/m3y54m/Embedded-Engineering-Roadmap.git)
![学习路线图](./assets/images/Embedded-Engineering-Roadmap.png)

核心逻辑：**基础系统→硬件交互→协议解析→内核驱动→项目实战**，每阶段配「书籍+视频+文档+工具」，兼顾理论与实操。

---

## 一、基础阶段（1-2周：系统+硬件入门）

目标：吃透树莓派Linux操作、GPIO/UART基础用法，建立「系统-硬件」关联

### 必看书籍（中文优先，新手友好）

- 《树莓派用户指南》（官方中文版）：系统安装、SSH、GPIO入门，配套实验清晰

- 《鸟哥的Linux私房菜 基础篇》：Linux命令、权限、进程管理，嵌入式开发必备系统基础

- 《Python编程：从入门到实践》：Python基础，适配树莓派GPIO/Pyserial快速开发

### 视频课程（B站免费，跟着敲就行）

- 【韦东山】嵌入式Linux应用开发完全手册（入门篇）：系统配置+基础命令+GPIO实操

- 【正点原子】树莓派快速入门：从烧录系统到LED闪烁，新手零门槛

- 【电子发烧友】树莓派UART串口通信教程：启用串口、接线、数据收发、Putty调试

### 核心文档（权威无坑，必存）

- 树莓派官方文档：[https://www.raspberrypi.com/documentation/](https://www.raspberrypi.com/documentation/)（GPIO/UART/I2C配置、系统备份）

- Raspberry Pi UART 完整指南：[https://en.hwlibre.com/Accessing-UART-and-I2C-from-Raspberry-Pi-OS:-A-Complete-Guide/](https://en.hwlibre.com/Accessing-UART-and-I2C-from-Raspberry-Pi-OS:-A-Complete-Guide/)（含Python/C示例、常见错误排查）

- Raspberry Pi GPIO Pinout：[https://pinout.xyz/](https://pinout.xyz/)（引脚功能速查，接线必备）

### 工具清单（上手即用）

- 系统烧录：Raspberry Pi Imager（官方）

- 串口调试：SSCOM（Windows）、COMTool（跨平台）、minicom（树莓派终端）

- GPIO开发库：Python（RPi.GPIO、pyserial）、C（wiringPi、bcm2835）

---

## 二、进阶阶段（2-4周：外设交互+协议解析）

目标：掌握I2C/SPI/ADC、自定义串口协议解析，衔接你的「UART报文解析」需求

### 必看书籍（理论+实战结合）

- 《Raspberry Pi Cookbook》（中文版《树莓派实战秘籍》）：外设交互（I2C/SPI/传感器）+ 串口协议解析案例

- 《Linux设备驱动开发详解》（宋宝华）：Linux驱动基础，为后续内核学习铺垫

- 《嵌入式系统接口技术》：UART/I2C/SPI协议原理，报文帧头/帧尾/校验设计

### 视频课程（聚焦协议与解析，实战强）

- 【韦东山】Linux高级IO与串口协议解析：自定义帧协议（AA+长度+数据+55+CRC）、解析代码实现

- 【正点原子】手把手教你学Linux之串口通信：串口配置、数据收发、CRC校验、协议解析

- 【电子发烧友】树莓派I2C传感器（DHT11/DS18B20）数据采集：I2C配置、驱动编写、数据解析

### 核心文档（协议解析必备，直接套用）

- 树莓派UART配置官方指南：[https://www.raspberrypi.com/documentation/computers/configuration.html#configuring-uarts](https://www.raspberrypi.com/documentation/computers/configuration.html#configuring-uarts)（启用PL011串口、禁用蓝牙冲突）

- COMTool 自定义协议模板配置文档：[https://comtool.readthedocs.io/](https://comtool.readthedocs.io/)（可视化配置帧头/帧尾/CRC，一键解析报文）

- CRC校验工具文档：[https://crccalc.com/](https://crccalc.com/)（在线计算CRC16/32，验证报文完整性）

### 实战工具（协议解析高效神器）

- 串口调试+解析：COMTool（跨平台，支持自定义协议模板）、SSCOM（Windows，CRC校验+帧解析）

- 报文分析：Wireshark（配合USB转TTL抓串口包）、Serial Port Monitor（Windows）

- 数据可视化：Python（matplotlib）、Node-RED（拖拽式显示传感器数据）

---

## 三、高级阶段（4周+：内核驱动+项目实战）

目标：从应用层深入内核层，掌握Linux驱动开发、交叉编译、物联网项目实战

### 必看书籍（进阶核心，对标岗位需求）

- 《Mastering Embedded Linux Programming》（中文版《精通嵌入式Linux编程》）：内核配置、根文件系统构建、交叉编译

- 《Linux内核设计与实现》（Robert Love）：内核架构、进程调度、内存管理，驱动开发核心理论

- 《Advanced Raspberry Pi》：树莓派内核编译、自定义驱动、硬件底层操作（适合深入硬件）

### 视频课程（深度实战，提升项目经验）

- 【韦东山】Linux高级驱动开发视频教程：字符设备驱动、GPIO中断、设备树（DT）配置

- 【正点原子】第四期 手把手教你学Linux之驱动开发篇：树莓派驱动开发实战（UART驱动、传感器驱动）

- 【电子发烧友】树莓派MQTT物联网终端开发：传感器数据采集→串口上报→MQTT云端同步→远程控制

### 核心文档（内核/驱动开发必备）

- Linux内核官方文档：[https://www.kernel.org/doc/html/latest/](https://www.kernel.org/doc/html/latest/)（驱动开发、设备树、内核编译）

- Raspberry Pi 内核编译指南：[https://www.raspberrypi.com/documentation/computers/linux_kernel.html](https://www.raspberrypi.com/documentation/computers/linux_kernel.html)（编译内核、加载自定义模块）

- Linux 设备树（Device Tree）入门：[https://elinux.org/Device_Tree_Usage](https://elinux.org/Device_Tree_Usage)（树莓派外设驱动必备）

### 实战项目（综合应用，可写进简历/博客）

1. 智能环境监测站：GPIO+DHT11（温湿度）+UART（上报）+MQTT（云端）+LCD（本地显示）

2. 自定义串口驱动：基于树莓派PL011 UART，编写字符设备驱动，实现自定义数据收发逻辑

3. 树莓派内核裁剪与定制：根据项目需求裁剪内核模块，减小系统体积，提升运行效率

---

## 四、关键学习技巧（帮你少走弯路）

1. **先模仿再创新**：初期直接复用成熟代码（如传感器驱动、串口协议模板），跑通后再修改参数、添加功能

2. **硬件防护优先**：每次接线前断电、释放静电，用杜邦线时避免引脚短路（树莓派3.3V引脚短路易烧板）

3. **问题闭环解决**：遇到报错（如串口 Permission denied），先记录现象→查原因→试解决方案→总结到知识库（Markdown文档），形成「问题-解决」清单

4. **善用社区资源**：Stack Overflow（搜索关键词：Raspberry Pi UART parse、GPIO interrupt）、Reddit r/raspberry_pi、树莓派中文社区

