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
+ [参考方法](https://www.chenxublog.com/2024/05/10/raspberry-pi-5-uart-ssh-no-data.html)
