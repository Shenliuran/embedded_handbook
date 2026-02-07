# 树莓派相关配置

## 安装clash

```bash
git clone --branch master --depth 1 https://gh-proxy.org/https://github.com/nelvko/clash-for-linux-install.git \
  && cd clash-for-linux-install \
  && bash install.sh
```

+ [clash-for-linux-install](https://github.com/nelvko/clash-for-linux-install)
    1. 先clone到Windows上，再使用`scp -r .\clash-for-linux-install\ liuranshen@192.168.1.3:/home/liuranshen/clash-for-linux-install`将仓库上传到树莓派中
    2. 在树莓派中执行安装脚本

## 安装Neovim

1. 下载[neovim最新镜像(version>=0.11)](https://github.com/neovim/neovim/releases): `wget https://github.com/neovim/neovim/releases/download/v0.11.5/nvim-linux-arm64.appimage`
2. 解压镜像: `chmod u+x ./nvim-linux-arm64.appimage && ./nvim-linux-arm64.appimage --extract-appimage`
3. 将解压后的文件移动到系统根目录: `mv ./squashfs-root /`
4. 在`/opt`文件夹下创建nvim软连接: `ln -s /squashfs-root/usr/bin/nvim /opt/nvim`
5. 在.bashrc中，将`/opt`加入到路径中: `export PATH=$PATH:/opt`

## 使用串口登录树莓派
+ 调试探针Debug-Probe
    1. USB 至 UART 桥接器
        1. 树莓派Pico的 UART 通信将由调试探针转发到计算机，并显示为 *CDC UART*
        2. 连接到树莓派5的Debug Probe 默认情况下，它在 /dev/ttyAMA0（别名为/dev/serial0）提供115,200波特率8数据位，1停止位，无校验位的连接
        3. 树莓派5在raspi-config启用串行控制台将在 `/dev/ttyAMA0` 设备对应的 *新UART口* 上启用串行控制台。而旧型号则在GPIO14和15上启用串行控制台
+ 使用GPIO 14/15(Pin 8/10)
    1. 使用`pinctrl`配置树莓派5的GPIO功能: `pinctrl set 10 op  # Set GPIO 10 to be an output`
        1. 如果没有`pinctrl`命令，则需要先安装该工具。[`pinctrl`](https://blog.csdn.net/weixin_65147589/article/details/141595836)
    2. [参考方法1](https://forums.raspberrypi.com/viewtopic.php?t=359132)
+ 在树莓派5 上，主 UART(primary UART) 位于调试头(Debug header，也就是Debug Probe所连接的[3pin JST-SH](./category/1.core_hardware_components/hardware_connection.md###JST连接器)接口)
+ 修改文件: [参考方法2](https://www.chenxublog.com/2024/05/10/raspberry-pi-5-uart-ssh-no-data.html)
```bash
# 1. 把`cmdline.txt`开头的console参数改成这样:

console=ttyAMA0,115200 console=tty1 

# 2. 在`config.txt`末尾加上这几行:

enable_uart=1
dtparam=uart0
dtparam=uart0_console
```
